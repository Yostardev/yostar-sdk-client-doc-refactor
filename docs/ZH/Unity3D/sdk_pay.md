### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的支付&验单流程，我们为游戏开发人员绘制了下列支付时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_pay.jpg" alt="" width="800" height="738" align="left" />


.
### 2、打开商店协议界面
\* 调用该接口可打开商店协议界面;


- #### 函数定义
    ```cs
    public void showAgreement(Agreement agreementType)
    ```

    入参名称|入参说明|备注
    ---|:--:|:--|
    agreementType|需展示的协议类型,枚举值|AGREEMENT_REFUND, //韩服 退款协议<br/>AGREEMENT_REFUND_EXPLAIN,// 韩服 退款说明<br/>AGREEMENT_FUND_SETTLEMENT,// 日服 资金结算法<br/>AGREEMENT_SPECIFIC_COMMERCIAL,// 日服 特定商业法|

- #### 调用示例
    ```cs
    YoStarSDK.Instance.showAgreement(Agreement.AGREEMENT_REFUND_EXPLAIN);
    ```



### 3、发起支付
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现游戏道具的购买;<br/>\* 调用该接口前,务必先设置PayEvent监听回调，以便支付操作后,顺利收到操作结果的事件;

- #### 函数定义
    ```cs
    public ResultCode Pay(string productId, string payNotifyUrl, string extraData)
    ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--:|:--|
    productId|string|支付的产品Id|无|
    payNotifyUrl|string|支付回调URL|<br/>可联系悠星为每个枚举环境设置对应的游戏服务器发货地址,该笔订单完成后,悠星SDK服务器会通知对应的游戏服务器地址发放道具;|
    extraData|string|透传递参数|建议入参游戏的支付订单号,该参数会在支付回调里携带返回;|

- #### 调用示例

    ```cs
    private void OnPayRespone(PayRet ret){

       if (ret.R_CODE == ResultCode.OK){

            // pay success
        }else if(ret.R_CODE == ResultCode.PAY_HOLDON){

            //订单处理中，建议对游戏服务器轮询支付结果；
        }else{

           // pay fail
        }
    }

    YoStarSDKEvent.Instance.PayEvent += OnPayRespone;//Important!!!
    YoStarSDK.Instance.Pay("gold_100", "https://test.paynotifyurl.com", "game_order_001");
    ```

    PayRet 属性名|参数说明|备注
    ---|:--:|:--|
    R_CODE|状态码,枚举值|0:成功<br/> 其他值可查看错误表含义|
    R_MSG| 错误信息,辅助排查问题|无 |
    ORDER_ID| 悠星订单号|无 |
    EXTRA_DATA| 透传字段|透传支付接口的入参extraData字段 |


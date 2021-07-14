### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的支付&验单流程，我们为游戏开发人员绘制了下列支付时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_pay.jpg" alt="" width="800" height="738" align="left" />


.
### 2、打开商店协议界面
\* 调用该接口可打开商店协议界面;


- #### 函数定义
    ``` java
    public static void showAgreement(Activity activity,int agreementType)
    ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    agreementType|int|需展示的协议类型,枚举值| 0 // 日服 资金结算 <br/> 1 // 日服 特定商业 <br/> 2 // 韩服 退款说明 <br/> 3 // 韩服 退款协议 |

- #### 调用示例
    ``` java
    AiriSDK.showAgreement(MainActivity.this, GooglePayComponent.AGREEMENT_FUND_SETTLEMENT);
    ```



### 3、发起支付
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现游戏道具的购买;<br/>\* 调用该接口前,务必先设置AiriSDK.setCallBack监听回调，以便支付操作后,顺利收到操作结果的事件;

- #### 函数定义
    ``` java
    public static void pay(Activity activity, String productId, String serverTag, String extraData)
    ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    productId|string|需要支付的产品Id|无|
    serverTag|string|支付环境地址;枚举值|在不同支付环境上支付的订单，可用来区分不同阶段的订单，比如测试、提审、正式环境|
    extraData|string|透传递参数|建议入参游戏的支付订单号,该参数会在支付回调里携带返回|

- #### 调用示例

    ``` java
    AiriSDK.pay(MainActivity.this, "productId", "serverTag", "extraData");
    ```
- #### 回调示例
    ``` java
    {"EXTRA_DATA":"cp_order1619087389775","ORDER_ID":"1250504353048453120","METHOD":"OnPayNotify","R_MSG":" success ","R_CODE":0}
    ```

    ``` java
    {"EXTRA_DATA":"cp_order1619087178071","ORDER_ID":"1250503465462337536","METHOD":"OnPayNotify","R_MSG":"the relevant request is in progress and takes a long time to notify the client to poll","R_CODE":200180}
    ```
    PayRet 属性名|类型|参数说明|备注
    ---|:--:|:--|:--|
    ORDER_ID| string|悠星订单号|无 |
    EXTRA_DATA| string|透传字段|透传支付接口的入参extraData字段 |

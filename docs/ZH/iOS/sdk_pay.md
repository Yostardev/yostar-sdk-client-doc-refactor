### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的支付&验单流程，我们为游戏开发人员绘制了下列支付时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/YoStarSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_pay.jpg" alt="" width="800" height="738" align="left" />


.
### 2、打开商店协议界面
\* 调用该接口可打开商店协议界面;


- #### 函数定义
```objectivec
    /**
    获取其他协议视图
    @param type
            0 日服 资金结算法
            1 日服 特定商业交易法
            2 韩服 退款说明
            3 韩服 退款协议
    */
    + (void)showAgreement:(int)type;
```

    入参名称|入参说明|备注
    ---|:--:|:--|
    type|需展示的协议类型,int|3, //韩服 退款协议<br/>2,// 韩服 退款说明<br/>0,// 日服 资金结算法<br/>1,// 日服 特定商业法|

- #### 调用示例
```objectivec
[YoStarSDK showAgreement:1];
```



### 3、发起支付
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现游戏道具的购买;<br/>\* 调用该接口前,务必先设置**setCallback**监听`BuyMethod`回调，以便支付操作后,顺利收到操作结果的事件;

- #### 函数定义
```objectivec
    /**
    @param productId   商品的ID
    @param payNotifyUrl   cp侧的支付通知url
    @param extraData   额外的信息，防重
    */
    + (void)pay:(NSString *)productId
      payNotifyUrl:(NSString *)payNotifyUrl
      extraData:(NSString *)extraData;
```

    入参名称|入参说明|备注
    ---|:--:|:--|
    productId|需要支付的产品Id|无|
    payNotifyUrl|支付回调URL;字符串|无|
    extraData|透传递参数|建议入参游戏的支付订单号,该参数会在支付回调里携带返回|

- #### 调用示例
```objectivec
[YoStarSDK pay:@"xxxid" payNotifyUrl:@"https://test.paynotifyurl.com" extraData:@"xxxxx"];
```
    回调的数据转换成`字典`类型
    属性名|参数说明|备注
    ---|:--:|:--|
    R_CODE|状态码,枚举值|0:成功<br/> 其他值可查看错误表含义|
    R_MSG| 错误信息,辅助排查问题|无 |
    ORDER_ID| 悠星订单号|无 |
    EXTRA_DATA| 透传字段|透传支付接口的入参extraData字段 |
    METHOD | 事件 | 比如：`OnPayNotify`代表支付 |


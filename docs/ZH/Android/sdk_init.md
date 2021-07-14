### 1、SDK初始化

\* 调用该接口完成SDK的初始化工作;<br/>
\* 在初始化成功的情况下，才能调用SDK其他接口;<br/>
\* 调用该接口前，请先设置AiriSDK.setCallBack监听回调，以便初始化成功后,顺利收到初始化成功的事件;


- #### 函数定义

  ``` java
  public static void init(Activity activity, String sdkUrl, String payStoreId)
  ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    sdkUrl|string|SDK服务器地址|无|
    payStoreId|string|支付渠道|google支付:googleplay|

<br/>

- #### 调用示例

  ``` java
  AiriSDK.init(MainActivity.this, "https://xxxxx.arknights.com", "googleplay");
  ```
- #### 回调示例
  ``` java
    {"R_VIRTUAL":1,"LOGIN_PLATFORM":-1,"SHOW_LOG":true,"METHOD":"OnInitNotify","LOGIN_UID":"","R_MSG":"success","R_CODE":0,"LOGIN_NAME":""}
  ```
    resultMap 属性名|类型|参数说明|备注
    ---|:--:|:--|:--|
    SHOW_LOG|boolean| log信息|初始化接口控制<br/>true//显示<br>false//不显示 |
    R_VIRTUAL|int| 设备类型|1//虚拟机<br/>0//真机 |
    LOGIN_UID|string|缓存的账号UID|无|
    LOGIN_NAME|string|缓存的账号昵称|无 |
    LoginPlatform|int|缓存账号类型|DEVICE = 0,//游客<br/>MIGRATIONCODE = 1,//引继码<br/>TWITTER = 2,    //twitter<br/>FACEBOOK = 3, //facebook<br/>YOSTAR = 4,//悠星<br/>GOOGLE = 5,//Google|

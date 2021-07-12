### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的账户登录&验证流程，我们为游戏开发人员绘制了下列登录时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_login.jpg" alt="" width="860" height="800" align="left" />

.
### 2、账号登录
<span id = "login"/>

\* 调用该接口可完成账号的快速登录;<br/>\* 如果是第一次调用该接口，会进行游客登录(日服)或者打开账号中心界面UI让用户选择登录方式(美韩服);<br/>\* 如果SDK已有登录缓存记录，则会用缓存进行快速登录;<br/>\* 参考下面的调用示例，请先设置AiriSDK.setCallBack监听回调，以便登录成功后,顺利收到登录成功的事件;


- #### 函数定义

  ``` java
  public static void login(Activity activity)
  ```

- #### 调用示例

    ``` java
    AiriSDK.login(MainActivity.this);
    ```
- #### 回调示例

    ``` java
    {"AMAZON_NAME":"","LOGIN_PLATFORM":0,"YOSTAR_NAME":"","TWITTER_NAME":"","GOOGLE_EMAIL":"","MIGRATION_CODE":"","METHOD":"OnLoginNotify","FACEBOOK_NAME":"","LOGIN_UID":"40119188699623424","R_MSG":" success ","R_CODE":0,"LOGIN_NAME":""}
    ```

    | resultMap    | 参数说明 | 备注 |
    | -------------- | ------ | ------ |
    | strProductId   | string | 商品ID，和运营方协商后获取，该ID是配置在AiriSDK后台（必要） |
    | eServerTag     | BuyServerTag(枚举) | 服务器枚举（提审服、预发布服、正式服）（必要）支付对应的服务器tag。根据这个tag不同，最后服务端的支付通知URL也会不同 |
    | strExtraData   | string | 透传字段，该字段会在客户端的回调，以及服务端的支付回调中原样返回，请保证每次传入的参数不一致。服务端的支付回调通知请参见服务端接入文档。（必要） |


### 3、打开账号中心界面
\* 调用该接口打开账号中心界面UI，用户可以在UI上选择登录方式(FB、TW、Google、Yostar、引继码); <br/>\* 调用该接口前，务必参考[【账号登录】](#login)章节先设置AiriSDK.setCallBack监听回调，以便登录成功后，顺利收到登录成功的事件;


- #### 函数定义

    ``` java
    public static void showAccountCenter(Activity activity)
    ```

- #### 调用示例

    ``` java
    AiriSDK.showAccountCenter(MainActivity.this);
    ```



### 4、打开引继码生成界面
\* 只有日服有此功能;<br/>
\* 该接口需账户登录成功后才能调用;<br/>
\* 调用该接口，打开引继码生成界面; 用户可以查看、生成新的引继码;<br/>
\* 一个账号同时只能有一个引继码,多次生成,之前的引继码会被失效;<br/>
\* 一个引继码只能用来登录一次;

- #### 函数定义
    ``` java
    public static void showTranscode(Activity activity)
    ```

- #### 调用示例
    ``` java
    AiriSDK.showTranscode(MainActivity.this);
    ```


### 5、绑定三方账号
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现本地账号与三方账号建立绑定连接关系;<br/>\* 调用该接口前,务必先设置AiriSDK.setCallBack监听回调，以便绑定操作后,顺利收到操作结果的事件;

- #### 函数定义
    ``` java
    public static void linkSocial(Activity activity, int platform)
    ```

    入参名称|入参说明|备注
    ---|:--:|:--|
    platform|需绑定的平台类型|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|


- #### 调用示例
    ``` java
        AiriSDK.linkSocial(MainActivity.this, 3);
    ```
  
- #### 回调示例

  ``` java
      {"LOGIN_PLATFORM":3,"SOCAIL_NAME":"xxx","METHOD":"OnLinkNotify","R_MSG":" success ","R_CODE":0}
  ```

    | resultMap属性    | 参数说明 | 备注 |
    | ---- | ---- | ------ |
    | R_CODE | 状态码,枚举值 | 0:成功<br/>其他值可查看错误表含义 |
    | R_MSG | 错误信息,辅助排查问题 | 无  |
    | LOGIN_PLATFORM | 绑定的三方平台 |2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|
    | SOCAIL_NAME | 三方账号的昵称 | 无 |




### 6、解绑三方账号
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现本地账号与三方账号解除绑定连接关系;<br/>\* 调用该接口前,务必先设置AiriSDK.setCallBack监听回调，以便解绑操作后,顺利收到操作结果的事件;


- #### 函数定义
    ``` java
    public static void unlinkSocial(Activity activity, int platform)
    ```

    入参名称 | 入参说明 | 备注
    --|:---:|:---|
    platform|需绑定的平台类型,枚举值|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|


- #### 调用示例
    ``` java
    AiriSDK.unlinkSocial(MainActivity.this, SdkConst.LOGINPLATFORM_FACEBOOK);
    ```
- #### 回调示例

  ``` java
      {"LOGIN_PLATFORM":3,"SOCAIL_NAME":"xxx","METHOD":"OnUnLinkNotify","R_MSG":" success ","R_CODE":0}
  ```
  
    resultMap 属性名|参数说明|备注
    ---|:--:|:--|
    R_CODE|状态码,枚举值|0:成功<br/>其他值可查看错误表含义|
    R_MSG| 错误信息,辅助排查问题|无 |
    LOGIN_PLATFORM|解绑绑定的三方平台|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|
    SOCAIL_NAME|三方账号的昵称|无 |




### 7、删除账号
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现从SDK服务器上删除SDK UID账号;<br/>\* 调用该接口前,务必先设置AiriSDK.setCallBack监听回调，以便删除操作后,顺利收到操作结果的事件;


- #### 函数定义
    ``` java
    public static void deleteAccount(Activity activity)
    ```

- #### 调用示例
    ``` java
    AiriSDK.deleteAccount(MainActivity.this);
    ```







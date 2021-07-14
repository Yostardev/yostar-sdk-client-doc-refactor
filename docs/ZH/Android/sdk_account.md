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

    | LoginRet    | 类型 | 参数说明 | 备注 |
    | -------------- | ------ | ------ |------ |
    | LOGIN_UID   | string | SDK登陆成功之后返回UID |无
    | LOGIN_NAME   | string | SDK登陆成功之后返回用户名 |无
    | LOGIN_PLATFORM   | int | 登录平台类型 | fb、tw、google、yostar、apple、游客
    | FACEBOOK_NAME   | string | 绑定的FB账号用户名 |无
    | TWITTER_NAME   | string | 绑定的TW账号用户名 |无
    | YOSTAR_NAME    | string | 绑定的YoStar账号用户名 |无
    | GOOGLE_EMAIL   | string | 绑定的Google账号用户名 |无
    | AMAZON_NAME   | string | 绑定的AMAZON账号用户名 |无
    | MIGRATION_CODE   | string | 该账号生成的可用引继码 |无（必要） |无|


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

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    platform|int|需绑定的平台类型|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|


- #### 调用示例
    ``` java
        AiriSDK.linkSocial(MainActivity.this, 3);
    ```
  
- #### 回调示例

  ``` java
      {"LOGIN_PLATFORM":3,"SOCAIL_NAME":"xxx","METHOD":"OnLinkNotify","R_MSG":" success ","R_CODE":0}
  ```

    | resultMap属性    |类型| 参数说明 | 备注 |
    | ---- | ---- | ------ | ------ |
    | LOGIN_PLATFORM | int | 绑定的三方平台 |2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|
    | SOCAIL_NAME | string | 三方账号的昵称 | 无 |




### 6、解绑三方账号
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现本地账号与三方账号解除绑定连接关系;<br/>\* 调用该接口前,务必先设置AiriSDK.setCallBack监听回调，以便解绑操作后,顺利收到操作结果的事件;


- #### 函数定义
    ``` java
    public static void unlinkSocial(Activity activity, int platform)
    ```

    入参名称 | 类型 |入参说明 | 备注
    --|:---:|:---|:---|
    platform|int|需绑定的平台类型,枚举值|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|


- #### 调用示例
    ``` java
    AiriSDK.unlinkSocial(MainActivity.this, SdkConst.LOGINPLATFORM_FACEBOOK);
    ```
- #### 回调示例

  ``` java
      {"LOGIN_PLATFORM":3,"SOCAIL_NAME":"xxx","METHOD":"OnUnLinkNotify","R_MSG":" success ","R_CODE":0}
  ```
  
    resultMap 属性名|类型|参数说明|备注
    ---|:--:|:--|:--|
    R_CODE|int|状态码,枚举值|0:成功<br/>其他值可查看错误表含义|
    R_MSG|string| 错误信息,辅助排查问题|无 |
    LOGIN_PLATFORM|int|解绑绑定的三方平台|2//TWITTER,<br/>3//FACEBOOK,<br/>4//YOSTAR,<br/>5//GOOGLE|
    SOCAIL_NAME|string|三方账号的昵称|无 |




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







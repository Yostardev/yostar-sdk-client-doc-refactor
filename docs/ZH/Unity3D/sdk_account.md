### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的账户登录&验证流程，我们为游戏开发人员绘制了下列登录时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_login.jpg" alt="" width="860" height="800" align="left" />

.
### 2、账号登录
<span id = "login"/>

\* 调用该接口可完成账号的快速登录;<br/>\* 如果是第一次调用该接口，会进行游客登录(日服)或者打开账号中心界面UI让用户选择登录方式(美韩服);<br/>\* 如果SDK已有登录缓存记录，则会用缓存进行快速登录;<br/>\* 参考下面的调用示例，请先设置LoginEvent监听回调，以便登录成功后,顺利收到登录成功的事件;


- #### 函数定义

  ```cs
    public void Login()
  ```

- #### 调用示例
```cs
    private void OnLoginResponse(LoginRet ret){ //callBack

      if (ret.R_CODE == ResultCode.OK){
          // 登录成功，继续游戏逻辑
      }else {
         // 登录失败，用户可重新触发登录按钮
      }
    }

    YoStarSDKEvent.Instance.LoginEvent += OnLoginResponse; // Important!!!
    YoStarSDK.Instance.Login();
```

    | LoginRet    | 类型 | 参数说明 | 备注 |
    | -------------- | ------ | ------ |------ |
    | R_CODE   | ResultCode(枚举) |错误码 |无
    | R_MSG     | string | 错误信息,辅助排查问题 |无
    | LOGIN_UID   | string | SDK登陆成功之后返回UID |无
    | LOGIN_NAME   | string | SDK登陆成功之后返回用户名 |无
    | LOGIN_PLATFORM   | LoginPlatform(枚举) | 登录平台类型 | fb、tw、google、yostar、apple、游客
    | FACEBOOK_NAME   | string | 绑定的FB账号用户名 |无
    | TWITTER_NAME   | string | 绑定的TW账号用户名 |无
    | YOSTAR_NAME    | string | 绑定的YoStar账号用户名 |无
    | GOOGLE_EMAIL   | string | 绑定的Google账号用户名 |无
    | APPLE_ID       | string | 绑定的Apple账号ID |无
    | MIGRATION_CODE   | string | 该账号生成的可用引继码 |无
    


### 3、打开账号中心界面
\* 调用该接口打开账号中心界面UI，用户可以在UI上选择登录方式(FB、TW、Google、Yostar、Apple、引继码); <br/>\* 调用该接口前，务必参考[【账号登录】](#login)章节先设置LoginEvent监听回调，以便登录成功后，顺利收到登录成功的事件;


- #### 函数定义

    ```cs
    public void ShowAccountCenter()
    ```

- #### 调用示例

    ```cs
    YoStarSDK.Instance.ShowAccountCenter();
    ```



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

    | LoginRet    | 参数说明 | 备注 |
    | -------------- | ------ | ------ |
    | strProductId   | string | 商品ID，和运营方协商后获取，该ID是配置在AiriSDK后台（必要） |
    | eServerTag     | BuyServerTag(枚举) | 服务器枚举（提审服、预发布服、正式服）（必要）支付对应的服务器tag。根据这个tag不同，最后服务端的支付通知URL也会不同 |
    | strExtraData   | string | 透传字段，该字段会在客户端的回调，以及服务端的支付回调中原样返回，请保证每次传入的参数不一致。服务端的支付回调通知请参见服务端接入文档。（必要） |


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




### 4、打开用户中心界面
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口，打开用户中心界面; 用户可查看、生成新的引继码、三方账号绑定、删除账号、清理缓存等操作;<br/>
\* 调用接口前，请先按示例设置好删除账号回调、清理缓存回调、退出登录回调，以便在用户执行完对应操作时，可以切换游戏场景;<br/>
\* 一个账号同时只能有一个引继码,多次生成,之前的引继码会被失效;<br/>
\* 一个引继码只能用来登录一次;


- #### 函数定义
    ```cs
    public void showAccountCenter()
    ```

- #### 调用示例
    ```cs

    private void OnDeleteAccountResponse(DeleteAccountRet ret){
        // 账号删除成功, 建议回到游戏登录界面
    }
    YoStarSDKEvent.Instance.DeleteAccountEvent += OnDeleteAccountResponse;

    private void OnClearCacheResponse(ClearRet ret){
         // 缓存清理成功，建议回到游戏初始化界面，用户可触发初始化按钮进行重新初始化SDK；
    }
    YoStarSDKEvent.Instance.ClearSDKCacheEvent += OnClearCacheResponse;

    private void OnLogoutResponse(LogoutRet ret){
      // 账号退出成功，建议回到游戏登录界面
    }
    YoStarSDKEvent.Instance.LogoutEvent += OnLogoutResponse;

    YoStarSDK.Instance.showAccountCenter();

    ```







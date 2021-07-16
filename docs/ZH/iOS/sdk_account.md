### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的账户登录&验证流程，我们为游戏开发人员绘制了下列登录时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_login.jpg" alt="" width="860" height="800" align="left" />

.
### 2、账号登录
<span id = "login"/>

\* 调用该接口可完成账号的快速登录;<br/>\* 如果是第一次调用该接口，会进行游客登录(日服)或者打开账号中心界面UI让用户选择登录方式(美韩服);<br/>\* 如果SDK已有登录缓存记录，则会用缓存进行快速登录;<br/>\* 参考下面的调用示例，请先设置LoginEvent监听回调，以便登录成功后,顺利收到登录成功的事件;


- #### 函数定义
```objectivec
    /**
    快速登陆
     */
    + (void)login;
```

- #### 调用示例
```objectivec
[YoStarSDK login];
```

### 3、打开账号中心界面
\* 调用该接口打开账号中心界面UI，用户可以在UI上选择登录方式(FB、TW、Yostar、Apple、引继码); <br/>\* 调用该接口前，务必参考**初始化章节**设置监听回调，以便登录成功后，顺利收到登录成功的事件;


- #### 函数定义
```objectivec
    /**
    账号管理:
    */
    + (void)showAccountCenter;
```

- #### 调用示例
```objectivec
[YoStarSDK showAccountCenter];
```








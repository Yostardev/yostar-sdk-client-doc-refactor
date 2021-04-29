### 1、功能概述
\* 为了让开发人员能更好的理解我们的SDK的账户登录&验证流程，我们为游戏开发人员绘制了下列登录时序图:
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/YoStarSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/sdk_login.jpg" alt="" width="860" height="800" align="left" />

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

### 4、打开引继码生成界面
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口，打开引继码生成界面; 用户可以查看、生成新的引继码;<br/>
\* 一个账号同时只能有一个引继码,多次生成,之前的引继码会被失效;<br/>
\* 一个引继码只能用来登录一次;

- #### 函数定义
```objectivec
    /**
    生成引继码视图
    */
    + (void)showTranscode;
```

- #### 调用示例
```objectivec
[YoStarSDK showTranscode];
```

### 5、删除账号
\* 该接口需账户登录成功后才能调用;<br/>\* 调用该接口可实现从SDK服务器上删除SDK UID账号;<br/>\* 调用该接口前,务必先设置**setCallback**监听`DeleteUIDMethod`回调，以便删除操作后,顺利收到操作结果的事件;


- #### 函数定义
```objectivec
    /**
    删除账号 韩服
    */
    + (void)deleteAccount;
```

- #### 调用示例
```objectivec
[YoStarSDK deleteAccount];
```







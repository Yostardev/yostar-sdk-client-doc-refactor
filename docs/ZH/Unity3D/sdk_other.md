### 1、打开公告界面
\* 调用该接口打开公告界面,如果游戏内有自己的公告界面，可不接入;

- #### 函数定义
    ```cs
    public void ShowAnnouncement()
    ```
- #### 调用示例

    ```cs
    YoStarSDK.Instance.ShowAnnouncement();
    ```

### 2、打开设置界面(用户未登录)
<span id = "settings"/>

\* 调用该接口打开设置界面,可查看用户协议、隐私声明、清理缓存、联系客服；<br/>
\* 调用该接口前需先设置好ClearSDKCacheEvent回调，以便接收SDK缓存被清理的事件，后续需重新初始化SDK；

- #### 函数定义
    ```cs
    public void ShowSettings()
    ```
- #### 调用示例

    ```cs
    private void OnClearCacheRespone(ClearRet ret)
    {
      if(ret.code == ResultCode.OK){

      // SDK缓存被清理, 建议回到游戏开始界面，需重新初始化SDK;
      }
    }

    YoStarSDKEvent.Instance.ClearSDKCacheEvent += OnClearCacheRespone;
    YoStarSDK.Instance.ShowSettings();
    ```

### 3、打开设置界面(用户已登录)
\* 调用该接口打开设置界面,可查看用户协议、隐私声明、清理缓存、联系客服；<br/>
\* 调用该接口前需先设置好ClearSDKCacheEvent回调，可参考[【打开设置界面(用户未登录)】](#settings)章节;

- #### 函数定义
    ```cs
    public void ShowSettings(string serverId, string roleUid, string roleName, string roleCreateTime, int purchase, string[] tags)
    ```

    入参名称| 类型|入参说明|备注
    ---|---| ---|---|
    serverId|string| 服务器ID|无 |
    roleUid|string| 角色UID|无 |
    roleName|string| 角色昵称|无 |
    roleCreateTime|string| 角色创建时间|无 |
    purchase|int| 角色氪金总额|无 |
    tags|string[]| 角色标签数组| 标签数据可联系悠星运营获取 |

- #### 调用示例

    ```cs
    YoStarSDKEvent.Instance.ClearSDKCacheEvent += OnClearCacheRespone;
    YoStarSDK.Instance.ShowSettings("servierId","uid", "name", "1998-08-25", 100, new string[0]);
    ```

### 4、获取设备号
\* 调用该接口可同步获取SDK内使用的设备号;

- #### 函数定义
    ```cs
    public string GetDeviceID()
    ```

- #### 调用示例

    ```cs
    string deviceId = YoStarSDK.Instance.GetDeviceID();
    ```

### 5、获取SDK版本号
\* 调用该接口可同步获取当前SDK版本号;

- #### 函数定义
    ```cs
    public string GetSdkVer()
    ```

- #### 调用示例

    ```cs
    string sdkVer = YoStarSDK.Instance.GetSdkVer();
    ```

### 6、分享截图
\* 调用该接口，可以将自定义的Texture2D交由操作系统进行分享到三方应用;

- #### 函数定义
    ```cs
    public void SystemShare(string strShareText, Texture2D texShare = null)
    ```

    入参名称|类型|入参说明|备注
    ---|---|---|---|
    strShareText|string| 分享的文字标题|无 |
    texShare|Texture2D| 分享的贴图数据 |无|


- #### 调用示例
    ```cs
    YoStarSDK.Instance.SystemShare("sample", screenShot);
    ```

### 7、打开商店评分界面
\* 调用该接口，可打开应用商店的评分页面;

- #### 函数定义
    ```cs
    public void RequestStoreReview()
    ```

- #### 调用示例
    ```cs
    YoStarSDK.Instance.RequestStoreReview();
    ```

### 8、检测设备是否支持苹果登录
\* 调用该接口，可同步检查本机是否支持苹果登录;

- #### 函数定义
    ```cs
    public bool AppleSignInAvailable()
    ```

- #### 调用示例
    ```cs
    bool isAvailable = YoStarSDK.Instance.AppleSignInAvailable();
    ```


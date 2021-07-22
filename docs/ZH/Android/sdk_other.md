### 1、打开公告界面
\* 调用该接口打开公告界面,如果游戏内有自己的公告界面，可不接入;

- #### 函数定义
    ``` java
    public static void showAnnouncement(Activity activity)
    ```
- #### 调用示例

    ``` java
    YoStarSDK.showAnnouncement(MainActivity.this);
    ```

### 2、打开设置界面(用户未登录)
<span id = "settings"/>

\* 调用该接口打开设置界面,可查看用户协议、隐私声明、清理缓存、联系客服；<br/>
\* 调用该接口前需先设置好YoStarSDK.setCallBack回调，以便接收SDK缓存被清理的事件，后续需重新初始化SDK；

- #### 函数定义
    ``` java
    public static void showSettings(Activity activity)
    ```
- #### 调用示例

    ``` java
    YoStarSDK.showSettings(MainActivity.this);
    ```

### 3、打开设置界面(用户已登录)
\* 调用该接口打开设置界面,可查看用户协议、隐私声明、清理缓存、联系客服；<br/>
\* 调用该接口前需先设置好YoStarSDK.setCallBack回调，可参考[【打开设置界面(用户未登录)】](#settings)章节;

- #### 函数定义
    ``` java
    public static void showSettings(Activity activity, String sdkVersion, String serverId, String roleUid, String roleName, String roleCreateTime, int purchase, String tags)
    ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    serverId| string |服务器ID|无 |
    sdkVersion| string|YoStarSDK版本|无 |
    roleUid| string|角色UID|无 |
    roleName| string|角色昵称|无 |
    roleCreateTime| string|角色创建时间|无 |
    purchase| int|角色氪金总额|无 |
    tags| string|角色标签数组|标签信息可以联系悠星运营获取|

- #### 调用示例

    ``` java
    YoStarSDK.showSettings(MainActivity.this, "3.0.0", "serverId", "001", "roleName", "", 0, "[tag1, tag2]");
    ```

### 4、清理SDK缓存
\* 日服不会清除缓存
\* 调用该界面可清理SDK内运行缓存数据;<br/>
\* 该接口同步执行,建议游戏调用该接口后, 切换游戏场景到开始界面，需重新初始化SDK;

- #### 函数定义
    ``` java
    public static void clearSDKCache()
    ```

- #### 调用示例

    ``` java
    YoStarSDK.clearSDKCache();

    // SDK缓存被清理, 建议回到游戏开始界面，需重新初始化SDK;
    ```

### 5、获取设备号
\* 调用该接口可同步获取SDK内使用的设备号;

- #### 函数定义
    ``` java
    public static String getDeviceId()
    ```

- #### 调用示例

    ``` java
    YoStarSDK.getDeviceId();
    ```

### 6、分享截图
\* 调用该接口，可以将自定义的Texture2D交由操作系统进行分享到三方应用;

- #### 函数定义
    ``` java
    public static void systemShare(Activity activity, String strShareText, String imgPath)
    ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    strShareText|string| 分享的文字标题|无 |
    imgPath|string| 分享的贴图数据地址 |无|


- #### 调用示例
    ``` java
    YoStarSDK.systemShare(MainActivity.this, "strShareText", "imgPath");
    ```

### 7、打开商店评分界面
\* 调用该接口，可打开应用商店的评分页面;

- #### 函数定义
    ``` java
    public static void requestStoreReview(Activity activity)
    ```

- #### 调用示例
    ``` java
    YoStarSDK.requestStoreReview(MainActivity.this);
    ```


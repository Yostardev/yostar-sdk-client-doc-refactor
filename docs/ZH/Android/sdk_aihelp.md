

### 1、用户未登录状态发起客诉
\* 调用该接口可打开Aihelp的客诉界面;

- #### 函数定义
    ``` java
    public static void showAiHelpFAQs(Activity activity)
    ```


- #### 调用示例

    ``` java
    AiriSDK.showAiHelpFAQs(MainActivity.this);
    ```


### 2、用户已登录状态发起客诉
\* 调用该接口可打开Aihelp的客诉界面;<br/>
\* 该接口需账户登录成功后才能调用;

- #### 函数定义
    ``` java
    public static void showAiHelpFAQs(Activity activity, String sdkVersion, String serverId, String roleUid, String roleName, String roleCreateTime, int purchase, String tags)
    ```

    入参名称|入参说明|备注
    ---|:--:|:--|
    serverId| 服务器ID|无 |
    sdkVersion| airiSDK版本|无 |
    roleUid| 角色UID|无 |
    roleName| 角色昵称|无 |
    roleCreateTime| 角色创建时间|无 |
    purchase| 角色氪金总额|无 |
    tags| 角色标签数组|标签信息可以联系悠星运营获取|


- #### 调用示例

    ``` java
    AiriSDK.showAiHelpFAQs(MainActivity.this, "3.0.0", "serverId", "001", "roleName", "", 0, "[tag1, tag2]");
    ```





### 1、用户未登录状态发起客诉
\* 调用该接口可打开Aihelp的客诉界面;

- #### 函数定义
    ```cs
    public void ShowAiHelpFAQs()
    ```


- #### 调用示例

    ```cs
    YoStarSDK.Instance.ShowAiHelpFAQs();
    ```


### 2、用户已登录状态发起客诉
\* 调用该接口可打开Aihelp的客诉界面;<br/>
\* 该接口需账户登录成功后才能调用;

- #### 函数定义
    ```cs
    public void ShowAiHelpFAQs(string serverId, string roleUid, string roleName, string roleCreateTime, int purchase, string[] tags)
    ```

    入参名称|类型|入参说明|备注
    ---| --- | ---| ---|
    serverId|string|服务器ID|无 |
    roleUid|string| 角色UID|无 |
    roleName|string| 角色昵称|无 |
    roleCreateTime|string| 角色创建时间|无 |
    purchase|int|角色氪金总额|无 |
    tags|string[] | 角色标签数组|标签信息可以联系悠星运营获取|


- #### 调用示例

    ```cs
    YoStarSDK.Instance.ShowAiHelpFAQs(servierId,uid,name, "1998-08-25", 100, new string[]{"tag1","tag2"});
    ```



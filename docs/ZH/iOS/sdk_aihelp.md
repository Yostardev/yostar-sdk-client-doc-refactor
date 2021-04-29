\* 调用客诉之前需要注册AIHelp
```objectivec
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    [YoStarSDK aiHelpInitForApiKey:@"ApiKey" domainName:@"Apidomain" appID:@"appID"];
    return YES;
}
```

### 发起客诉
\* 调用该接口可打开Aihelp的客诉界面;
\* 未登录状态接口参数可传空

- #### 函数定义
```objectivec
    + (void)showAiHelpFAQs:(NSString *)sdkVersion
              withServerId:(NSString *)serverId
               withRoleUid:(NSString *)roleUid
              withRoleName:(NSString *)roleName
        withRoleCreateTime:(NSString *)roleCreateTime
              withPurchase:(int)purchase
                  withTags:(NSString *)tags;
```

    入参名称|入参说明|备注
    ---|:--:|:--|
    sdkVersion| SDK版本号 | 可空|
    serverId| 服务器ID|无 |
    roleUid| 角色UID|无 |
    roleName| 角色昵称|无 |
    roleCreateTime| 角色创建时间|无 |
    purchase| 角色氪金总额|无 |
    tags| 角色标签|标签信息可以联系悠星运营获取|


- #### 调用示例
```objectivec
    NSData *tagData = [NSJSONSerialization dataWithJSONObject:@[@"bug",@"bad_user"] options:NSJSONWritingFragmentsAllowed error:nil];
    NSString *tagStr = [[NSString alloc] initWithData:tagData encoding:NSUTF8StringEncoding];
    [YoStarSDK showAiHelpFAQs:@""
               withServerId:@"serverid"
                withRoleUid:@"roleid"
               withRoleName:@"rolename"
         withRoleCreateTime:@"2020-11-11"
               withPurchase:1000
                   withTags:tagStr];
```



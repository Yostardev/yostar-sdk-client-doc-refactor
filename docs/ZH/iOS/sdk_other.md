### 1、打开公告界面
\* 调用该接口打开公告界面,如果游戏内有自己的公告界面，可不接入;

- #### 函数定义
```objectivec
    /**
     公告视图
     */
    + (void)showAnnouncement;
```
- #### 调用示例
```objectivec
[YoStarSDK showAnnouncement];
```

### 2、打开设置界面
\* 调用该接口打开设置界面,可查看用户协议、隐私声明、清理缓存、联系客服；<br/>
\* 调用该接口前需先设置好**setCallback**监听`ClearSDKCacheMethod` 回调;
\* 未登录状态接口参数可传空
- #### 函数定义
```objectivec
    /**
     设置视图
     */
    + (void)showSettings:(NSString *)sdkVersion
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
    [YoStarSDK showSettings:@""
             withServerId:@""
              withRoleUid:@""
             withRoleName:@""
       withRoleCreateTime:@""
             withPurchase:0
                 withTags:tagStr];
```

### 3、清理SDK缓存
\* 调用该界面可清理SDK内运行缓存数据;<br/>
\* 该接口同步执行,建议游戏调用该接口后, 切换游戏场景到开始界面，需重新初始化SDK;

- #### 函数定义
```objectivec
    /**
     清除SDk缓存
     */
    + (void)cleanSDKCache;
```

- #### 调用示例
```objectivec
[YoStarSDK cleanSDKCache];
// SDK缓存被清理, 建议回到游戏开始界面，需重新初始化SDK;
```

### 4、获取设备号
\* 调用该接口可同步获取SDK内使用的设备号;

- #### 函数定义
```objectivec
    /**
     获取设备的ID
     */
    + (NSString *)getDeviceId;
```

- #### 调用示例
```objectivec
[YoStarSDK getDeviceId];
```

### 5、分享截图
\* 调用该接口，交由操作系统进行分享到三方应用;

- #### 函数定义
```objectivec
    /**
     分享
     */
    + (void)systemShare:(NSString *)strShareText
          withImageData:(Byte *)imgDataByte
             withLength:(int)nSize;
```

    入参名称|入参说明|备注
    ---|:--:|:--|
    strShareText| 分享的文字标题|无 |
    imgDataByte | 二进制数据 | 无 |
    nSize | 二进制数据的长度 |无|


- #### 调用示例
```objectivec
    UIImage *image = info[UIImagePickerControllerOriginalImage];
    NSData *imageData = UIImagePNGRepresentation(image);
    [picker dismissViewControllerAnimated:true completion:^{
        [YoStarSDK systemShare:@"图片分享"
               withImageData:(Byte *)[imageData bytes]
                  withLength:[@(imageData.length) intValue]];
    }];
```

### 6、打开商店评分界面
\* 调用该接口，可打开应用商店的评分页面;

- #### 函数定义
```objectivec
    /**
     App Store评分
     */
    + (void)requestStoreReview;
```

- #### 调用示例
```objectivec
[YoStarSDK requestStoreReview];
```

### 7、检测设备是否支持苹果登录
\* 调用该接口，可同步检查本机是否支持苹果登录;

- #### 函数定义
```objectivec
     /**
      判断系统版本是否大于iOS 13
      */
    + (BOOL)checkAppleSignInAvailable;
```
- #### 调用示例
```objectivec
BOOL isSupport = [YoStarSDK checkAppleSignInAvailable];
```


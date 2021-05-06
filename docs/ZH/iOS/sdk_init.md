### 1、SDK初始化
\* 调用该接口完成SDK的初始化工作;<br/>\* 在初始化成功的情况下，才能调用SDK其他接口;<br/>
\* 调用该接口前，请先设置InitEvent监听回调，以便初始化成功后,顺利收到初始化成功的事件;

- #### 导入头文件
```objectivec
#import <YoSDKCoreKit/YoSDKCoreKit.h>
```
- #### 设置对回调的监听
    - 调用
    ```objectivec
    [YoStarSDK setCallback:^(NSString * _Nonnull result) {
            NSData *data = [result dataUsingEncoding:NSUTF8StringEncoding];
            NSDictionary *dic = [NSJSONSerialization JSONObjectWithData:data options:NSJSONReadingAllowFragments error:nil];
            NSLog(@"%@", [dic descriptionInStringsFileFormat]);
            if ([dic[METHODKEY] isEqualToString:InitMethod]) {
                //初始化回调
                if (dic[RCODEKEY] == YoErrorCodeSuccess) {
                    //初始化成功
                } else {
                    //初始化失败
                }
            }
    }];
    ```
    - 定义
    ```objectivec
        + (void)setCallback:(SDKCallBackBlock)block;
    ```
    - 释义
    > 处理初始化、登录、购买、绑定、支付等操作的回调
    
    - 回调的数据转换成`字典`类型
        属性名|参数说明|备注
        ---|:--:|:--|
        R_CODE|状态码,枚举值|0:成功<br/> 其他值可查看第7章错误码表含义|
        R_MSG| 错误信息,辅助排查问题|无 |
        LOGIN_UID|缓存的账号UID|无|
        LOGIN_NAME|缓存的账号昵称|无 |
        LOGIN_PLATFORM|缓存账号类型,枚举值|YoLoginPlatformDevice = 0,//游客<br/>YoLoginPlatformTranscode = 1,//引继码<br/>YoLoginPlatformTwitter = 2,//twitter<br/>YoLoginPlatformFacebook = 3, //facebook<br/>YoLoginPlatformYostar = 4,//悠星<br/>YoLoginPlatformApple = 6, //apple|

    


- #### 函数定义

```objectivec
/**
 @param initURL 初始化的URL
 */
+ (void)init:(NSString *)initURL;
```
   入参名称|入参说明|备注
   ---|:--:|:--|
   initURL| 初始化的URL | https://xxxx.com |

<br/>

- #### 调用示例
  ```objectivec
  [YoStarSDK init:@"https://xxxx.com"];
  ```

    
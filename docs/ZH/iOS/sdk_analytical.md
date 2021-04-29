
### 1、数据埋点
\* 调用该接口可实现自定义埋点数据上报;

- #### 函数定义
```objectivec
    /**
    埋点
     @param strEventName    埋点
     @param strJsonCallbackParameter 参数
     */

    + (void)userEventUpload:(NSString *)strEventName
    strJsonCallbackParameter:(NSString *)strJsonCallbackParameter;
```
    入参名称|入参说明|备注
    ---|:--:|:--|
    strEventName| 事件名|可联系悠星运营获取需埋点的事件名 |
    strCallbackParameter|事件上报参数|可联系悠星运营获取埋点数值 |

- #### 调用示例
```objectivec
    NSDictionary *paramsDic = @{
        @"name" : @"ALIAS",
        @"age" : @"20"
    };
    NSData *data = [NSJSONSerialization dataWithJSONObject:paramsDic options:NSJSONWritingFragmentsAllowed error:nil];
    NSString *pStr = [[NSString alloc] initWithData:data encoding:NSUTF8StringEncoding];
   
    [YoStarSDK userEventUpload:@"eventName" strJsonCallbackParameter:pStr];
```

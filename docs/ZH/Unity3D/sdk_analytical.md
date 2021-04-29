
### 1、数据埋点
\* 调用该接口可实现自定义埋点数据上报;

- #### 函数定义
    ```cs
    public void UserEventUpload(string strEventName, Dictionary<string, string> strCallbackParameter = null)
    ```
    入参名称|入参说明|备注
    ---|:--:|:--|
    strEventName| 事件名|可联系悠星运营获取需埋点的事件名 |
    strCallbackParameter|事件上报参数|可联系悠星运营获取埋点数值 |

- #### 调用示例

    ```cs
    Dictionary<string, string> dic = new Dictionary<string, string>();
    dic.Add("uid", "1234543");
    YoStarSDK.Instance.UserEventUpload("user_login_event", dic);
    ```

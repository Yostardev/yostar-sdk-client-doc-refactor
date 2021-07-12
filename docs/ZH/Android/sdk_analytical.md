
### 1、数据埋点
\* 调用该接口可实现自定义埋点数据上报;

- #### 函数定义
    ``` java
    public static void userEventUpload(String strEventName, String strJson)
    ```
    入参名称|入参说明|备注
    ---|:--:|:--|
    strEventName| 事件名|可联系悠星运营获取需埋点的事件名 |
    strJson|事件上报参数|可联系悠星运营获取埋点数值 |

- #### 调用示例

    ``` java
    AiriSDK.userEventUpload("test_event_name", "{"test1":"t_test_1","test2":"t_test_2","test3":"t_test_3"}");
    ```

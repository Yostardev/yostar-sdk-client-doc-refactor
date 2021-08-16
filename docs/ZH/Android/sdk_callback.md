本SDK的主入口类为YoStarSDK，以下方法皆从该类中调用。

- #### 函数定义

  ``` java
    public static void setCallBack(SdkCallBack callBack)
  ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--|:--|
    callBack|SdkCallBack|回调接口|无|

<br/>

- #### 调用示例

  ``` java
      YoStarSDK.setCallBack(new AiriSDK.SdkCallBack() {
          @Override public void onCallBack(HashMap<String, Object> resultMap) {
              // 所有异步接口调用后，调用结果都会在该函数返回；
          }
      });
  ```
  
每个回调都至少有三个基础字段信息：

    resultMap 属性名|类型|参数说明|备注
    ---|:--:|:--:|:--|
    R_CODE|int|状态码|0:成功<br/> 其他值可查看第7章错误码表含义|
    R_MSG|string| 错误信息,辅助排查问题|无 |
    METHOD|string| 对应接口|无 |

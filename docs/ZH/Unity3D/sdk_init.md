### 1、SDK初始化

\* 调用该接口完成SDK的初始化工作;<br/>\* 在初始化成功的情况下，才能调用SDK其他接口;<br/>
\* 调用该接口前，请先设置InitEvent监听回调，以便初始化成功后,顺利收到初始化成功的事件;


- #### 函数定义

  ```cs
    public bool Init(Envs environment, PayStore payStore)
  ```

    入参名称|类型|入参说明|备注
    ---|:--:|:--:|:--|
    environment|Envs|sdk出包服环境|test、release|
    payStore|PayStore|出包渠道|googleplay、appstore、onestore|


<br/>

- #### 调用示例

  ```cs
      private void OnInitResponse(InitRet ret){//callback

          if (ret.R_CODE == ResultCode.OK){
              //  初始化成功, 继续游戏逻辑
          }else{
              //初始化失败, 不做操作;  用户可重新触发初始化按钮
          }
      }

      YoStarSDKEvent.Instance.InitEvent += OnInitResponse;

      YoStarSDK.Instance.Init(Envs.test, PayStore.appstore);
  ```

    InitRet 属性名|类型|参数说明|备注
    ---|:--:|:--:|:--|
    R_CODE|枚举|状态码|0:成功<br/> 其他值可查看第7章错误码表含义|
    R_MSG|string| 错误信息,辅助排查问题|无 |
    LOGIN_UID|string|缓存的账号UID|无|
    LOGIN_NAME|string|缓存的账号昵称|无 |
    LoginPlatform|枚举|缓存账号类型|DEVICE = 0,//游客<br/>MIGRATIONCODE = 1,//引继码<br/>TWITTER = 2,    //twitter<br/>FACEBOOK = 3, //facebook<br/>YOSTAR = 4,//悠星<br/>GOOGLE = 5,//Google<br/>APPLE = 6, //apple|

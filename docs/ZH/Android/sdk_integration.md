### 1: AndroidManifeset配置

- #### 客服系统

  ``` xml
    <meta-data android:name="aihelp_apiKey" android:value="xxxxxxx" />
    <meta-data android:name="aihelp_demain" android:value="xxxxx" />
    <meta-data android:name="aihelp_appId" android:value="xxxxxxxxxxx" />
  ```

### 2: res资源配置

AiriSDK集成了firebase的部分功能，需要在res/values/google_service_strings.xml中配置firebase服务参数。
获取参数值请咨询悠星商务人员。

\* 其中default_web_client_id字段已从后台初始化接口下发

  ``` xml
    <!--
        <string name="default_web_client_id">***</string>
    -->
    <string name="fcm_fallback_notification_channel_label">****</string>
    <string name="firebase_database_url">*****</string>
    <string name="gcm_defaultSenderId">*****</string>
    <string name="google_api_key">******</string>
    <string name="google_app_id">******</string>
    <string name="google_crash_reporting_api_key">******</string>
    <string name="google_storage_bucket">*****</string>
    <string name="project_id">*****</string>
  ```
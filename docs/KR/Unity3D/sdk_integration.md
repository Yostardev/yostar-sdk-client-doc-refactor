### Step1: 导入AiriSDK
\* Unity编辑器打开游戏工程后, 依次双击AiriSDK和Resource的unitypackage 导入到游戏工程;<br/>
\* 如果你的游戏工程中已经有自定义的AndroidManifest.xml ,在导入AiriSDK时请注意，避免该文件被覆盖重写;

#### AiriSDK目录结构
<img src="https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/unity_dir.png" alt="" width="330" height="260" align="left"  />
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>


### Step2: 配置接入参数
\* 选择菜单栏 *AiriSDK > Config Settings* 菜单项,打开AiriSDK的参数配置面板;<br/>

![loading.png](https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/unity_asset.png)
<br/>

\* 在配置面板中填写各项功能的接入参数;(若不打算接入对应的功能，相关参数可为空);

![loading.png](https://sdkresources.oss-cn-shanghai.aliyuncs.com/AiriSDK%E6%8E%A5%E5%85%A5%E6%96%87%E6%A1%A3%E5%9B%BE%E5%BA%8A/unity_config.png?)



**Save Config** 按钮会将上述配置参数保存在以下目录:
- \Assets\AiriSDK\Resources\
- \Assets\Plugins\Android\res\values\google_service_strings.xml
- \Assets\Plugins\Android\AndroidManifest.xml

可根据你的需求,将上述目录加入git管理,避免每次出包频繁配置参数;
<br/><br/>
注: 以上参数必须正确填写，每次修改后，均需执行一次**Save Config** 按钮，否则游戏运行时将无法获得SDK配置参数；

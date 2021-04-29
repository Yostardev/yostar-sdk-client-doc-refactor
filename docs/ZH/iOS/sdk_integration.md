[AIHelp](https://docs.aihelp.net/zh/docs/integrating/iOS/)
[Firebase](https://firebase.google.com/docs/ios/setup)

### 1、导入* framework * 与* bundle *
>`YoSDKCoreKit.framework`
 `YoSDKFBKit.framework`
 `YoSDKTWKit.framework`
 `YoSDKSignInAppleKit.framework`
 `YoSDKAdjustKit.framework`
 `YoSDKIAPKit.framework`
 `YoSDKAiHelpKit.framework`
 `YoSDKResources.bundle`
### 2、在 `Xcode Build Settings` 里面设置 `Other Linker Flags` 的值为：
>`-ObjC`
 `-lc++`

### 3、添加依赖库
在项目设置`target` -> `General` -> `Linked Frameworks and Libraries`添加如下依赖库：
>`libsqlite3.tbd`
 ​`libresolv.tbd`
 `libicucore.tbd`
 `libz.tbd`
 `Accelerate.framework`
 `Foundation.framework`
 `MapKit.framework`
 `StoreKit.framework`
 `SafariServices.framework`
 `SystemConfiguration.framework`
 `UIKit.framework`
 `​WebKit.framework`
### 4、设置SDK所需权限, 在项目工程的 info.plist 中增加5个权限：
>`Privacy - Photo Library Usage Description` 需要访问您的相册权限，才能将图片上传反馈给客服
 `Privacy - Camera Usage Description` 需要访问您的相机权限，才能拍摄问题图片并反馈给客服
 `Privacy - Photo Library Additions Usage Description` 需要照片添加权限，才能保存图片到相册
 `Privacy - Microphone Usage Description` 需要访问您的麦克风权限，才能在表单页上传视频录像并反馈给客服
 `Privacy - Location When In Use Usage Description` 需地理位置权限，才能分享给你朋友位置

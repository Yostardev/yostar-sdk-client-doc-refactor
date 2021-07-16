[AIHelp](https://docs.aihelp.net/zh/docs/integrating/iOS/)
[Firebase](https://firebase.google.com/docs/ios/setup)

### 1、导入*framework* 与*bundle*
> 1. `YoSDKCoreKit.framework`
  2. `YoSDKFBKit.framework`
  3. `YoSDKTWKit.framework`
  4. `YoSDKSignInAppleKit.framework`
  5. `YoSDKAdjustKit.framework`
  6. `YoSDKIAPKit.framework`
  7. `YoSDKAiHelpKit.framework`
  8. `YoSDKResources.bundle`
### 2、在 `Xcode Build Settings` 里面设置 `Other Linker Flags` 的值为：
> 1. `-ObjC`
  2. `-lc++`

### 3、添加依赖库
在项目设置`target` -> `General` -> `Linked Frameworks and Libraries`添加如下依赖库：
> 1. `libsqlite3.tbd`
  2. ​`libresolv.tbd`
  3.`libicucore.tbd`
  4.`libz.tbd`
  5. `Accelerate.framework`
  6. `Foundation.framework`
  7.`MapKit.framework`
  8. `StoreKit.framework`
  9. `SafariServices.framework`
  10. `SystemConfiguration.framework`
  11.`UIKit.framework`
  12. `​WebKit.framework`
### 4、设置SDK所需权限, 在项目工程的 info.plist 中增加5个权限：
> 1. `Privacy - Photo Library Usage Description` 需要访问您的相册权限，才能将图片上传反馈给客服
 2. `Privacy - Camera Usage Description` 需要访问您的相机权限，才能拍摄问题图片并反馈给客服
 3. `Privacy - Photo Library Additions Usage Description` 需要照片添加权限，才能保存图片到相册
 4. `Privacy - Microphone Usage Description` 需要访问您的麦克风权限，才能在表单页上传视频录像并反馈给客服
 5. `Privacy - Location When In Use Usage Description` 需地理位置权限，才能分享给你朋友位置


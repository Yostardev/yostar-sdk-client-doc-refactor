联系悠星运营获取下列SDK接入包,以及接入配置参数:

### SDK接入所需文件
| 文件名称 | 说明 | 备注 |
| :------: | :-----: | :----: |
| **YoSDKCoreKit.framework** | `核心库` | 必选 |
| **YoSDKFBKit.framework** | 与 `Facebook` 相关库 | 可选 |
| **YoSDKTWKit.framework** | 与 `twitter` 相关的库 | 可选 |
| **YoSDKSignInAppleKit.framework** | `Apple` 登录库 | 如果使用了其他第三方账号登录，则必选，否则可选 |
| **YoSDKAdjustKit.framework** | `埋点`相关 | 可选 |
| **YoSDKIAPKit.framework** | `Apple` 支付相关 | 可选 |
| **YoSDKAiHelpKit.framework** | `客诉`相关 | 可选 |
| **YoSDKResources.bundle** | *SDK资源包,不同区服会有不同的资源包；<br/>内含SDK UI界面所依赖的图片资源<br/>以及无需暴露给CP的一些配置文件* | 必选 |
| **GoogleService-Info.plist** | `Google`配置文件 | 如果使用了<br/>`YoSDKAdjustKit.framework`<br/>库，则必选，否则为可选 |

### SDK接入配置参数
| 参数名称 | 参数说明 | 备注 |
| :------: | :-----: | :----: |
| Twitter Key | 用于配置Twitter登录功能 | 如果使用了<br/>`YoSDKTWKit.framework`<br/>库，则必选，否则为可选 |
| Facebook App Id | 用于配置Facebook登录功能 |如果使用了<br/>`YoSDKFBKit.framework`<br/>库，则必选，否则为可选 |
| Aihelp Key | 用于配置Aihelp客诉功能 | 如果使用了<br/>`YoSDKAiHelpKit.framework`<br/>库，则必选，否则为可选 |
| Aihelp Domain | 用于配置Aihelp客诉功能 | 如果使用了<br/>`YoSDKAiHelpKit.framework`<br/>库，则必选，否则为可选 |
| Aihekp iOS App Id | 用于配置Aihelp客诉功能 | 如果使用了<br/>`YoSDKAiHelpKit.framework`<br/>库，则必选，否则为可选 |


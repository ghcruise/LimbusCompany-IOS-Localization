# LimbusCompany-IOS-Localization
本文将介绍一种《边狱公司》（Limbus Company）iOS 的客户端汉化方案。   
适用于不想使用**Q公司**、**K公司**、**O公司**等加速器产品，且有其他代理工具的人群   

## 声明
- **前提：有其他代理工具（如Shadowrocket、Surge等）**
- 汉化资源来自[LocalizeLimbusCompany](https://github.com/LocalizeLimbusCompany/LocalizeLimbusCompany)，遵循 **CC BY-NC-SA 4.0 协议**   
- 包含战斗气泡，来自[Bilibili调爪](https://space.bilibili.com/485880984)
- 关键词彩色高亮
- 剧情故事中的人物名和称号已汉化
- 本项目实现的是对游戏内日语替换，因此选择日语才可以看到汉化效果。同样地，可以参考下文 [详细原理](#原理简介) 实现对韩语或英语的替换，同样可以达到本项目的效果
- 由于IOS端字库限制，本项目在尽可能保留原意的前提下对汉化资源中的部分文本进行了替换  
[字符映射表（施工中）]()


## 原理简介
核心原理是通过 **中间人（Man-in-the-Middle）代理** 拦截游戏 API 返回的数据，并在返回客户端之前进行资源替换，从而实现翻译。  

[详细原理（施工中）]()
## 使用方法 
本文以Shadowrocket为例，其它代理工具请参照各自工具的使用方法  

### MitM配置 - CA证书安装
1. 打开Shadowrocket，进入`配置`页面，点击当前使用的规则最右侧的`ⓘ`进入`conf页面`
2. 进入`HTTPS解密`页面，启用`HTTPS解密`
3. 在弹出的证书页面选择`生成新的CA证书`并确认
4. 点击`安装证书`并允许下载描述文件
5. 在设备的`设置`→`通用`→`VPN与设备管理`页面选择下载的描述文件并安装
6. 在设备的`设置`→`通用`→`关于本机`→`证书信任设置`启用对安装证书的完全信任
   
---
### 代理软件配置
本项目提供两个汉化版本可供使用  
- 稳定版：零协更新后才会更新，对于游戏维护后的新增内容显示为`UNKNOWN`  
- 最新版：需要定期更新模块。游戏维护后可立即更新，新内容无汉化。零协更新后也会更新。  
   
  
**如果你安装了[Script-Hub模块](https://github.com/Script-Hub-Org/Script-Hub/wiki/%E5%AE%89%E8%A3%85)，则可以点击下方链接一键导入**   
#### 稳定版
- [Shadowrocket模块](https://api.boxjs.app/shadowrocket/install?module=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization.module%2F_end_%2FLimbusCompanyIOSLocalization.sgmodule%3Ftype%3Dsurge-module%26target%3Dshadowrocket-module%26del%3Dtrue%26jqEnabled%3Dtrue)  
  
- [Stash覆写](https://api.boxjs.app/stash/install-override?url=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization.module%2F_end_%2FLimbusCompanyIOSLocalization.stoverride%3Ftype%3Dsurge-module%26target%3Dstash-stoverride%26del%3Dtrue%26jqEnabled%3Dtrue)  
  
- [Surge模块](https://api.boxjs.app/surge/install-module?url=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization.module%2F_end_%2FLimbusCompanyIOSLocalization.sgmodule%3Ftype%3Dsurge-module%26target%3Dsurge-module%26del%3Dtrue%26jqEnabled%3Dtrue&name=)  

- [Loon插件](https://www.nsloon.com/openloon/import?plugin=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization.module%2F_end_%2FLimbusCompanyIOSLocalization.plugin%3Ftype%3Dsurge-module%26target%3Dloon-plugin%26del%3Dtrue%26jqEnabled%3Dtrue)   
    
#### 最新版
- [Shadowrocket模块](https://api.boxjs.app/shadowrocket/install?module=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization-pre-release.module%2F_end_%2FLimbusCompanyIOSLocalization-pre-release.sgmodule%3Ftype%3Dsurge-module%26target%3Dshadowrocket-module%26del%3Dtrue%26jqEnabled%3Dtrue)  
  
- [Stash覆写](https://api.boxjs.app/stash/install-override?url=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization-pre-release.module%2F_end_%2FLimbusCompanyIOSLocalization-pre-release.stoverride%3Ftype%3Dsurge-module%26target%3Dstash-stoverride%26del%3Dtrue%26jqEnabled%3Dtrue)  
  
- [Surge模块](https://api.boxjs.app/surge/install-module?url=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization-pre-release.module%2F_end_%2FLimbusCompanyIOSLocalization-pre-release.sgmodule%3Ftype%3Dsurge-module%26target%3Dsurge-module%26del%3Dtrue%26jqEnabled%3Dtrue&name=)  

- [Loon插件](https://www.nsloon.com/openloon/import?plugin=http%3A%2F%2Fscript.hub%2Ffile%2F_start_%2Fhttps%3A%2F%2Fraw.githubusercontent.com%2Fghcruise%2FLimbusCompany-IOS-Localization%2Frefs%2Fheads%2Fmain%2FLimbusCompanyIOSLocalization-pre-release.module%2F_end_%2FLimbusCompanyIOSLocalization-pre-release.plugin%3Ftype%3Dsurge-module%26target%3Dloon-plugin%26del%3Dtrue%26jqEnabled%3Dtrue)   
  

**如果你没有安装Script-Hub模块，建议你安装一个。如果实在不想安装，请看下文**
- Shadowrocket模块  
复制下方链接，导入Shadowrocket模块中并启用
    - [稳定版](https://raw.githubusercontent.com/ghcruise/LimbusCompany-IOS-Localization/refs/heads/main/LimbusCompanyIOSLocalization.module)
    - [最新版](https://raw.githubusercontent.com/ghcruise/LimbusCompany-IOS-Localization/refs/heads/main/LimbusCompanyIOSLocalization-pre-release.module)
- Surge & Loon & Quantumult X  
~~由于作者没有这些代理工具，所以也不会有这部分的内容~~  
  

---
### 启动游戏
确认
- 启用VPN
- 启用上述配置

**进入游戏会提示下载约20Mb资源文件则说明汉化成功**

## 最后
- 如果你觉得本项目对你有帮助，请帮忙点个 Star，这是对我最好的支持！
- ~~还不是为了自己在手机上玩得舒服，顺手搞的~~
- 对文本或其他方面有建议的可以在 Issue 中提出

## 致谢
Original project:
https://github.com/LocalizeLimbusCompany/LocalizeLimbusCompany

Licensed under CC BY-NC-SA 4.0.

# LimbusCompany-IOS-Localization
本文将介绍一种《边狱公司》（Limbus Company）iOS 的客户端汉化方案。   
适用于不想使用**Q公司**、**K公司**、**O公司**等加速器产品，且有其他代理工具的人群   

## 声明
- **前提：有其他代理工具（如Shadowrocket、Surge等）**
- 汉化资源来自[LocalizeLimbusCompany](https://github.com/LocalizeLimbusCompany/LocalizeLimbusCompany)，遵循 **CC BY-NC-SA 4.0 协议**   
- 包含战斗气泡
- 本项目实现的是对游戏内日语替换，因此选择日语才可以看到汉化效果。同样地，可以参考下文 [详细原理](#原理简介) 实现对韩语或英语的替换，同样可以达到本项目的效果
- 由于IOS端字库限制，本项目在尽可能保留原意的前提下对汉化资源中的部分文本进行了替换  
[字符映射表（施工中）]()


## 原理简介
核心原理是通过 **中间人（Man-in-the-Middle）代理** 拦截游戏 API 返回的数据，并在返回客户端之前进行资源替换，从而实现翻译。  

[详细原理（施工中）]()
## 使用方法 
本文以Shadowrocket为例，其它代理工具请参照各自工具的使用方法  

### CA证书安装
1. 打开Shadowrocket，进入`配置`页面，点击当前使用的规则最右侧的`ⓘ`进入`conf页面`
2. 进入`HTTPS解密`页面，启用`HTTPS解密`
3. 在弹出的证书页面选择`生成新的CA证书`并确认
4. 点击`安装证书`并允许下载描述文件
5. 在设备的`设置`→`通用`→`VPN与设备管理`页面选择下载的描述文件并安装
6. 在设备的`设置`→`通用`→`关于本机`→`证书信任设置`启用对安装证书的完全信任

### 代理软件配置
**强烈建议自行下载release中的manifest.json和localize_jp.zip并起一个http服务器，并将以下脚本中的Link修改为下载链接**  
1. 打开Shadowrocket，进入`配置`页面，点击当前使用的规则最右侧的`ⓘ`进入`conf页面`
2. 进入`HTTPS解密`页面，确认启用`HTTPS解密`，在`域名`一栏添加
    ```
    *.limbuscompanycdn.org
    ```
3. 返回`conf页面`,进入`脚本`，点击`+`按钮添加如下脚本  

- 脚本1:PatchInfo，用于manifest.json  
类型:`http-response`  
引擎:`auto`  
脚本:
    ```js
    $httpClient.get(
    "Link1",
    function(err, resp, data) {

        $done({
            status:200,
            headers:{"Content-Type":"application/json"},
            body:data
        });

    });
    ```
    表达式:
    ```regex
    ^https://downloadcommon\.limbuscompanycdn\.org/.*LocalizePatchInfo\.json$
    ```
    最大尺寸:`0`  
    其他选项不修改 
******

- 脚本2:汉化资源包，用于localize_jp.zip  
    脚本:
    ```js
    $httpClient.get(
    "Link2",
    function(err, resp, data) {

        $done({
            status:200,
            headers:{"Content-Type":"application/zip"},
            body:data
        });

    });
    ```
    表达式:
    ```regex
    localize_jp
    ```
    其他选项同脚本1

### 启动游戏
确认
- 启用VPN
- 启用上述配置
- 启用上述脚本

**进入游戏会提示下载约17Mb资源文件则说明汉化成功**

## 最后
- 如果你觉得本项目对你有帮助，请帮忙点个 Star，这是对我最好的支持！
- ~~还不是为了自己在手机上玩得舒服，顺手搞的~~
- 对文本或其他方面有建议的可以在 Issue 中提出

## 致谢
Original project:
https://github.com/LocalizeLimbusCompany/LocalizeLimbusCompany

Licensed under CC BY-NC-SA 4.0.

## MADP开发者种子工程集成使用手册
### 一、搭建环境
>我们要求全部都安装，否则可能无法完整开发与调试。
#### 基础环境
* * *
Mac 或 Windows:
* Node.js (>=9.x), npm version 4+
##### 安装命令行工具
```
npm install eeui-cli -g
```
如果提示需要权限安装，请使用sudo安装：sudo npm install eeui-cli -g。

如果你在中国地区，我们还是推荐您使用 cnpm 安装：cnpm install eeui-cli -g。
>eeui-cli工具是否安装成功，可在终端执行eeui -version或者eeui -help相关信息即可验证
##### 更新命令行工具
```
npm update eeui-cli -g
```
#### 开发 iOS
开发平台: Mac
>CocoaPods 使用过程中遇到问题及时 Google。
##### 版本要求
* ruby: 2.5.0 以上
* cocoapods: 1.5.0 以上
其他版本会有环境问题
##### 安装
* Xcode (appStore 下载)
* CocoaPods(建议使用pod 1.5.3或之后版本)
1. 升级 rubygem 环境：$ sudo gem update --system
2. 移除现有 rubygem 镜像：$ gem sources --remove https://rubygems.org/
3. 添加gem.ruby-china镜像：$ gem source -a https://gems.ruby-china.com/
4. 安装 CocoaPods：$ sudo gem install cocoapods
5. 如果以上命令报错则执行：$ sudo gem install -n /usr/local/bin cocoapods
6. 最后执行：$ pod setup 过程比较漫长，请耐心等待执行完成
#### 开发 Android
开发平台: Mac/Windows
##### 版本要求
* AndroidStudio: 3.5.0+
##### 安装
JDK 是 JAVA 开发包，AndroidStudio 是 Android开发IDE，这两项不再做过多介绍。
* 下载并安装 JDK。
* 下载并安装 Android Studio。
> 如果您使用虚拟机进行跨平台开发，也需要配置好对应平台的所需环境。
#### 模拟器或真机安装
* iOS 开发中 xcode 已经自带了模拟器
* Android 开发者也可以使用 android studio 自带模拟器
### 二、创建项目
>执行此节之前，请确保必须的环境全都安装完成。
#### 下载种子工程
开发者可前往[开发者门户网站](www.pactera.com/)下载种子工程模板，下载完解压缩到本地，终端cd进入解压得到的文件夹；
>Tips
>
>[开发者门户网站](www.pactera.com/)当前正在搭建中，种子工程模板请邮件联系产品部[han.wang26@pactera-fintech.com];

种子工程目录结构
![921c7106cf1b2c802f2523dd12cbbe1d.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p55)
首次打开我们已经为您内置了由一些 demo，您可以看到相关的页面

npm项目及依赖说明
#### 配置APP相关信息
##### 1.前往MADP运管平台创建应用获取配置文档
平台地址：[http://10.114.14.60:8888/#/login](http://10.114.14.60:8888/#/login)
>具体如何创建应用请参见内容操作手册文档，文档请前往[开发者门户网站](www.pactera.com/)获取

![0e4bcfcce752d32e79826a639e98237c.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p56)@

##### 2.设置工程App信息
终端执行eeui setting就可以按提示设置App名称、版本等App信息。
![2a48e1684fed975faeb5b60adf89bcfc.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p51)@w=300



#### 安装node依赖
进入开发目录，执行 npm install 加载 node_modules Node.js基础模块
```
cd projectName
npm install
```
![ecf47290a98f69fe845da317533e6aef.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p52)@w=300
执行npm run dev 确认依赖安装没有问题
```
npm run dev
```

![a68710ffe9e8771e55c0ec244be0b8ba.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p53)@w=300

### 三、运行项目
#### iOS 运行项目
确保您已经安装完成 iOS 所需环境。
cd到iOS工程目录platforms/ios/eeuiApp 执行pod install命令来拉取iOS工程的依赖
```
pod install
```
首次执行时间会稍长，命令执行完毕后找到当前目录下 eeuiApp.xcworkspace 文件，双击即可唤起XCode打开 iOS 工程；

然后在XCode选择相应的模拟器（比如iPhone xs），点击▶按钮来运行项目。

#### Android 运行项目
确保您已经安装完成 Android 所需环境。

1.打开AndroidStudio软件然后Open Android工程目录platforms/android/eeuiApp。 2.待项目构建完成，点击 AndroidStudio 上方工具栏的 Run，即可运行项目。
>第一次打开 AndroidStuido 时，由于本地环境未配置好，AndroidStuido 会提示错误，按照 IDE 提示，点击 sync 同步一下，大部分环境问题都可以解决。

注：

* 可能您第一次构建的时间太长您也可以尝试解决 Android Studio 第一次导入项目太慢。实在不行就请耐心等待 Android Studio 自己构建完成吧
效果如下：
![a4cc802a48622b343688d3dceb243f2b.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p57)@w=150


#### 四、集成MADP基础能力插件
##### 插件安装
终端执行eeui plugin install madp/madp
![d1417ee3b1630f5318576b2c1adaa942.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p54)
##### 指定基础能力插件依赖版本
Android studio打开工程目录platforms/android/eeuiApp/build.gradle，在ext字段下添加基础能力插件的依赖版本，然后同步sync一下即可
```
madp_upgrade = "1.0.8"
madp_framework = "1.2.2"
madp_container = "1.4.0"
madp_rpc = "1.1.9"
madp_push = "1.0.0"
okhttp = "4.2.2"
okdownload_okdownload = "1.0.5"
okdownload_sqlite = "1.0.5"
okdownload_okhttp = "1.0.5"
okdownload_filedownloader = "1.0.5"
okdownload_ktx = "1.0.7"
```
![42ac80297a1e6e29c4fe0a6398151ce1.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p58)@w=300

##### 将代码配置文件放置到assets目录下
Android asset是位置：
platforms/android/eeuiApp/app/src/main/assets
![b0e92b2bea179e1178320b38ce7f9f80.png](evernotecid://ADC6FA8A-1FCD-4BFC-817B-EC9FFF69EC19/appyinxiangcom/28049159/ENResource/p59)@w=300

##### 验证插件正确安装
>备注：请测试机连接好vpn
IDE运行app，点击MADP内置组件-->rpc-->简单示例模块，点击发起请求，如果不报错即为验证通过，表明已经正常连接上网关

>至此 MADP基础能力的集成完成










# Jenkins <http://jenkins-ci.org/>
###### 自动化集成打包发布

1. Mac中安装环境
    * java安装环境,jenkins需要java7+
    * jenkins官网下载 jenkins-1.643.pkg
    * 或者采用brew安装 brew install jenkins (推荐)
2. 启动jenkins
    * 命令 java -jar ***/jenkins.war
    * 若采用brew安装直接使用 jenkins命令
3. 配置环境,进入http://localhost:8080
	* 在系统管理->管理插件中,安装
        - Git plugin , Git client plugin , Git server plugin
        - Xcode integration , SICCI for Xcode Plugin , Clang Scan-Build Plugin
    * 重启jenkins
4. 新建项目
    * 创建一个free style的Item项目
    * 源码管理选择Git,输入Http地址,Credentials里面填入Git的帐号密码,分之上默认是master
        - 一直想采用ssh模式获取,可是到目前为止还未成功,总是失败
    * 构建触发器Poll SCM
        - H/5 \* * * * (每5分钟触发一次)
    * 增加构建步骤,选择Xcode
        - General build settings
            + Target (项目中Target的名称)
            + Clean before build?  YES 
            + Generate Archive?    YES (这样Xcode中Organizer可以看到)
            + Configuration?       Release/Debug
            + Pack application and build .ipa?   YES
            + .ipa filename pattern?    XXX_${VERSION}_${BUILD_DATE}
            + Output directory? /Users/xxx/Desktop
        - Code signing & OS X keychain options
            + 可以增加一个系统插件 Keychains and Provisioning Profiles Management
            + Code Signing Identity
            + Embedded Profile (输入profile文件全路径包括名称和扩展名)
            + [10.10系统之后需要修改的地方](http://stackoverflow.com/questions/32504355/error-itms-90339-this-bundle-is-invalid-the-info-plist-contains-an-invalid-ke/32762413#32762413)
        - Advanced Xcode build options(很多都有英文说明)
            + Clean test reports? YES(会用的话可以选NO)
            + Xcode Schema File?  一般跟Target是一样的
            + SDK? (不用填,我也不知道格式是啥)
            + SYMROOT? (不用填,我也不知道格式是啥)
            + Custom xcodebuild arguments? (不填)
            + Xcode Workspace File? ${WORKSPACE}/ProjectName (项目.xcworkspace文件路径名称,没有后缀)
            + Xcode Project Directory? ${WORKSPACE}/ProjectName (项目.xcodeproj文件路径名称,没有后缀)
            + Xcode Project File?
            + Build output directory? ${WORKSPACE}/build (编译时的文件路径,随便填)
   	* 保存
5. 立即构建项目,运行成功


#####FTP问题
* 开启Mac自带的ftp功能,可用[Mountain Tweaks](http://tweaksapp.com/download_mountain.html)
* 增加jenkins插件 FTP publisher plugin
* 在jenkins系统设置中FTP repository hosts设置相应内容
    - Profile Name :名称 随便填
    - hostname : localhost
    - Port : 21
    - TimeOut : 3000
    - Root Repository Path : /Users/xxx 自己选择
    - User Name : 自己Mac系统登录时的用户名
    - Password : 自己Mac系统登录时的密码
* 在jenkins项目配置中增加构建后操作 Publish artifacets to FTP
    - FTP site : 选择刚才创建的
    - Files to upload, Source : 需要上传的文件 如ipa/*.ipa
    - Files to upload, Destination : ftp服务器中的文件夹


###### 未完成

1. 出来的ipa包可以直接发送给测试邮件,或者fir等网站
2. xcarchive文件提交到某一个git中或者ftp服务器保存起来
3. 如果出现关于libswiftCore的错误请参考[->Link](http://stackoverflow.com/questions/25297638/how-do-i-codesign-a-swift-app-via-the-commandline)
4. 签名一直出错中(2016.9.30已解决)


参考链接 [->Link](http://www.cocoachina.com/ios/20160804/17281.html)

 
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
            + Code Signing Identity (直接输入证书名称,iPhone Developer: XXX (???))
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



未完成
3. 出来的ipa包可以直接发送给测试邮件
4. xcarchive文件提交到某一个git中或者ftp服务器保存起来？


如果有哪位大神知道,可以联系我或者推荐我文章哦



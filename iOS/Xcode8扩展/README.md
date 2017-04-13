Xcode8 增加iOS6,iOS7 SDK

将 6.0 6.1 7.0 7.1 文件夹（这些文件夹来自Xcode7.3.1安装包）添加到
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/

将以下路径上的文件夹和文件的权限 对 everyone 改成 读与写(默认是只读) 最好不要影响其他文件
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/SDKSettings.plist
然后用Xcode打开SDKSettings.plist
编辑DefaultProperties DEPLOYMENT_TARGET_SUGGESTED_VALUES 增加 6.0 6.1 7.0 7.1
将这些文件夹与文件的权限恢复回去
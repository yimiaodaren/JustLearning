##Xcode8+ 增加iOS6,iOS7 SDK

- 将 6.0 6.1 7.0 7.1 文件夹（这些文件夹来自Xcode7.3.1安装包）添加到
> /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport/

- 找到 
> /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS.sdk/SDKSettings.plist

- 然后用Xcode打开SDKSettings.plist
> 编辑DefaultProperties DEPLOYMENT_TARGET_SUGGESTED_VALUES 增加 6.0 6.1 7.0 7.1

###	
    对该文件权限操作不好的，先把这个文件复制到桌面
    
    ls -l //查看权限
    -rw-rw-r--  1 root  wheel  997  2  3 00:06 SDKSettings.plist
    
    //修改成最高权限后进行修改保存
    sudo chmod 777 SDKSettings.plist
    
    //文件覆盖回去
    
    //把权限和所有者恢复
    sudo chmod 664 SDKSettings.plist
    sudo chown root SDKSettings.plist 
    
    
    
    
    

###### 目前无法增加iOS7模拟器
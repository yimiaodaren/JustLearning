# RSA

###多个rsa操作
1. 生成rsa文件,另外命名x_rsa
	ssh-keygen -t rsa -C "xxx"
2. 在~/.ssh下 文件名为x_rsa x_rsa.pub
3. 在/etc/ssh/ssh_config添加

###
	 Host github.com 
	 IdentityFile ~/.ssh/x_rsa
    

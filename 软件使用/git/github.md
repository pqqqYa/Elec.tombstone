[github网址](https://github.com/)

git remote -v 查看当前所有远程地址别名
git remote add 别名 远程地址
# 1. 推送本地库
git push 别名 分支
或者github客户端直接上传
![[Pasted image 20221219215657.png]]
上面检查和云端库有没有区别

# 2. 拉取云端库
git pull 别名 分支
上传需要安装配置[[OpenSSL配置|OpenSSL]]才可以
和推送一样可以直接用github客户端
# 3. 克隆库
git clone <github链接>
克隆公共库代码不需要账号，只要有链接就可以
在[[cmd操作|命令提示符]]里面输入代码
# 1. 切换源
## 1. 清华大学
`pip config set global.index-url `
https://pypi.tuna.tsinghua.edu.cn/simple
## 2. 官方
`pip config set global.index-url` 
https://pypi.org/simple/
# 2. 查看pip位置
	`python -m site` 
# 3. 安装
## 1. 安装
`pip install 名字`
## 2. 查看路径
再次输入`pip install 名字`就可以看到安装位置
# 4. 查看pip安装了多少包
`pip list`
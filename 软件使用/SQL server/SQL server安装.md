知乎链接[SQL server和SSMS安装 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/638784414)
# 一、下载所需要的文件

## SQL server

[SQL Server 下载 | Microsoft](https://www.microsoft.com/zh-cn/sql-server/sql-server-downloads)

![](https://pica.zhimg.com/80/v2-d6c663ad040002c6c4d38b0eccd8d7dd_720w.png?source=d16d100b)

下载Developer的免费版本

## SQL Server Management Studio (SSMS)
[下载 SQL Server Management Studio (SSMS) - SQL Server Management Studio (SSMS) | Microsoft Learn](https://learn.microsoft.com/zh-cn/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)


# 二、安装SQL server

![](https://picx.zhimg.com/80/v2-c8b211a95397f75a9fa80fe6f3fac540_720w.jpeg?source=d16d100b)

选择”下载介质“

![](https://pic1.zhimg.com/80/v2-4520f89fd05f3207e9ecf87bf1fcb517_720w.jpeg?source=d16d100b)


这里选择”ISO“然后选择下载位置，这里只是下载的文件，放在哪里都可以

![](https://pic1.zhimg.com/80/v2-71694166608c179ad5f820b859c8c5f4_720w.jpeg?source=d16d100b)


直接双击ISO文件，文件会在虚拟光驱被打开

![](https://pica.zhimg.com/80/v2-b652db0e0c4a03c2f60de1fc10f8da88_720w.jpeg?source=d16d100b)


打开以后直接点击Setup.exe开始安装

![](https://pic1.zhimg.com/80/v2-78c450297106b1ce6e3df12310bff24b_720w.png?source=d16d100b)


点击”全新 SQL Server独立安装或向现有安装添加功能“

![](https://picx.zhimg.com/80/v2-b8c3f4fda709e8145d0f54f0fb34e192_720w.png?source=d16d100b)

选择”Developer“版本

![](https://picx.zhimg.com/80/v2-03d171a57e7684ea6eeb8ddf1f31251a_720w.jpeg?source=d16d100b)

接受，直接下一步

![](https://picx.zhimg.com/80/v2-20e02222c5007ea47f53b9fd73f4cd8b_720w.jpeg?source=d16d100b)



![](https://picx.zhimg.com/80/v2-5a7867755dd3f94a65388f5f8d0047f9_720w.jpeg?source=d16d100b)

下一步

![](https://picx.zhimg.com/80/v2-20e02222c5007ea47f53b9fd73f4cd8b_720w.jpeg?source=d16d100b)


不要勾选，下一步

![](https://picx.zhimg.com/80/v2-ea1d09bdeec5270641f96b5bcb5647fd_720w.jpeg?source=d16d100b)


下一步

![](https://picx.zhimg.com/80/v2-e0585236e430f34d681ea445d1a6e2e7_720w.jpeg?source=d16d100b)

这里开始检测环境，一般情况下不会有问题的，这个地方的”windows防火墙“警告不用管

![](https://picx.zhimg.com/80/v2-db485c602d7220ef83fc302558855459_720w.png?source=d16d100b)



这里默认是勾选了的，取消勾选

![](https://picx.zhimg.com/80/v2-deeae44836b08111f873e6126d695fbb_720w.png?source=d16d100b)

如果是学生学习，只需要选择”数据库引擎服务“就可以了

![](https://pic1.zhimg.com/80/v2-65b50600b53e8f0ae797477cda660a7f_720w.png?source=d16d100b)


选”默认实例“，点击下一步

![](https://picx.zhimg.com/80/v2-55b404e7687055282e19c84a37572977_720w.png?source=d16d100b)


这里全部选择”自动“

![](https://picx.zhimg.com/80/v2-9a5b7c41fba8a3a019d22c32771df664_720w.png?source=d16d100b)


选择”混合模式“，设置密码，密码后面有用，要记住

![](https://picx.zhimg.com/80/v2-896f627f0cb10409e53096c11ce08966_720w.jpeg?source=d16d100b)


下一步开始默认位置安装就可以了

![](https://pica.zhimg.com/80/v2-a9f79242651bcf362d9add95a5604dab_720w.jpeg?source=d16d100b)


这里SQL Server就安装完成了

# 三、安装SSMS (SQL Server Management Studio）

![](https://picx.zhimg.com/80/v2-089a963bc63f3af607a673100a5e8156_720w.jpeg?source=d16d100b)


直接双击下载好的文件点开就行了

![](https://pic1.zhimg.com/80/v2-be5e76f4af2fd4ab4a8805b66d288f70_720w.jpeg?source=d16d100b)


![](https://picx.zhimg.com/80/v2-a7ce4905cf99903a25ad624bf552774d_720w.jpeg?source=d16d100b)


重启算计完成


# 四、测试

![](https://picx.zhimg.com/80/v2-c46a19e8056d8156094673a043688ff1_720w.jpeg?source=d16d100b)


搜索”SQL Server Management Studio“直接点开

![](https://pica.zhimg.com/80/v2-9ac5e6cc99769e3a056883d5fa1a753d_720w.jpeg?source=d16d100b)


![](https://pica.zhimg.com/80/v2-8fba104582539046ce9daab6252a7935_720w.jpeg?source=d16d100b)


服务器类型(T)：数据库引擎

身份验证(A)：Windows身份验证

![](https://picx.zhimg.com/80/v2-a7866efd6ec06cbfcfcc54c5fb641f95_720w.jpeg?source=d16d100b)


选择”新建查询“或者直接Ctrl+N

![](https://picx.zhimg.com/80/v2-55f9987a27e614d525f0130b70336517_720w.jpeg?source=d16d100b)


创建一个新的数据库”testZ“

![](https://picx.zhimg.com/80/v2-ba2379cbe8469dfaef3344f8c4063855_720w.jpeg?source=d16d100b)


这里出现了我们刚才创建的数据库说明完成了


# 五、创建桌面快捷方式

![](https://picx.zhimg.com/80/v2-36be97938e292cfd9f618351c1b55c32_720w.png?source=d16d100b)


打开文件所在位置，把快捷方式拖出来到桌面即可

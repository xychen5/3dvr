## 1 准备相关环境
### 1-1 安装latex相关文档工具
ref：
```
vscode + miktex: 
https://blog.csdn.net/yinqingwang/article/details/79684419
https://blog.csdn.net/billy145533/article/details/102903395
```

## 2 复现以及熟悉hexi项目
项目地址：[hexi](https://github.com/breeswish/hexi)
下载相关的项目到本地，阅读readme然后尝试复现该项目；

### 2-1 准备项目需要的环境
- 1 nodejs
安装教程： [nvm + nodejs安装](https://www.cnblogs.com/zaid/p/12263149.html)
  + 注意事项： 教程里的全局安装有问题，所以该步骤跳过不做，**务必记得切换镜像源到taobao**
- 2 python3.6+，然后安装相关python包: 
  + sanic yapsy protobuf pyee git+https://github.com/iceb0y/aiomongo websockets

  + 安装方法：
```sh
python3 -m pip install -r requirements.txt
#以上方法里面由于源的问题拿不到相关的包，指定源头：
pip install sanic -i http://pypi.tuna.tsinghua.edu.cn/simple/ --trusted-host pypi.tuna.tsinghua.edu.cn

#若指定源安报错的解决方案：[error: Microsoft Visual C++ 14.0 is required.](https://blog.csdn.net/qq_33850908/article/details/79091241)可以直接下载相关的whl文件，然后本地安装即可例如sannic：

在该网址获得whl包：https://pypi.tuna.tsinghua.edu.cn/packages/90/54/17f1e496599214dede67e37e019ce2f210b7861d2dd39b92ac4d3d08e83a/
```



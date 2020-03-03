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

- 3 使用cnpm代替npm
  + 相应的教程：[cnpm代替npm](https://www.cnblogs.com/silfox/p/8512394.html)

### 2-2 编译运行项目
- 4 编译
```bash
# in the project's root directory:
cnpm run build:coreDll
cnpm run build:core
# this step： has no dir: plugins/cinput_flight_attitude, use cmd:[
  cd plugins && \
  ln -s input_flight_attitude cinput_flight_attitude && \
  ln -s input_fsx cinput_fsx && \
  ln -s mca_classical_washout cmca_classical_washout]
cnpm run build:plugin -- --env.pluginName cinput_flight_attitude
cnpm run build:plugin -- --env.pluginName cinput_fsx
cnpm run build:plugin -- --env.pluginName cmca_classical_washout
cnpm run build:plugin -- --env.pluginName output_stewart_visualize

# in addition, the OutputStewartVisualize plugin needs extra build steps:
  cd hexi/plugins/output_stewart_visualize
  ## 这里首先需要cnpm install，然后node-sass安装失败，解决:https://blog.csdn.net/weixin_34332905/article/details/88018267?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task
  cnpm install
  cnpm install node-ssas
  cnpm install
  cnpm start
```
- 5 运行
```bash
# in the project's root directory:
# 任然有依赖： pip install uvloop
python -m hexi.server

```


- yarn init -y初始化项目
- yarn add -D vite 打包工具安装
- yarn add vue 安装vue依赖

<img src="assets/image-20230408164303940.png" alt="image-20230408164303940" style="float: left; zoom: 50%;" />

### 创建index.html & src/index.js文件

在index.html中引入src/index.js， 并初始化body id=app进行绑定

![image-20230408164541253](assets/image-20230408164541253.png)

接下来我们在index.js进行vue的编写

<img src="assets/image-20230408164921191.png" alt="image-20230408164921191" style="zoom:50%;float:left" />

我们来试着运行， 先编写下脚手架(用命令进行构建运行,有点像makefile格式)

<img src="assets/image-20230408165051277.png" alt="image-20230408165051277" style="zoom:50%;float:left" />

接下来，用`yarn dev`cmd命令我们就可以执行运行项目

<img src="assets/image-20230408165324340.png" alt="image-20230408165324340" style="zoom:50%;" />

怎么什么都没有。。。

![image-20230408165622125](assets/image-20230408165622125.png)

是因为vue默认版本不支持template， 我们可以将vue换成`vue/dist/vue.esm-bundler.js`

<img src="assets/image-20230408165742222.png" alt="image-20230408165742222" style="zoom:50%;" />

这样页面就有效果了

![image-20230408165806553](assets/image-20230408165806553.png)
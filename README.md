# 这是用来部署java后台项目的shell脚本


- 支持dev、qa、生产多环境部署。
- 支持多节点部署。
- 支持多应用选择部署。

-----

# 操作步骤：
  - 执行main.sh sh ./main.sh  
  - 进行交互式操作，内部会自动调用remoteshell.sh进行服务器的一系列动作。

--------

# 效果演示
  
-#  启动：  ./main.sh
 -   （1）首先选择需要部署的应用：（我们的项目是如下4个应用，这个可以根据不同的项目在shell里进行扩展）
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-8cd3d483981be608.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （2）选择部署的环境，（我们的项目是3个环境dev、qa、prod）
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-32c026a22bdcf5b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （3）选择部署方式，（我做的是自动部署或者手动部署）
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-4df7ff74e410269a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （4.1）先说手动部署，里面包括所有的准备动作
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-59a97b57191ddb37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （4.2）再说自动部署，自动执行手动部署的全部动作
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-3185a2edc0a63661.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （5）进入循环，选择部署其他环境或其他应用
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-99ef2a626814ff2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

-   （6）结果，启动项目完毕
![Alt text](https://upload-images.jianshu.io/upload_images/17375175-ebc4d2e914a88820.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


三、备注

---------

# 备注
*暂时不支持前台部署，后续加入。
大家一起来升级吧。*



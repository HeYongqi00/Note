### <center> Webots概述
#### 1.Webots是什么
&emsp;&emsp;Webots是一款专业的移动机器人仿真软件包，允许用户创建具有质量、关节、摩擦系数等物理属性的3D虚拟世界，用户可以添加简单的被动对象或移动机器人的主动对象。
#### 2.Webots仿真
&emsp;&emsp;Webots仿真需要什么：
- 一个定义机器人和环境的地图文件(.wbt)，(.wbt)文件有时依赖于(.proto)文件和textures。
- 上述机器人的控制程序。
- 一个可选的物理插件，用于修改Webots常规的物理行为。
#### 3.什么是控制器
&emsp;&emsp;控制器就是控制世界文件中指定机器人的计算机程序，可以用C、C++、Python、Java、Matlab编写，
#### 4.什么是主管控制器(Supervisor Controller)
&emsp;&emsp;主管控制器是主管字段下设置为`True`的控制器，通常是由人类操作员而不是真正的机器人执行，主管控制器有权访问特权操作，比如可以让机器人移动到随机位置。
#### 5.Webots中的Solid节点
&emsp;&emsp;`Solid`节点表示刚体，可以忽略形变。为了定义一个刚体，需要创建一个刚体节点，在节点内，根据刚体的特性设置不同过的子节点。需要下图展示了一个刚体节点和他的子节点。
![Webots节点](https://img-blog.csdnimg.cn/f856c431a874485590048570eab17dad.png)
`Solid`节点的图形是由子节点里面的`Shape`节点定义的，碰撞边界在`boundingObject`定义，图形和碰撞边界一般相同，但是也可以不同，`Physics`节点定义对象是静态环境还是动态环境。
&emsp;&emsp;下面在环境中新建一个球的例子
- 1.新建`Solid`节点，在`Base nodes`里面选择`Solid`;
- 2.在他的子节点`children`添加一个`shape`节点;
- 3.`shape`节点的`appearance`选择`PBRAppearance`;
- 4.`geometry`表示物体的形状，选择`Sphere`;
- 5.物体边界`boundingObject`也选择`Sphere`,可以设置`DEF`名字，`DEF`机制允许在一个地方定义节点并在场景树的其他地方调用。




### <center> A Hierarchical Control Framework for Drift Maneuvering of Autonomous Vehicles
### <center> 自动驾驶车辆漂移操作分层控制框架
#### 1.Motivation
Maneuvering an autonomous vehicle under drift condition is critical to the safety of autonomous vehicles when there is a sudden loss of traction due to external conditions such as rain or snow, which is a challenging control problem due to the presence of significant sideslip and nearly full saturation of the tires.
当由于雨雪等外部条件而突然失去牵引力时，在漂移状态下操纵自动驾驶汽车对自动驾驶汽车的安全性至关重要。由于存在显著的`侧滑`和`轮胎饱和`，这是一个具有挑战性的控制问题。
#### 2.Question
- 漂移状态会对车辆有什么影响？影响哪些指标？这些指标怎么体现？
&emsp;&emsp;漂移状态车辆的特征就是**侧滑角大**，**轮胎接近饱和**，
- 如何建立车辆打滑的数学模型？
- 分层控制器是怎么设计的，以及是怎么解耦的？
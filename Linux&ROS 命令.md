Linux 命令  俺可以～～😄

- 打开新的command window： Ctrl + Alt + t

- 常用更新代码

  `sudo apt-get update`,`sudo apt-get upgrade`,`sudo apt autoremove`

  

- 查看Ubuntu版本

  ```Linux
  sudo lsb_release -a
  ```


- cd “改变工作路径”

  cd 【目录路径】

  

- pwd “显示当前目录的绝对路径”

  **print the working directory** 

  ```shell
  $ pwd
  ```

  ![image-20200304153255857](pic/image-20200304153255857.png)

- mkdir “创建一个目录”

  mkdir 【-p】【目录名称】

  - -p 确保目录名称存在，不存在的就建一个

  

- ls “列出目录的内容”

  

- touch “改变文件或目录时间” --生成新文件

  `touch [-acfm][-d<日期时间>][-r<参考文件或目录>] [-t<日期时间>][--help][--version][文件或目录…]`

  > ls -l 可以显示档案的时间记录

  - a 改变档案的读取时间记录。
  - m 改变档案的修改时间记录。
  - c 假如目的档案不存在，不会建立新的档案。与 --no-create 的效果一样。
  - f 不使用，是为了与其他 unix 系统的相容性而保留。
  - r 使用参考档的时间记录，与 --file 的效果一样。
  - d 设定时间与日期，可以使用各种不同的格式。
  - t 设定档案的时间记录，格式与 date 指令相同。
  - --no-create 不会建立新档案。
  - --help 列出指令格式。
  - --version 列出版本讯息。

  

- mv “文件或目录改名，移动文件”

  mv 【选项】【源文件or目录】【新文件or目录】

  - -i: 若指定目录已有同名文件，则先询问是否覆盖旧文件;
  - -f: 在 mv 操作要覆盖某已有的目标文件时不给任何指示;  

  | 命令格式         | 运行结果                                                     |
  | :--------------- | :----------------------------------------------------------- |
  | mv 文件名 文件名 | 将源文件名改为目标文件名                                     |
  | mv 文件名 目录名 | 将文件移动到目标目录                                         |
  | mv 目录名 目录名 | 目标目录已存在，将源目录移动到目标目录；目标目录不存在则改名 |
  | mv 目录名 文件名 | 出错                                                         |



- cp “复制文件/目录到另一个文件/目录”

  cp 【选项】【源文件or目录】【新文件or目录】

  - -a：此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合。
  - -d：复制时保留链接。这里所说的链接相当于Windows系统中的快捷方式。
  - -f：覆盖已经存在的目标文件而不给出提示。
  - -i：与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖。
  - -p：除复制文件的内容外，还把修改时间和访问权限也复制到新文件中。
  - -r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。
  - -l：不复制文件，只是生成链接文件。



- rm “删除文件/目录”

  touch【选项】【文件/目录名称】

  - -i 删除前逐一询问确认。
  - -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
  - -r 将目录及以下之档案亦逐一删除。

  删除当前目录下的所有文件及目录，命令行为：`rm  -r  * `

## vim 常用

```shell
vim fileName	//vim打开文件，文件需带有绝对路径
i				//编辑文件
esc     		//退出编辑状态

退出先ctl+c
wq：	保存退出
:x： 保存退出
wqa：保存所有文件并退出
q!： 不保存退出
qa!：有多个文件被打开，同时退出

x: 删除光标后一个字符,相当于 Del 
 
X: 删除光标前一个字符,相当于 Backspace

dd: 删除光标所在行,n dd 删除指定的行数 

u: 一步一步撤销 
 
Ctrl+r: 反撤销

/: str查找
　　　　n: 下一个
　　　　N：上一个
```

![img](../../Documents/GitHub/ROS-Learning-note/pic/aHR0cHM6Ly9pbWFnZXMyMDE4LmNuYmxvZ3MuY29tL2Jsb2cvMTI2OTYyOS8yMDE4MDMvMTI2OTYyOS0yMDE4MDMyODEyMzgyODU5OC0xNDIzMjI2MjMyLmpwZw.jpeg)

## ROS命令

#### **常用指令：**

>```pytb
># 建立工作空间
>$mkdir -p ~/catkin_ws/src   
>$cd ~/catkin_ws
>$catkin_make
>
># 编译
>$cd ~/catkin_ws 
>$catkin_make 
>$source ~/catkin_ws/devel/setup.bash # 编译完成后要source刷新环境
>
># rospack
># 查找某个pkg的地址
>$ rospack find [package_name]
># 列出本地所有的pkg 
>$ rospack list 
>
># roscd 
># 跳转到某个pkg路径下
>$ roscd package_name
>
>#查看ROS package path
>$ echo $ROS_PACKAGE_PATH
>
>#roscd log ROS存log文件处（没roscore过不存在）
>$ roscd log
>
># rosls 
># 列举出某个pkg下的文件信息
>$ rosls package_name
>
># rosed 
># 编辑pkg中的文件
>$ rosed package_name  file_name 
>
># catkin_create_pkg 
># 创建一个pkg 
>$ catkin_create_pkg <pkg_name> [deps] 
>
># rosdep 
># 安装某个pkg所需的依赖
>$ rosdep install [pkg_name} 
>```

![](../../Documents/GitHub/ROS-Learning-note/pic/v2-07a18520cf03a3589e0686eea7564209_1440w.jpg)

#### catkin

目前编译ROS的Package有两种方法：

- catkin_make
- catkin build

#### **创建workspace**

**注意: catkin编译之前需要回到工作空间目录，`catkin_make`在其他路径下编译不会成功。编译完成后，如果有新的目标文件产生（原来没有），那么一般紧跟着要source刷新环境，使得系统能够找到刚才编译生成的ROS可执行文件。这个细节比较容易遗漏，致使后面出现可执行文件无法打开等错误。**

```shell
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

For Python3 最后一个指令:

```shell
$ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

完成catkin_make的workspace文件包含三个文件夹：

`build`, `devel`, `src`

- src/: ROS的catkin软件包（源代码包） **所有的code在src文件中**
- build/: catkin（CMake）的缓存信息和中间文件
- devel/: 生成的目标文件（包括头文件，动态链接库，静态链接库，可执行文件等）、环境变量

**每次改完code**需要new build需要terminal在catkin_ws文件中**再次输入**：`catkin_make`

![img](../../Documents/GitHub/ROS-Learning-note/pic/catkin_flow.jpg)

**source workspace**

添加程序包到全局路径bashrc

```shell
$ echo "source catkin_ws/devel/setip.bash">> ~/.bashrc
$ source ~/.bashrc
```

source setup.bash file: 保证在进入devel文件内

```shell
$ source devel/setup.bash
```

**查看ros包路径环境变量是否配置好**

```shell
$ echo $ROS_PACKAGE_PATH
```

![image-20200304151651049](pic/image-20200304151651049.png)

catkin编译的工作流程如下：

1. 首先在工作空间`catkin_ws/src/`下递归的查找其中每一个ROS的package。
2. package中会有`package.xml`和`CMakeLists.txt`文件，Catkin(CMake)编译系统依据`CMakeLists.txt`文件,从而生成`makefiles`(放在`catkin_ws/build/`)。
3. 然后`make`刚刚生成的`makefiles`等文件，编译链接生成可执行文件(放在`catkin_ws/devel`)。\

也就是说，Catkin就是将`cmake`与`make`指令做了一个封装从而完成整个编译过程的工具。catkin有比较突出的优点，主要是：

- 操作更加简单
- 一次配置，多次使用
- 跨依赖项目编译



#### package的创建

1个package下常见的文件、路径有：

```
  ├── CMakeLists.txt    #package的编译规则(必须)
  ├── package.xml       #package的描述信息(必须)
  ├── src/              #源代码文件
  ├── include/          #C++头文件
  ├── scripts/          #可执行脚本
  ├── msg/              #自定义消息
  ├── srv/              #自定义服务
  ├── models/           #3D模型文件
  ├── urdf/             #urdf文件
  ├── launch/           #launch文件
```

其中一个Catkin的软件包（package）必须要包括两个文件：

- package.xml: 包括了package的描述信息
  - name, description, version, maintainer(s), license
  - opt. authors, url's, dependencies, plugins, etc...
- CMakeLists.txt: 构建package所需的CMake文件
  - 调用Catkin的函数/宏
  - 解析`package.xml`
  - 找到其他依赖的catkin软件包
  - 将本软件包添加到环境变量

**创建package在`catkin_ws/src`下**

```shell
$ cd ~/catkin_ws/src
$ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
$ cd ~/catkin_ws
$ catkin_make
```

例子：

```shell
$ catkin_create_pkg my_tut roscpp rospy std_msgs
```

![image-20210219053843259](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219053843259.png)

这样就会在当前路径下新建`my_tut`软件包，包括：

```
  ├── CMakeLists.txt
  ├── include
  │   └── my_tut
  ├── package.xml
  └── src
```

再次回到workspace中catkin_make & source至.bashrc

```shell
$ cd ~/catkin_ws
$ catkin_make

$ . ~/catkin_ws/devel/setup.bash
```



#### Package安装方法

- Deb二进制包安装方式

deb方式安装方法十分简单，根据ROS版本，直接运行apt-get命令，例如：

```shell
$ sudo apt-get install ros-kinetic-camera-calibration
```

- 源码安装方式

源码安装方式稍微复杂，安装方法如下：

1. 创建catkin工作空间
2. 在catkin工作空间的src文件夹下，下载ROS的Package源代码
3. 使用catkin build命令编译安装

- **大救星Tab键**

不清楚的不打完, 按Tab键 once:会自动补全;twice:list installed packages

```
rosls <<<TAB twice>>
# list all currently installed packages
```



#### 创建 ROS 工作空间

###### 启动ROS

```shell
$ roscore
```

**新窗口**

###### 创建workspace

```shell
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
#或者 $ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

For Python3 最后一个指令:

```shell
$ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

###### 编译 ROS 程序

```shell
$ cd ~/catkin_ws/
$ catkin_make
#或者 $ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

###### 添加程序包到全局路径

```shell
$ echo "source catkin_ws/devel/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```



#### Package 相关操作

###### 创建 Package 并编译

```
$ cd ~/catkin_ws/src
$ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
$ cd ~/catkin_ws
$ catkin_make
```

###### 查找 Package

```shell
$ rospack find [package name]
```

###### 查看 Package 依赖 

```shell
$ rospack depends <package_name>
$ rospack depends1 <package_name>
```

These dependencies for a package are stored in the **package.xml** file

#### Node 相关

node不可以用相同的名字

###### 查看所有正在运行的 Node

```shell
$ rosnode list
```

###### 查看某节点信息

```shell
$ rosnode info [node_name]
```

###### 结束某个node

```shell
$ rosnode kill [node_name]
```

###### 测试连接节点

Ping (test connectivity) a node repeatedly. rosrun了的才会有反应

```shell
$ rosnode ping [node_name] 
```

![img](../../Documents/GitHub/ROS-Learning-note/pic/masterandnode.png)

###### py例子1: **先new terminal运行roscore**

python code位于**Jian/python_ws/src/my_tut/scripts**

`chmod +x first_node.py`变绿色可执行文件

每次修改不需要catkin_make,直接运行即可

![image-20210219065416854](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219065416854.png)

![image-20210219065507649](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219065507649.png)

###### py例子2：

每0.1s输出一个info

![image-20210219070502219](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219070502219.png)

node运行中可查看`rosnode list`

无法同时launch多个同一个名字的node（可改名字）

###### c++例子1:

一直报错因为cpp '' 和""不同！！要用双引号。

为什么vs code更新但是vim没有：move了fist_node.cpp 的位置没有在VS code 重新打开并保存

![image-20210219195758376](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219195758376.png)

cpp code位于**Jian/python_ws/src/my_tut/src**

里面node的名字也和python不同，可以同时在一个ROS中运行

修改完需要打开Jian/python_ws/src/my_tut/CMakeLists.txt

For Noetic, Python version at least: 3.0.2

find_package有：roscpp

![image-20210219173654021](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219173654021.png)

添加这两行指令：cpp executable+link libraries

![image-20210219173527501](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219173527501.png)

需要catkin_make: `jian@jian-ubuntu:~/python_ws$ catkin_make`

新生成executable node_cpp

![image-20210219214229010](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219214229010.png)

###### c++例子2

![image-20210219220303814](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219220303814.png)

没有新node，不需要修改CMakeList.txt

![image-20210219220427715](../../Documents/GitHub/ROS-Learning-note/pic/image-20210219220427715.png)

显示新node：my_first_cpp_node

###### 运行 Node

上边run的方法太繁琐，使用rosrun

**新终端运行**

```shell
$ rosrun [package_name] [node_name]

$ rosrun my_tut first_node.py
$ rosrun my_tut node_cpp
```

注意：executable python是文件名;cpp是CMakeLists.txt中自己定的名字。 需要rosrun node 中查看，ctl+c退出就不显示了

![image-20210220002123349](../../Documents/GitHub/ROS-Learning-note/pic/image-20210220002123349.png)

###### 图形化显示 topic rqt_graph

```shell
$ rosrun rqt_graph rqt_graph
$ rosrun rqt_plot rqt_plot
```

钩掉Debug

![image-20210220004217418](../../Documents/GitHub/ROS-Learning-note/pic/image-20210220004217418.png)

rosrun my_tut node_cpp

rosrun my_tut first_node.py

![image-20210220010759209](../../Documents/GitHub/ROS-Learning-note/pic/image-20210220010759209.png)

###### node with turtlesim

新终端：打开turtlesim

```shell
$ rosrun turtlesim turtlesim_node  //负责显示turtle的node
```

![image-20200305114410201](../../Documents/GitHub/ROS-Learning-note/pic/image-20200305114410201.png)

新终端:键盘控制turtlesim

```shell
$ rosrun turtlesim turtle_teleop_key //负责控制turtle的node
```

![image-20200305114644654](../../Documents/GitHub/ROS-Learning-note/pic/image-20200305114644654.png)

![image-20210220012714038](../../Documents/GitHub/ROS-Learning-note/pic/image-20210220012714038.png)

**turtlesim_node, turtle_teleop_key是 turtlesim这个package中executable的名字**

**/turtlesim, /teleop_turtle是node的名字**

#### Topic相关

- topic的通信方式是ROS中比较常见的单向异步通信方式

- topic 有massage type
- ROS master帮助node 订阅 topics

>```pytb
># 与Topic、Msg相关命令
>
># rostopic 
># 列出当前所有的topic 
>$ rostopic list 
># 显示某个topic的属性信息
>$ rostopic info /topic_name 
># 显示某个topic的内容
>$ rostopic echo /topic_name 
># 向某个topic发布内容
>$ rostopic pub /topic_name 
>
># rosmsg 
># 列出系统上所有的msg
>$ rosmsg list 
># 显示某个msg内容
>$ rosmsg show /msg_name
>```

###### 查看rostopic所有操作

```shell
$ rostopic -h
```

```shell
rostopic bw     display bandwidth used by topic
rostopic echo   print messages to screen
rostopic hz     display publishing rate of topic    
rostopic list   print information about active topics
rostopic pub    publish data to topic
rostopic type   print topic type
```

Taha:`rostopic pub -l /rostopic name [TAB]`

###### 查看所有 Topic 列表

```shell
$ rostopic list
```

###### 图形化显示 topic rqt_graph

```shell
$ rosrun rqt_graph rqt_graph
$ rosrun rqt_plot rqt_plot
```

###### 查看某个 Topic 信息

```sh
$ rostopic echo [topic]
```

###### 查看 Topic 消息格式

```shell
$ rostopic type [topic]
$ rosmsg show [msg_type]
```

###### 向topic发布消息

```shell
$ rostopic pub [topic] [msg_type] [args]
```

###### py例子publisher

在 ~/python_ws/src/my_tut/scripts 建立 pub.py, 让其excutable

`chmod +x pub.py`, pub.py:

```python
#!/usr/bin/env python3

import rospy
from std_msgs.msg import String

if __name__=='__main__':
    rospy.init_node('robot_news_transmitter') #initialized node's name
    pub = rospy.Publisher('/robot_news_pub', String,queue_size=10)  #topic's name

    rate = rospy.Rate(2) #2hz -> 0.5 sec

    while not rospy.is_shutdown():
        msg = String()
        msg.data ="Hi, this is robot news publisher."
        pub.publish(msg)
        rate.sleep()
        
    rospy.loginfo("Node is stopped.")
```

ros版本： ros noetic

Terminal 1: roscore

Terminal 2运行pub.py: python3 pub.py

Terminal 3 查看node: rosnode list

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ rosnode list
/robot_news_transmitter
/rosout
```

Terminal 4 查看 topic & echo

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ rostopic list
/robot_news_pub
/rosout
/rosout_agg
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ rostopic echo /robot_news_pub
data: "Hi, this is robot news publisher."
---
data: "Hi, this is robot news publisher."
---
data: "Hi, this is robot news publisher."
---
data: "Hi, this is robot news publisher."

```

###### py例子subscriber　

接收上面pub.py的信号 sub.py

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ ls
first_node.py  pub.py  sub.py
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ chmod +x sub.py
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ ls
first_node.py  pub.py  sub.py
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ 
```

```
#!usr/bin/env python3

import rospy
from std_msgs.msg import String

def callback_receive_radio_data(msg):
    rospy.loginfo('Messsage received: ')
    rospy.loginfo(msg)

if __name__=='__main__':
    rospy.init_node('smartphone_subscriber')
    sub =rospy.Subscriber('/robot_news_pub', String, callback_receive_radio_data) #subscribe的topic's name 和publish的一致
    rospy.spin()

```

ros版本： ros noetic

Terminal 1: roscore

Terminal 2运行sub.py: python3 sub.py

Terminal 3 运行pub: rosrun my_tut pub.py

此时Terminal 2：

```shell
INFO] [1615833237.726734]: Messsage received: 
[INFO] [1615833237.730774]: data: "Hi, this is robot news publisher."
[INFO] [1615833238.225839]: Messsage received: 
[INFO] [1615833238.230374]: data: "Hi, this is robot news publisher."
[INFO] [1615833238.725763]: Messsage received: 
[INFO] [1615833238.729962]: data: "Hi, this is robot news publisher."
```

###### C++例子publisher

```shell
ian@jian-ubuntu:~/python_ws/src/my_tut$ ls
CMakeLists.txt  include  package.xml  scripts  src
jian@jian-ubuntu:~/python_ws/src/my_tut$ cd src/
jian@jian-ubuntu:~/python_ws/src/my_tut/src$ ls
first_node.cpp
jian@jian-ubuntu:~/python_ws/src/my_tut/src$ 
jian@jian-ubuntu:~/python_ws/src/my_tut/src$ touch pub_cpp.cpp  //不用excutable
jian@jian-ubuntu:~/python_ws/src/my_tut/src$ ls
first_node.cpp  pub_cpp.cpp
```

pub_cpp.cpp

```cpp
#include <ros/ros.h>
#include <std_msgs/String.h>

int main (int argc, char **argv)
{       
        ros::init(argc, argv, "robot_news_transmitter");
        ros::NodeHandle nh;

        ros::Publisher pub = nh.advertise<msgs::String>("/robot_news_pub", 10);

        ros::Rate rate(3)

        while (ros::ok()){
            std_msgs::String msg;
            msg.data = "Hi, this is cpp robot news publisher.";
            pub.publish(msg);
            rate.sleep();
        }


} 
```

**记得需catkin_make**

Terminal1:进入CMakeLists.txt 增加excutable

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut$ ls
CMakeLists.txt  include  package.xml  scripts  src
jian@jian-ubuntu:~/python_ws/src/my_tut$ vim CMakeLists.txt 
```

```shell
# add_executable(${PROJECT_NAME}_node src/my_tut_node.cpp)

add_executable(node_cpp src/first_node.cpp)

target_link_libraries(node_cpp ${catkin_LIBRARIES})
－－－－－－－－新增部分－－－
add_executable(robot_news_transmitter src/pub_cpp.cpp)

target_link_libraries(robot_news_transmitter ${catkin_LIBRARIES})

```

Terminal2:

```shell
jian@jian-ubuntu:~/python_ws$ catkin_make

...
Scanning dependencies of target robot_news_transmitter
[ 25%] Building CXX object my_tut/CMakeFiles/robot_news_transmitter.dir/src/pub_cpp.cpp.o
[ 75%] Built target node_cpp
[100%] Linking CXX executable /home/jian/python_ws/devel/lib/my_tut/robot_news_transmitter --新生成的部分
[100%] Built target robot_news_transmitter

```

Terminal 3: roscore

Terminal4运行robot_news_transmitter: 

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ rosrun my_tut 
first_node.py           pub.py                  sub.py
node_cpp                robot_news_transmitter  
jian@jian-ubuntu:~/python_ws/src/my_tut/scripts$ rosrun my_tut robot_news_transmitter 

```

Terminal5:

```shell
jian@jian-ubuntu:~/python_ws$ rosnode list
/robot_news_transmitter
/rosout
```

Terminal6:

```shell
jian@jian-ubuntu:~/python_ws$ rostopic list
/robot_news_pub
/rosout
/rosout_agg
jian@jian-ubuntu:~/python_ws$ rostopic echo /robot_news_pub
data: "Hi, this is cpp robot news publisher."
---
data: "Hi, this is cpp robot news publisher."
---
data: "Hi, this is cpp robot news publisher."

```

###### C++例子subscriber　

sub_cpp.cpp

```cpp
#include <ros/ros.h>
#include<std_msgs/String.h>


void callback_receive_news_data(const std_msgs::String& msg)
{
        ROS_INFO("Message received: %s",msg.data.c_str());


}

int main (int argc, char **argv){
        ros::init(argc, argv, "smartphone_subscriber");
        ros::NodeHandle nh;

        ros::Subscriber sub = nh.subscribe("/robot_news_pub",1000, callback_receive_news_data);

        ros::spin();
}    
```

Terminal1:

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut$ vim CMakeLists.txt 
---------------------------

# add_executable(${PROJECT_NAME}_node src/my_tut_node.cpp)

add_executable(node_cpp src/first_node.cpp)

target_link_libraries(node_cpp ${catkin_LIBRARIES})

add_executable(robot_news_transmitter src/pub_cpp.cpp)

target_link_libraries(robot_news_transmitter ${catkin_LIBRARIES})
－－－－－－－－新增部分－－－
add_executable(smartphone_subscriber src/sub_cpp.cpp)

target_link_libraries(smartphone_subscriber ${catkin_LIBRARIES})


```

Terminal2: 

```shell
jian@jian-ubuntu:~/python_ws$ catkin_make


...
Scanning dependencies of target smartphone_subscriber
[ 16%] Building CXX object my_tut/CMakeFiles/smartphone_subscriber.dir/src/sub_cpp.cpp.o
[ 50%] Built target robot_news_transmitter
[ 83%] Built target node_cpp
[100%] Linking CXX executable /home/jian/python_ws/devel/lib/my_tut/smartphone_subscriber --新生成部分
[100%] Built target smartphone_subscriber
```

Terminal 3: roscore

Terminal4 rosnode, rostopic list:

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut$ rosnode list
/robot_news_transmitter
/rosout
/smartphone_subscriber
jian@jian-ubuntu:~/python_ws/src/my_tut$ rostopic list
/robot_news_pub
/rosout
/rosout_agg

```

Terminal 5 rosrun pub_cpp

```shell
jian@jian-ubuntu:~/python_ws$ rosrun my_tut robot_news_transmitter 
```

Terminal 6 rosrun sub_cpp

```shell
jian@jian-ubuntu:~/python_ws/src/my_tut/src$ rosrun my_tut smartphone_subscriber 
[ INFO] [1615840177.637129074]: Message received: Hi, this is cpp robot news publisher.
[ INFO] [1615840177.970222663]: Message received: Hi, this is cpp robot news publisher.
[ INFO] [1615840178.303499780]: Message received: Hi, this is cpp robot news publisher.
[ INFO] [1615840178.636910307]: Message received: Hi, this is cpp robot news publisher.
```

**code 改变要catkin_make**

#### Service 相关操作

###### 查看所以service操作

```
$ rosservice -h
```

###### 查看 service 列表

```
$ rosservice list
```

###### 调用 service

```
$ rosservice call [service] [args]
```

###### 查看 service 格式并显示数据

```
$ rosservice type [service] | rossrv show
```

###### 设置service parameter

```
$ rosparam set [parame_name] [args] + rosservice call clear
```

###### 获得parameter

```
$ rosparam get [parame_name]
```

###### 加载parameter

```
$ rosparam load [file_name] [namespace]
```

###### 删除parameter

```
$ rosparam delete
```

#### Bag 相关操作

###### 录制所有topic变化

```
$ rosbag record -a
```

###### 记录某些topic

```
$ rosbag record -O subset <topic1> <topic2>
```

###### 查看bag信息

```
$ rosbag info <bagfile_name>
```

###### 回放

```
$ rosbag play (-r 2) <bagfile_name>
```











#### refernce

udemy, [book](https://sychaichangkun.gitbooks.io/ros-tutorial-icourse163/content/chapter3/3.1.html)
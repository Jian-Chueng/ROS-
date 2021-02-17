## Linux 命令  俺可以～～😄

- 打开新的command window**： Ctrl + Alt + t

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

  ![image-20200304153255857](image/image-20200304153255857.png)

  

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
>$ rospack find package_name
># 列出本地所有的pkg 
>$ rospack list 
>
># roscd 
># 跳转到某个pkg路径下
>$ roscd package_name
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

#### ![img](image/v2-07a18520cf03a3589e0686eea7564209_1440w.jpg)

#### catkin

目前编译ROS的Package有两种方法：

- catkin_make
- catkin build

**创建workspace**

```shell
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ catkin_make
```

For Python3 最后一个指令:

```shell
$ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

**添加程序包到全局路径**

```shell
$ echo "source catkin_ws/devel/setip.bash">> ~/.bashrc
$ source ~/.bashrc
```

source setup.*sh file:

```shell
$ source devel/setup.bash
```

**查看ros包路径环境变量是否配置好**

```shell
$ echo $ROS_PACKAGE_PATH
```

![image-20200304151651049](image/image-20200304151651049.png)

**catkin_make与catkin build的区别**

与catkin_make不同，catkin命令行工具不仅仅是围绕cmake和make命令的瘦包装器。 catkin build命令隔离地在工作空间的源空间中构建每个包，以防止构建时串扰。 因此，在其最简单的用法中，catkin构建的行为类似于catkin_make_isolated的并行化版本。

#### Package安装方法

##### **Deb二进制包安装方式**

deb方式安装方法十分简单，根据ROS版本，直接运行apt-get命令，例如：

```shell
$ sudo apt-get install ros-kinetic-camera-calibration
```

##### 源码安装方式

源码安装方式稍微复杂，安装方法如下：

1. 创建catkin工作空间
2. 在catkin工作空间的src文件夹下，下载ROS的Package源代码
3. 使用catkin build命令编译安装

#### **大救星Tab键**

不清楚的不打完, 按Tab键 once:会自动补全;twice:list installed packages



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

```shell
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



#### Node 相关

###### 查看所有正在运行的 Node

```shell
$ rosnode list
```

###### 查看某节点信息

```shell
$ rosnode info [node_name]
```

###### 运行 Node

**新终端运行**

```shell
$ rosrun [package_name] [node_name]
```

#### Topic相关

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

###### 图形化显示 topic

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
# ROS 常用命令字典

## 创建ROS workspace

启动ROS

```shell
$ roscore
```



**新窗口**



创建workspace

```shell
jian@jian-ubuntu:~$ mkdir -p ~/catkin_ws/src
jian@jian-ubuntu:~$ cd ~/catkin_ws/
jian@jian-ubuntu:~/catkin_ws$ catkin_make
```

For Python3 最后一个指令:

```shell
$ catkin_make -DPYTHON_EXECUTABLE=/usr/bin/python3
```

**参数说明**：

- -p 确保目录名称存在，不存在的就建一个。

![image-20200304144234515](pic/image-20200304144234515.png)

catkin_ws文件里面有三个文档：buid, devel, src。

source setup.*sh file:

```shell
$ source devel/setup.bash
```

确保ROS_PACKAGE_PATH 在一下dictionary中

```shell
jian@jian-ubuntu:~/catkin_ws$ echo $ROS_PACKAGE_PATH
```

![image-20200304151651049](pic/image-20200304151651049.png)

添加程序包到全局路径

```shell
$ echo "source catkin_ws/devel/setip.bash">> ~/.bashrc
$ source ~/.bashrc
```

## package 相关

创建 Package 并编译

```shell
$ cd ~/catkin_ws/src
$ catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
$ cd ~/catkin_ws
$ catkin_make
```

![image-20200304155639311](pic/image-20200304155639311.png)

查找 Package

```shell
$ rospack find [package name]
```

![image-20200304152916544](pic/image-20200304152916544.png)

change directory roscd

```shell
$ roscd [locationname[/subdir]]
```

![image-20200304153126439](pic/image-20200304153126439.png)

print the working directory 

```shell
$ pwd
```

![image-20200304153255857](pic/image-20200304153255857.png)

列表 rosls

```shell
$ rosls [locationname[/subdir]]
```

![image-20200304153808782](pic/image-20200304153808782.png)

感觉和ls差不多

**大救星Tab键**

不清楚的不打完, 按Tab键 once:会自动补全;twice:list installed packages

## Node 相关

查看所有正在运行的 Node

```shell
$ rosnode list
```

![image-20200304160157539](pic/image-20200304160157539.png)

查看某节点信息

```shell
$ rosnode info [node_name]
```

![image-20200304160311340](pic/image-20200304160311340.png)

运行 Node

**新终端运行**

```shell
$ rosrun [package_name] [node_name]
```

![image-20200304160704599](pic/image-20200304160704599.png)

![：](pic/image-20200304160727590.png)

此时的rosnode list：

![image-20200304160822750](pic/image-20200304160822750.png)

Ping一下

![image-20200304161818042](pic/image-20200304161818042.png)

## Topic相关
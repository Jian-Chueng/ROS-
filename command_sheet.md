# Linux 俺可以

### **打开新的command window**： Ctrl + Alt + t

### **查看Ubuntu版本**

`

```Linux
sudo lsb_release -a
```

`

### **查看ROS版本**

1. 先在终端输入 $roscore
2. 打开新终端，输入 $ rosparam list
3. 继续输入 $ rosparam get /rosdistro

咱的版本： kinetic 1.12.14

### catkin方式创建ROS工作空间**

ROS Fuerte及早期版本请选择rosbuild

`

```Linux
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/src
```

`

即使这个工作空间是空的（在'src'目录中没有任何软件包，只有一个`CMakeLists.txt`链接文件），你依然可以编译它

`

```Linux
$ cd ~/catkin_ws/
$ catkin_make
```

`

catkin_make命令在catkin 工作空间中是一个非常方便的工具。如果你查看一下当前目录应该能看到'build'和'devel'这两个文件夹。在'devel'文件夹里面你可以看到几个setup.*sh文件。`source`这些文件中的任何一个都可以将当前工作空间设置在ROS工作环境的最顶层，想了解更多请参考catkin文档。接下来首先`source`一下新生成的setup.*sh文件：
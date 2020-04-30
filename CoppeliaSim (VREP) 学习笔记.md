# CoppeliaSim (VREP) 学习笔记

## 连接python方法



1. #### Tools

   在anaconda中创建专门用于coppeliasim使用的environment：coppeliasim。

   安装

   scipy,numpy,matplotlib and other major libraries，

   IDE：Spyder or others

   python 3.7 version

2. #### files setup

   创建working folder (directory)： /Users/Jian/Documents/GitHub/M_robot/VREP/pysim

   有以下三个文件：

   - sim.py
   - simConst.py
   - remoteApi.dll（win), remoteApi.dylib(mac) or remoteApi.so (linux)

3. #### Setting up a Server

   1. 打开bubbleRob scene 

   2. Click on any of the cylinders you used as obstacles 

   3. Click on Add→Associated Child ScriptrightarrowThreaded Script 

   4. 在这个script的sysCall_threadmain() 下添加

      ```lua
      simExtRemoteApiStart(19999) 
      ```

      Now, as soon as the scene is played, a server will be listening on port 19999. 

   5. 单击左侧script选中 bubbleRob, click on “Disable” . Close the scripts window, you will see an “x” next to the script for bubbleRob
   6. start scene:  it will start the server

4. #### Setting up the Client

   1. 打开IDE：新建bubbleRob_control.py

      ```python
      import sim                  # access all the sim elements
      import sys
      import time                #used to keep track of time
      import numpy as np         #array library
      import math
      
      # Pre-Allocation
      sim.simxFinish(-1) # just in case, close all opened connections
      clientID=sim.simxStart('127.0.0.1',19999,True,True,5000,5)
      # start a connection
      if clientID!=-1:
          print ("Connected to remote API server")
      else:
          print("Not connected to remote API server")
          sys.exit("Could not connect")
      ```

   2. run bubbleRob_control.py

   可以看到console显示成功连接：“Connected to remote API server”

5. #### Controling the Robot

   

6. 

Reference：http://fid.cl/courses/ai-robotics/vrep-tut/pythonBubbleRob.pdf
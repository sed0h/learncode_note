# learncode_note
1.ros2_SetEnvironment
PowerShell:
setx OPENSSL_CONF "D:\Program Files\OpenSSL-Win64\bin\openssl.cfg" -m
Command Prompt:
setx -m OPENSSL_CONF D:\Program Files\OpenSSL-Win64\bin\openssl.cfg

Setup Environment 
  Start a command shell and source the ROS2 setup file to set up the workspace:
  > call C:\dev\ros2_foxy\local_setup.bat
Try example
  > call C:\dev\ros2_foxy\local_setup.bat
  > run demo_nodes_cpp talker
  Start another command shell:
  > call C:\dev\ros2_foxy\local_setup.bat
  > run demo_nodes_py listener

Installation troubleshooting:
   1.Failed to load Fast RTPS shared library
   --安装vcredist_x64.exe
   
Check environment variables
	CMD运行：
	> call D:\1work\ROS2_soa\ros2-windows\local_setup.bat
	> set | findstr -i ROS
	Check that variables like ROS_DISTRO and ROS_VERSION are set. For example:
	ROS_DISTRO=foxy
	ROS_LOCALHOST_ONLY=0
	ROS_PYTHON_VERSION=3
	ROS_VERSION=2

Add sourcing to your shell startup script
	Only for PowerShell users, create a folder in ‘My Documents’ called ‘WindowsPowerShell’. Within ‘WindowsPowerShell’, create file ‘Microsoft.PowerShell_profile.ps1’. Inside the file, paste:

	D:\1work\ROS2_soa\ros2-windows\local_setup.ps1
	PowerShell will request permission to run this script everytime a new shell is opened.
	
	未对文件Microsoft.PowerShell_profile.ps1 进行数字签名:
	set-ExecutionPolicy RemoteSigned


1.交换 a, b
  a = a^b^a
  b = a^b^b

2.cmake
1)
add_executable(<name> [WIN32] [MACOSX_BUNDLE]
		   [EXCLUDE_FROM_ALL]
		   source1 [source2 ...])
name: project name

example:
add_executable(test_swap swap_a_b.cpp swap/swap.cpp)
	
2)
include_directories([AFTER|BEFORE] [SYSTEM] dir1 [dir2 ...])
它相当于g++选项中的-I参数的作用，也相当于环境变量中增加路径到CPLUS_INCLUDE_PATH变量的作用。
example:
include_directories(swap/)

3)
link_directories(directory1 directory2 ...)
它相当于g++命令的-L选项的作用，也相当于环境变量中增加LD_LIBRARY_PATH的路径的作用。
	
1.$ find <指定目录> <指定条件> <指定动作>
find的使用实例：

　　$ find . -name "my*"

搜索当前目录（含子目录，以下同）中，所有文件名以my开头的文件。

　　$ find . -name "my*" -ls

搜索当前目录中，所有文件名以my开头的文件，并显示它们的详细信息。

　　$ find . -type f -mmin -10

搜索当前目录中，所有过去10分钟中更新过的普通文件。如果不加-type f参数，则搜索普通文件+特殊文件+目录。
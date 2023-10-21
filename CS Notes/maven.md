1. #### maven怎么排除依赖冲突

   `mvn -Dverbose dependency:tree`

2. #### maven常见指令

   1. mvn clean 清空产生的[项目]()( target里)

   2. mvn compile 编译源代码

   3. mvn test 运行测试
   4. mvn install 在本地repository中安装jar（包含mvn compile，mvn package，然后上传到本地仓库
   5. mvn deploy 上传到(包含mvn install,然后，上传到)
   6. mvn package 打包
   7. mvn site 产生site
   8. mvn test-compile 编译测试代码
   9. mvn -Dtest package 只打包不测试
   10. mvn jar:jar 只打jar包

   11. mvn test -skipping compile -skipping test-compile 只测试而不编译，也不测试编译

   12. mvn deploy 

   13. mvn source.jar [源码]()**打包**

   

3. #### package和install有什么区别

4. git



## Linux系统

1. CPU过高

   1. top：查找出哪个进程消耗的CPU高，

   2. top -Hp “进程号” ：找到CPU消耗最多的线程

   3. printf "%x\n" “线程号” ：转化为16进制格式

   4. 找线程用jstack分析，`jstack 进程号 | grep 16进制线程号 -A 10`

      非java指令用：`perf top -p 7574`

2. 绝对路径用什么符号表示？当前目录、上层目录用什么表示？主目录用什么表示? 切换目录用什么命令？

   绝对路径： 如/etc/init.d 

   当前目录: ./ 上层目录： ../  主目录： ~/ 

   切换目录： cd 

3. 查看当前进程，退出，查看当前路径

   查看当前进程： ps 

   执行退出： exit 

   查看当前路径： pwd 查看绝对路径 pwd -P

4. 如何清屏？退出当前命令？睡眠？

   清屏：clear 

   退出当前命令：ctrl + c彻底退出

   执行命令：ctrl +z 挂起当前进程

   fg:恢复后台

   查看当前用户id："id"查看uid gid所属分组及用户名

   查看指定帮助：man adduser

5. 常用工具

   1. 系统命令工具

   包括：进程间通信设施状态 ipcs、Linux系统运行时长 uptime、CPU平均负载和磁盘活动 iostat、监控，收集和汇报系统活动 sar、监控多处理器使用情况 mpstat、监控进程的内存使用情况 pmap、系统管理员调优和基准测量工具 nmon、密切关注Linux系统 glances、查看系统调用 strace

   2. 基础命令工具

   包括：系统进程状态 ps、虚拟内存统计工具 vmstat、控制台的流量监控工具 vnstat、 进程监控工具 atop，htop、内存使用状态 free

   3. 网络参数工具

   包括：Linux网络统计监控工具 netstat、显示和修改网络接口控制器 ethtool、网络数据包分析利刃 tcpdump、远程登陆服务的标准协议 telnet、获取实时网络统计信息 iptraf、显示主机上网络接口带宽使用情况 iftop

   4. 磁盘参数工具

   包括：磁盘卸载 umount、读取、转换并输出数据 dd、文件系统系统 df、磁盘挂载 mount

   5. 日志监控工具

   包括：实时网络日志分析器 GoAccess、多窗口之下日志监控 MultiTail、日志分析系统 LogWatch/Swatch

   6. 参数监控工具

   包括：监控apache网络服务器整体性能 apachetop、ftp 服务器基本信息 ftptop、IO监控 iotop、电量消耗和电源管理 powertop、监控 mysql 的线程和性能 mytop、系统运行参数分析 htop/top/atop

6. 

7. 

8. 

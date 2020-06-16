# Linux指令

## 基础指令

### ls 列出指定路径下的文件夹，文件

ls -l

ls -a

ls -h

ls -lah



### pwd 查看当前路径



### cd 进入指定路径

./ 当前目录

../ 当前目录的上一级目录

/ 根目录

~ 当前用户的home目录



### mkdir 创建目录

mkdir folderName

mkdir -p foldername/foldername/foldername

mkdir foldername foldername foldername



### touch 创建新文件

touch test.log

touch foldername/test.log

touch foldername/1.log foldername/2.log



### cp 拷贝文件夹，文件夹

cp -r foldername flodername/flodername/

cp -r foldername foldername/foldername/newfoldername

cp filename foldername/filename

cp filename folder/



### mv 移动文件，文件夹到指定路径

mv filename foldername

mv filename newfilename (F2 重命名)

mv foldername foldername/foldername



### rm 移除（删除）文件，文件夹

rm -r foldername

rm filename

rm filename filename



### vim 使用vim编辑器打开指定的文件

vim filename



### 输出重定向 >, >>

1.>

ps: ls -lh > filename 执行命令 ls -lh 输出的内容放进filename文件中，如果filename有内容，则会全部覆盖

2.>>

ps: ls -lh > filename 执行命令 ls -lh 输出的内容放进filename文件中，如果filename有内容，则会在后面添加，不会删除原来的内容



### cat 查看某个文件，或者合并多个文件到指定的文件中

cat filename

cat filename01 filename02 filename 03 > filename



## 进阶命令



### df 查看当前硬盘使用情况

df -h(较高的可读性)



### free 查看内容使用情况

free -m 以MB单位查看当前内容使用情况



### head 查看一个文本文件前多少行的内容

head -5 filename.txt  查看前五行



### tail查看一个文本文件后多少行的内容

tail -5 filename.txt  查看后五行

tail -f filename.txt 实时查看这个文件内容动态变化，一般是一些日志的文件（被动改动文件的情况， 主动使用编辑器改写是不会起作用的）



### less查看文件，以较少的内容进行输出查看文件，以较少的内容进行输出(方向键上下，自动加载)

less filename.txt （：q 回车退出）



### wc 查看文件内容信息

wc -l filename.txt  行号

wc -w filename.txt 单词数 （依照空格数来判断单词数量）

wc -c filename.txt 字节数



### date 操作时间

date 

date “+%F” 2020-06-01（date "+%Y%m%d"）

date "+%F $T"  2020-06-01 13:00:00（date "+%Y-%m-%d %H:%M:%S"）

date -d "- 1 day" 昨天时间

date -d "- 1 month" 上个月的时间



### cal 日历

cal 

cal -3 上个月 本月 下个月

cal -y 2020 某年的年份



### clear / crt + l 清屏



### | 管道

过滤：ls path | grep y 筛选出当前路径下带有y的文件夹

cat filename.txt | less 等价于less filename.txt

ls / | wc -l 查看根目录有多少个文件



## 高级指令



### hostname 获取主机名称

hostname 

hostname -f



### id 查看当前用户基本信息

id 当前用户

id 用户名 指定用户



### whoami 当前登录用户名

whoami



### ps -ef 查看当前进程

ps -ef 



### top 查看进程占用资源

top

按键 M 按照内存使用从高到低

按键 P 按照cpu使用率从高到低

按键 1 切换显示各个cpu详细信息

按键q 退出



### du -sh 查看某个文件夹真实存储大小

du -sh



### find 查找文件、文件夹

find path -name y 按名字（y）查找（通配符*）

find path -type 按照类型查找 （d 文件夹， f 文件）



### service 服务操作

service 服务名 start 开启服务

service 服务名 stop 停止服务

service 服务名 restart 重启服务



### kill 杀掉进程

kill 进程id

killall 进程名称



### ifconfig 查看网卡相关信息

ifconfig



### reboot 重启计算机

reboot



### shutdown 关闭计算机

shutdown

shutdown -h now 立马关机

shutdown -c 取消关机指令

poweroff



### uptime 计算机开启持续时间

uptime



### uname 获取计算机操作系统信息

uname

uname -a 获取全部信息



### netstat -tnlp 查看网络连接状态

netstat -tnlp



### man 查看手册

man 指令名称
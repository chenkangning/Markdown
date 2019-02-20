[TOC]
# Linux基础笔记
## Linux中的通配符
符号 | 作用
----| ----
 *  | 匹配任意内容
 ？ | 匹配任意一个字符
 [] | 匹配任意一个中括电内的字符

 ***

## 常用目录的作用  
目录  |  作用
---- | ----
/    | 根目录
/bin | 命令保存目录（普通用户就可以读取的命令）
/boot| 启动目录，放置启动相关文件
/dev | 设备文件保存目录
/etc | 配置文件保存目录
/home| 普通用户的家目录
/lib | 系统库保存目录
/mnt | 系统挂载目录
/media| 挂载目录
/root| 管理员目录
/tmp | 临时目录
/sbin| 命令保存目录（管理员才能使用的命令）
/proc| 直接写入内存
/sys |
/usr | 系统软件资源目录
/var | 系统相关文档内容

***

## 常用命令
命令                  | 作用 
---                  | ---
ls [选项] [文件或目录] | 査询目录中的内容 + -a 显示所有文件，包括隐藏文件。-l/-lh 显示详细信息/显示易懂信息。-d 査看目录属性。-h 人性化显示文件大小。-i 显示inode。
mkdir [选项] [目录名] | 建立目录 + -p 递归创建
cd [目录]            | 切换所在目录 + ～ 进入当前用户的家目录。- 进入上次目录。 .. 进入上级目录。. 进入当前目录。
rm [选项] [文件或目录] | 删除文件或目录 + -rf 强制删除文件或目录
cp [选项] [原文件或目录] [目标目录]| 复制命令 + -a 复制目录所有属性
mv [原文件或目录] [目标目录] | 剪切或改名命令（原文件如果不在目标目录下就是剪切，如果在目标目录下就是改名）
ln [选项] [原文件] [目标文件]| 链接命令 + -s 生成软链接（原文件要写绝对路径）。------**软链接特性：** 1.类似Windows快捷方式。2.软链接拥有自已的I节点和Block块，但是数据块中只保存原文件的文件名和I节点号，并没有实际的文件数据。3.lrwxrwxrwx l：软链接，软链接文件权限都为rwx。4.俢改任意文件，另一个都改变。5.删除原文件，软链接就不能再使用。------ **硬链接特性：** 1.拥有相同的i节点种存储block块，可以看做是同一个文件。2.可通过i节点识别。3.不能跨分区。4.不能针对目录使用。

***

## linux搜索命令
搜索命令               |                作用 
--------------------  |  -----------------
文件搜索命令 locate [文件名]    | 在后台数据库中按文件名搜索，搜索速度更快。（locate数据库是按毎天更新的，如査找的文件是新创建不久，査找不到需要使用 **updatedb** 命令更新数据库）
搜索命令的命令 whereis [选项] [命令名] | 搜索命令所在路径及帮助文档所在位置。+ -b：只査找可执行文件。 -m：只査找帮助文件。
搜索命令的命令 which [文件名]         | 搜索命令所在路径及别名 
文件搜索命令 find [搜索范围] [搜索文件] [搜索条件]  | find是系统当中搜索符合条件的文件名。避免大范围搜索，会耗费系统资源。**搜索条件介绍：**                                __*-size*__：（k小写/M大写）按条件大小査找，                                ```find /root -size -25k```:小于25kb的文件。                                   ```find /root -size 25k```：等于25kb的文件。                                   ```find /root -size +25k```：大于25kb的文件。                                  __*-a/-o*__:逻辑运算 _**与/或**__ ，```find /root -size -20k -a -size +25k```:査找/root目录下小于20kb与大于25kb的文件。                                        __*-atime*__:文件访问时间```find /root -atime +10```：査找10天前访问的文件。     __*-ctime*__:改变文件属性```find /root -ctime 10```:査找10天当天改变文件属性的文件。__*mtime*__:修改文件内容```find /root -mtime -10```:査找10内修改文件内容的文件。__*-exec 命令 {} \\;*__:对搜索结果执行操作，                                     ```find /root -size +20k -a -size -25k -exec ls -lh {} \;```:搜索/root目录下大于20k与小于25k的文件，执行ls -lh命令                                             __*name*__:文件名```find /toot```
搜索字符串命令 grep [选项] 字符串 文件名 | grep是在文件当中匹配符合条件的字符串。+ -i：忽略大小写 -v：排除指定字符串.```grep 'ln' /home/chenkangning/Markdown/linunx/linunx_date.md```

find命令 | grep命令的区别 
---|---
find命令 | grep命令
在系统当中搜索符合条件的文件名，如果需要匹配，使用通配符匹配，通配符是完全匹配。 | 在文件当中搜索符合条件的字符串，如果需要匹配，使用正则表达式进行匹，正则表达式时包含匹配

***

## 帮助命令     
**帮助命令man**     
* man 命令    
    * 获取指定命令的帮助     
     
* man ls
    * 査看ls的帮助
```linux
man -f ls 
#man文档等级
```
```
man -k ls
#包函ls的所有帮助文档
```   
**选项帮助 --help**  
* 命令 --help  
    * 获取命令选项的帮助   

例如：  
ls --help  

**shell内部命令帮助**
* help shell内部命令
    * 获取shell内部命令的帮助

例如：
* whereis cd
    * 确定是否是shell内部命令
* help cd
    * 获取内部命令帮助

## 压缩与解压缩命令   
* 常用压缩格式：  .zip  .gz   .bz2   
* 常用压缩格式：  .tar.gz   .tar.bz2   

.zip格式压缩   
* zip 压缩文件名 源文件  
    #压缩文件
* zip -r 压缩文件名 源目录  
    #压缩目录 
.zip格式解压缩  
* unzip 压缩文件   
    #解压缩.zip文件   

.gz格式压缩 
* gzip 源文件  
    #压缩为.gz格式的压缩文件，源文件会消失  
* gzip -c 源文件 > 压缩文件    
    #压缩为.gz格式，源文件保留    
例如：```gzip -c cangls > cangls.gz```   
* gzip -r 目录  
    #压缩目录下所有的子文件，但是不能压缩目录   

.gz格式解压缩  
* gzip -d 压缩文件  
    #解压缩文件    
* gunzip 压缩文件    
    #解压缩文件

.bz2格式压缩
* bzip2 源文件   
    #压缩为.bz2格，不保留源文件    
* bzip2 -k 源文件  
    #压缩后保留源文件
==注意：bzip2命令不能压缩目录==    

.bz2格式解压缩    
* bzip2 -d 压缩文件   
    #解压缩，-k保留压缩文件   
* bunzip2 压缩文件   
    #解压缩，-k保留压缩文件  

.tar.gz压缩格式   
==其实.tar.gz是先打包为.tar格式，再压缩为.gz格式==    
* tar -zcvf 压缩包名.tar.gz 源文件
* 选项：
    * -z: 压缩为.tzr.gz格式

* tar -zxvf 压缩包名.tar.gz
* 选项：
    * -x：解压缩.tar.gz格式

* tar -ztvf 压缩包名.tar.gz
* 选项：
    * -t：不解压査看压缩包内容

可指定压缩包放置路径与多文件压缩，如下:
```tar -zcvf /tmp/taest.tar.gz jp anaconda-ks.cfg```

.tzr.bz2压缩格式
* tar -jcvf 压缩包名.tar.bz2 源文件  
* 选项：
    * -z：压缩为.tar.bz2格式

* tar -jxvf 压缩包名.tar.bz2
* 选项： 
    * -X：解压缩包.tar.bz2格式

* tar -jtvf 压缩包名.tar.bz2
* 选项：
    * -t：不解压査看压缩包内容 

## shutdown命令   
[root@localhost ~ ]#shutdown [选项] 时间
选项：
-c：取消前一个关机命令
-h：关机
-r：重启
 &：在命令最后加上&，可以继续在命令行操作

* 其他关机命令
[root@localhost ~ ]# halt
[root@localhost ~ ]#poweroff
[root@localhost ~ ]#init0

* 其他重启命令
[root@localhost ~ ]# reboot
[root@localhost ~ ]# init6
    * 系统运行级别
        * 0：关机
        * 1：单用户
        * 2：不完全多用户，不含NFS服务
        * 3：完全多用户
        * 4：末分配
        * 5：图形界面
        * 6：重启
    * [root@localhost ~ ]# cat /etc/inittab
    #修改系统默认运行级别
    id:3:initdefault:

    * [root@localhost ~ ]# runlevel
    #査询系统运行级别

* 退出登陆命令
[root@localhost ~ ]#logout

## 其他命令
* 挂载命令
    * 用户登录査看和用户交互命令
    * [root@localhoust ~ ]# mount
        * #査询系统中已经挂载的设备
    * [root@localhost ~]# mount -a
        * #依据配置文件/etc/fstab的内容自动挂载

* 挂载命令格式
    * [root@localhost ~]# mount [-t 文件系统] [-o 特殊选项] 设备文件名 挂载点
        * 选项：
            * -t 文件系统：加入文件系统类型来指定挂载的类型，可以ext3、ext4、iso9660（就是挂载光盘）等文件系统
            * -o 特殊选项：可以指定挂载的额外选项 选项参数如列表
            
参数 | 说明
--- | ---
atime/noatime | 更新访问时间/不更新访问时间。访问分区文件时，是否更新文件的访问时间，US做默认为更新
async/sync | 异步/同步，默认异步
auto/noauto | 自动/手动，mount -a命令执行时，是否会自动安装/etc/fstab文件内容挂载，默认为自动
defaults | 定义默认值，相当于rw，suid，dev，exe，auto，nouser，async这七个选项
exec/noexec | 执行/不执行，设定是否允许在文件系统中执行可执行文件，默认是exec允许
remount | 重新挂载已经挂载的文件系统，一般用于修改指定特殊权限
rw/ro | 读写/只读，文件系统挂载时，是否具有读写权限，默认是rw
suid/nisuid | 具有/不具百SUID权限，设定文件系统是否具有SUID和SGID的权限，默认是具有
user/nouesr | 允许/不允许普通用户挂载，设定文件系统是否允许普通用户挂载，默认不允许
usrquota | 㝍入代表文件系统支持用户磁盘配额，默认不支持
grpquota | 写入代表文件系统支持组磁盘配额，默认不支持

* 挂载光盘
    * [root@localost ~]#mkdir /mnt/cdrom/
        * #建立挂载点
    * [root@localost ~]#mount -t iso9660 /dev/cdrom  /mnt/cdrom/
        * #挂载光盘
    * [root@localost ~]#mount /dev/sr0  /mnt/cdrom

* 卸载命令
    * [root@localost ~]#umount 设备文件名或挂载点
        * [root@localost ~]#umount /mnt/cdrom/


* 挂载U盘
    * [root@localost ~]#fdisk -l
        * #査看U盘设备文件名
    * [root@localost ~]#mount -t vfat /dev/sdb1/mnt/usb/
    * 注意：Linux默认是不支持NTFS文件系统的

* 査看登录用户信息
    * w 用户名
    命令输出：
        * USER：登陆的用户名；
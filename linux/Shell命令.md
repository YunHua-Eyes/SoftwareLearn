[toc]

# <font color='006600'>文件管理</font>

## <font color='#0000dd'>cat 命令</font>

**文件：/var/log/cron-2023060**

```shell
cat /var/log/cron-2023060
```
```shell
Jun  8 16:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[126323]: (root) CMD (run-parts /etc/cron.hourly)
Jun  8 16:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[126323]: (/etc/cron.hourly) starting 0anacron
Jun  8 16:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[126323]: (/etc/cron.hourly) finished 0anacron
Jun  8 17:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[127075]: (root) CMD (run-parts /etc/cron.hourly)
Jun  8 17:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[127075]: (/etc/cron.hourly) starting 0anacron
Jun  8 17:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[127075]: (/etc/cron.hourly) finished 0anacron
Jun  8 18:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[127358]: (root) CMD (run-parts /etc/cron.hourly)
Jun  8 18:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[127358]: (/etc/cron.hourly) starting 0anacron
Jun  8 18:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[127358]: (/etc/cron.hourly) finished 0anacron
```

由 1 开始对所有输出的行数编号
```shell
cat -n /var/log/cron-2023060
```
```shell
605  Jun  4 02:34:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103074]: (root) CMD (/usr/bin/systemctl --quiet restart update-motd)
606  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103181]: (root) CMD (run-parts /etc/cron.hourly)
607  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.hourly) starting 0anacron
608  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Anacron started on 2023-06-04
609  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job `cron.daily' in 30 min.
610  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job `cron.weekly' in 50 min.
611  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Jobs will be executed sequentially
612  Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.hourly) finished 0anacron
```

把 textfile1 的文档内容加上行号后输入 textfile2 这个文档里
```shell
cat /var/log/cron-20230604 > /root/cron-temp
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
-rw-r--r-- 1 root root 57274 Jun  8 19:14 cron-temp
-rwxr-xr-x 1 root root     0 Jun  8 16:11 log.txt
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# cat cron-temp
```
```shell
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[102975]: Anacron started on 2023-06-04
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[102975]: Normal exit (0 jobs run)
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[102966]: (/etc/cron.hourly) finished 0anacron
Jun  4 02:34:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103074]: (root) CMD (/usr/bin/systemctl --quiet restart update-motd)
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103181]: (root) CMD (run-parts /etc/cron.hourly)
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.hourly) starting 0anacron
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Anacron started on 2023-06-04
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job `cron.daily' in 30 min.
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job `cron.weekly' in 50 min.
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Jobs will be executed sequentially
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.hourly) finished 0anacron
```

## <font color='#0000dd'>chmod 命令</font>

| 权限 | rwx | 二进制 |
| :----- | ----: | :---: |
| 4 | 只读 | r-- 100 |
| 2 | 只写 |-w-	010 |
| 1 | 只执行 | --x 001 |

```shell
chmod 421 cron-temp
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
-r---w---x 1 root root 57274 Jun  8 19:14 cron-temp
```

```shell
chmod 763 cron-temp
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron-temp
```

## <font color='#0000dd'>chown 命令</font>

将文件的拥有者设为 root，群体的使用者 root 

```shell
chown root:root cron-temp
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron-temp
```

```shell
chown -R root:root *
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron-temp
```

## <font color='#0000dd'>cmp 命令</font>

比较 prog.o.bak 和 prog.o。如果文件相同，则不显示消息。
```shell
cmp cron-temp /var/log/cron-20230604
```

如果文件不同，则显示第一个不同的位置
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# cmp cron-temp /var/log/cron-20230528 
cron-temp /var/log/cron-20230528 differ: byte 1, line 1
```

## <font color='#0000dd'>diff 命令</font>

-H 或 --speed-large-files 　比较大文件时，可加快速度。

-y 或 --side-by-side 　以并列的方式显示文件的异同之处。
-W<宽度> 或 --width<宽度> 　在使用-y参数时，指定栏宽。

```shell
diff cron-temp /var/log/cron-20230528 -H -y -W 150
```
```shell
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[102966]: (/etc/cron.    |     May 28 02:34:01 iZbp10iy3yejxoxq8qhlpiZ CROND[70131]: (root) CMD (/usr
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[102975]: Anacron start    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[70248]: (root) CMD (run-
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[102975]: Normal exit (    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[70248]: (/etc/cron.h
Jun  4 02:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[102966]: (/etc/cron.    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[70257]: Anacron starte
Jun  4 02:34:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103074]: (root) CMD (/us    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[70257]: Will run job `
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ CROND[103181]: (root) CMD (run    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[70257]: Will run job `
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[70257]: Jobs will be e
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Anacron start    |     May 28 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[70248]: (/etc/cron.h
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job     <
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Will run job     <
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ anacron[103190]: Jobs will be     <
Jun  4 03:01:01 iZbp10iy3yejxoxq8qhlpiZ run-parts[103181]: (/etc/cron.    <
```

## <font color='#0000dd'>file 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# file cron-temp
cron-temp: ASCII text
```

多个文件
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# file cron-temp /var/log/cron
cron-temp:     ASCII text
/var/log/cron: ASCII text
```

-c 详细显示指令执行过程，便于排错或分析程序执行的情形
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# file -c cron-temp
cont    offset  type    opcode  mask    value   desc
```

## <font color='#0000dd'>find 命令</font>
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# find . -name cron-temp
./cron-temp
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# find /var/log/ -name "cron*"
/var/log/cron-20230604
/var/log/cron-20230528
/var/log/cron
```

查找 /home 目录下大于 1MB 的文件
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# find /var/log/ -size +1M
/var/log/journal/b6ab5170290e430b872c890ce386d1eb/system.journal
/var/log/journal/b6ab5170290e430b872c890ce386d1eb/system@00000000000000000000000000000000-0000000000000f21-0005f4a386cdfa09.journal
[root@iZbp10iy3yejxoxq8qhlpiZ ~]#
```

查找 /var/log 目录下在 7 天前修改过的文件：
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# find /var/log/ -mtime 7
/var/log/sa/sar31
/var/log/sa/sa31
```

将当前目录及其子目录下所有最近 7 天前更新过的文件列出，不多不少正好 7 天前的:
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# find /var/log/ -ctime 7
/var/log/sa/sar31
/var/log/sa/sa31
/var/log/btmp-20230601
```

将当前目录及其子目录下所有 7 天前 及更早更新过的文件列出
```shell
find /var/log/ -ctime +7
```

## <font color='#0000dd'>ln 命令</font>

-s 软链接(符号链接)

```shell
ln -s /var/log/cron-20230528 cron-20230528
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 56
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron-temp
```

硬链接

```shell
ln /var/log/cron-20230528 cron-20230528.txt
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 116
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root 56797 May 28 03:01 cron-20230528.txt
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron-temp
```

## <font color='#0000dd'>less 命令</font>

空格键 滚动一页
回车键 滚动一行
[pagedown]： 向下翻动一页
[pageup]： 向上翻动一页

```shell
less cron-temp
```
```shell
ps -ef |less
```
```shell
history | less
```

## <font color='#0000dd'>more 命令</font>

Enter 向下n行，需要定义。默认为1行
Ctrl+F 向下滚动一屏
空格键 向下滚动一屏
Ctrl+B 返回上一屏
= 输出当前行的行号

```shell
more cron-temp
```

## <font color='#0000dd'>mv 命令</font>

```shell
mv cron-temp cron_temp
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 116
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root 56797 May 28 03:01 cron-20230528.txt
-rwxrw--wx 1 root root 57274 Jun  8 19:14 cron_temp
```

## <font color='#0000dd'>rm 命令</font>

```shell
rm  -rf   test.txt
```

## <font color='#0000dd'>touch 命令</font>

修改文件或者目录的时间属性，包括存取时间和更改时间。

```shell
touch cron_temp
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 116
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root 56797 May 28 03:01 cron-20230528.txt
-rwxrw--wx 1 root root 57274 Jun  9 10:39 cron_temp
```

```shell
touch cron-20230528.txt
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 116
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root 56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root 57274 Jun  9 10:39 cron_temp
```

如果指定的文件不存在，则将创建一个新的空白文件。

```shell
touch text.txt
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 116
lrwxrwxrwx 1 root root    22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root 56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root 57274 Jun  9 10:39 cron_temp
-rw-r--r-- 1 root root     0 Jun  9 10:41 text.txt
```

## <font color='#0000dd'>which 命令</font>

查找文件

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# which cron_temp
/usr/bin/which: no cron_temp in (/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin)
```

查看指令的绝对路径

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# which bash
/usr/bin/bash
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# which docker
/usr/bin/docker
```

## <font color='#0000dd'>cp 命令</font>

```shell
cp /var/log/dnf.librepo.log dnf.librepo.log
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 444
lrwxrwxrwx 1 root root     22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root  56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root  57274 Jun  9 10:39 cron_temp
-rw-r--r-- 1 root root 333511 Jun  9 10:46 dnf.librepo.log
-rw-r--r-- 1 root root      0 Jun  9 10:41 text.txt
```

-r：若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件。

```shell
cp -r /var/log log
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 448
lrwxrwxrwx 1 root root     22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root  56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root  57274 Jun  9 10:39 cron_temp
-rw-r--r-- 1 root root 333511 Jun  9 10:46 dnf.librepo.log
drwxr-xr-x 9 root root   4096 Jun  9 10:46 log
-rw-r--r-- 1 root root      0 Jun  9 10:41 text.txt
```

## <font color='#0000dd'>whereis 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# whereis bash
bash: /usr/bin/bash /usr/share/man/man1/bash.1.gz /usr/share/info/bash.info.gz
```

## <font color='#0000dd'>awk 命令</font>

···


# <font color='006600'>磁盘管理</font>

## <font color='#0000dd'>cd 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# cd /var/log/
[root@iZbp10iy3yejxoxq8qhlpiZ log]# 
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ log]# cd -
/root
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# cd ..
[root@iZbp10iy3yejxoxq8qhlpiZ /]# 
```

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ /]# cd root/
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# 
```

## <font color='#0000dd'>df 命令</font>

-h 选项，通过它可以产生可读的格式df命令的输出：

```shell
df -h
```
```shell
Filesystem      Size  Used Avail Use% Mounted on
devtmpfs        966M     0  966M   0% /dev
tmpfs           984M     0  984M   0% /dev/shm
tmpfs           984M  584K  984M   1% /run
tmpfs           984M     0  984M   0% /sys/fs/cgroup
/dev/vda2        40G  5.1G   33G  14% /
/dev/vda1       200M  5.8M  195M   3% /boot/efi
overlay          40G  5.1G   33G  14% /var/lib/docker/overlay2/8d2796648cb6bd0971e1326f4e430556ba2033f8da86f56971bebcbcce59481e/merged
overlay          40G  5.1G   33G  14% /var/lib/docker/overlay2/a40ec70f5462861634027862f04a9e55d8ee636188ab4ba92dda6ac0d33d947f/merged
tmpfs           197M     0  197M   0% /run/user/0
```

## <font color='#0000dd'>du 命令</font>

```shell
du /root
```
```shell
4       /root/.ssh
11392   /root/log/sa
8       /root/log/tuned
4       /root/log/chrony
4       /root/log/private
4       /root/log/anaconda
28      /root/log/audit
40964   /root/log/journal/b6ab5170290e430b872c890ce386d1eb
40968   /root/log/journal
56404   /root/log
4       /root/.config/procps
8       /root/.config
8       /root/.pip
56916   /root
```

```shell
du -h /root
```
```shell
4.0K    /root/.ssh
12M     /root/log/sa
8.0K    /root/log/tuned
4.0K    /root/log/chrony
4.0K    /root/log/private
4.0K    /root/log/anaconda
28K     /root/log/audit
41M     /root/log/journal/b6ab5170290e430b872c890ce386d1eb
41M     /root/log/journal
56M     /root/log
4.0K    /root/.config/procps
8.0K    /root/.config
8.0K    /root/.pip
56M     /root
```


## <font color='#0000dd'>mkdir 命令</font>

```shell
mkdir runtest
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll
total 452
lrwxrwxrwx 1 root root     22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root  56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root  57274 Jun  9 10:39 cron_temp
-rw-r--r-- 1 root root 333511 Jun  9 10:46 dnf.librepo.log
drwxr-xr-x 9 root root   4096 Jun  9 10:46 log
drwxr-xr-x 2 root root   4096 Jun  9 12:08 runtest
-rw-r--r-- 1 root root      0 Jun  9 10:41 text.txt
```

-p 确保目录名称存在，不存在的就建一个（注：本例若不加 -p 参数，且原本目录不存在，则产生错误。）

```shell
mkdir runtest2/test
```
```shell
mkdir: cannot create directory ‘runtest2/test’: No such file or directory
```

```shell
mkdir -p runtest2/test
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ll runtest2/
total 4
drwxr-xr-x 2 root root 4096 Jun  9 12:09 test
```

## <font color='#0000dd'>pwd 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# pwd
/root
```

## <font color='#0000dd'>stat 命令</font>

```shell
stat cron_temp
```
```shell
  File: cron_temp
  Size: 57274           Blocks: 112        IO Block: 4096   regular file
Device: fd02h/64770d    Inode: 392462      Links: 1
Access: (0763/-rwxrw--wx)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-06-09 10:55:00.602382276 +0800
Modify: 2023-06-09 10:39:02.038353258 +0800
Change: 2023-06-09 10:39:02.038353258 +0800
```

## <font color='#0000dd'>ls 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls
cron-20230528  cron-20230528.txt  cron_temp  dnf.librepo.log  log  runtest  runtest2  text.txt
```

-a 显示所有文件及目录 (. 开头的隐藏文件也会列出)

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls -a
.              .bash_profile  cron-20230528.txt  log               runtest2  .viminfo
..             .bashrc        cron_temp          .pip              .ssh      .wget-hsts
.bash_history  .config        .cshrc             .pydistutils.cfg  .tcshrc
.bash_logout   cron-20230528  dnf.librepo.log    runtest           text.txt
```

-l 以长格式显示文件和目录信息，包括权限、所有者、大小、创建时间等。

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls -l
total 456
lrwxrwxrwx 1 root root     22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root  56797 Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root  57274 Jun  9 12:19 cron_temp
-rw-r--r-- 1 root root 333511 Jun  9 10:46 dnf.librepo.log
drwxr-xr-x 9 root root   4096 Jun  9 10:46 log
drwxr-xr-x 3 root root   4096 Jun  9 12:08 runtest
drwxr-xr-x 3 root root   4096 Jun  9 12:09 runtest2
-rw-r--r-- 1 root root      0 Jun  9 10:41 text.txt
```

-R 递归显示目录中的所有文件和子目录。

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls -R
.:
cron-20230528  cron-20230528.txt  cron_temp  dnf.librepo.log  log  runtest  runtest2  text.txt

./log:
anaconda               cron                          hawkey.log-20230528  maillog-20230528   secure-20230604
audit                  cron-20230528                 hawkey.log-20230604  maillog-20230604   spooler
boot.log               cron-20230604                 journal              messages           spooler-20230528
boot.log-20230522      dnf.librepo.log               kdump.log            messages-20230528  spooler-20230604
btmp                   dnf.log                       kern                 messages-20230604  tuned
btmp-20230601          dnf.rpm.log                   kern-20230528        private            wtmp
chrony                 ecsgo.log                     kern-20230604        sa
cloud-init.log         ecs_network_optimization.log  lastlog              secure
cloud-init-output.log  hawkey.log                    maillog              secure-20230528

./log/anaconda:
anaconda.log  dnf.librepo.log  ifcfg.log    ks-script-e9cefe1q.log  ks-script-_qixjqxp.log  program.log  syslog
dbus.log      hawkey.log       journal.log  ks-script-nq7k7iit.log  packaging.log           storage.log

./log/audit:
audit.log

./log/chrony:

./log/journal:
b6ab5170290e430b872c890ce386d1eb

./log/journal/b6ab5170290e430b872c890ce386d1eb:
system@00000000000000000000000000000000-0000000000000f21-0005f4a386cdfa09.journal  system.journal

./log/private:

./log/sa:
sa01  sa04  sa07  sa21  sa24  sa27  sa30   sar02  sar05  sar08  sar23  sar26  sar29
sa02  sa05  sa08  sa22  sa25  sa28  sa31   sar03  sar06  sar21  sar24  sar27  sar30
sa03  sa06  sa09  sa23  sa26  sa29  sar01  sar04  sar07  sar22  sar25  sar28  sar31

./log/tuned:
tuned.log

./runtest:
test

./runtest/test:

./runtest2:
test

./runtest2/test:
```

-lh 以人类可读的方式显示当前目录中的文件和目录大小

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls -lh
total 456K
lrwxrwxrwx 1 root root   22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
-rw------- 2 root root  56K Jun  9 10:39 cron-20230528.txt
-rwxrw--wx 1 root root  56K Jun  9 12:19 cron_temp
-rw-r--r-- 1 root root 326K Jun  9 10:46 dnf.librepo.log
drwxr-xr-x 9 root root 4.0K Jun  9 10:46 log
drwxr-xr-x 3 root root 4.0K Jun  9 12:08 runtest
drwxr-xr-x 3 root root 4.0K Jun  9 12:09 runtest2
-rw-r--r-- 1 root root    0 Jun  9 10:41 text.txt
```

-t 按照修改时间排序显示当前目录中的文件和目录

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# ls -lt
total 456
-rwxrw--wx 1 root root  57274 Jun  9 12:19 cron_temp
drwxr-xr-x 3 root root   4096 Jun  9 12:09 runtest2
drwxr-xr-x 3 root root   4096 Jun  9 12:08 runtest
drwxr-xr-x 9 root root   4096 Jun  9 10:46 log
-rw-r--r-- 1 root root 333511 Jun  9 10:46 dnf.librepo.log
-rw-r--r-- 1 root root      0 Jun  9 10:41 text.txt
-rw------- 2 root root  56797 Jun  9 10:39 cron-20230528.txt
lrwxrwxrwx 1 root root     22 Jun  8 20:59 cron-20230528 -> /var/log/cron-20230528
```

# <font color='006600'>网络通讯</font>

## <font color='#0000dd'>ifconfig 命令</font>

```shell
ifconfig
```
```shell
docker0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        inet6 fe80::42:efff:fede:c41d  prefixlen 64  scopeid 0x20<link>
        ether 02:42:ef:de:c4:1d  txqueuelen 0  (Ethernet)
        RX packets 81416  bytes 60638221 (57.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 91478  bytes 113932560 (108.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.30.41.94  netmask 255.255.240.0  broadcast 172.30.47.255
        inet6 fe80::216:3eff:fe1c:b392  prefixlen 64  scopeid 0x20<link>
        ether 00:16:3e:1c:b3:92  txqueuelen 1000  (Ethernet)
        RX packets 1882794  bytes 1291102558 (1.2 GiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1299485  bytes 234830719 (223.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2  bytes 140 (140.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2  bytes 140 (140.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

veth76e5ab0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::b834:9dff:fedc:b4a5  prefixlen 64  scopeid 0x20<link>
        ether ba:34:9d:dc:b4:a5  txqueuelen 0  (Ethernet)
        RX packets 19570  bytes 6032051 (5.7 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 25823  bytes 41324149 (39.4 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vethd9ef551: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::e060:77ff:fec4:93a0  prefixlen 64  scopeid 0x20<link>
        ether e2:60:77:c4:93:a0  txqueuelen 0  (Ethernet)
        RX packets 34749  bytes 47631532 (45.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 35076  bytes 3687693 (3.5 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

## <font color='#0000dd'>netstat 命令</font>

-a 或 --all 显示所有连线中的Socket

```shell
netstat -a
```
```shell
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:37325           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:sunrpc          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:mountd          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:46719           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:vcom-tunnel     0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:nfs             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:cslistener      0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:hostmon         0.0.0.0:*               LISTEN     
tcp        0      0 iZbp10iy3yejxoxq8qh:ssh 47.96.60.212:esimport   ESTABLISHED
tcp        0      0 iZbp10iy3yejxoxq8:53572 100.100.45.106:https    TIME_WAIT  
tcp        0      0 iZbp10iy3yejxoxq8:60164 100.100.30.26:http      ESTABLISHED
tcp6       0      0 [::]:sunrpc             [::]:*                  LISTEN     
tcp6       0      0 [::]:mountd             [::]:*                  LISTEN     
tcp6       0      0 [::]:39197              [::]:*                  LISTEN     
tcp6       0      0 [::]:vcom-tunnel        [::]:*                  LISTEN     
tcp6       0      0 [::]:nfs                [::]:*                  LISTEN     
tcp6       0      0 [::]:cslistener         [::]:*                  LISTEN     
tcp6       0      0 [::]:36553              [::]:*                  LISTEN     
tcp6       0      0 [::]:hostmon            [::]:*                  LISTEN  
```

-n 或 --numeric 直接使用IP地址，而不通过域名服务器。

-t 或 --tcp 显示TCP传输协议的连线状况。

```shell
netstat -nt
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 172.30.41.94:22         47.96.60.212:3564       ESTABLISHED
tcp        0      0 172.30.41.94:60164      100.100.30.26:80        ESTABLISHED
tcp        0      0 172.30.41.94:35928      100.100.45.106:443      TIME_WAIT
```

-u 或 --udp 显示UDP传输协议的连线状况。

```shell
netstat -nu
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 172.30.41.94:68         172.30.47.253:67        ESTABLISHED
udp        0      0 172.30.41.94:45569      10.143.33.49:123        ESTABLISHED
```

## <font color='#0000dd'>ping 命令</font>

-c <完成次数> 设置完成要求回应的次数。

```shell
ping -c 3 www.baidu.com
```
```shell
PING www.a.shifen.com (180.101.50.188) 56(84) bytes of data.
64 bytes from 180.101.50.188 (180.101.50.188): icmp_seq=1 ttl=50 time=18.0 ms
64 bytes from 180.101.50.188 (180.101.50.188): icmp_seq=2 ttl=50 time=18.0 ms
64 bytes from 180.101.50.188 (180.101.50.188): icmp_seq=3 ttl=50 time=18.0 ms

--- www.a.shifen.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 18.010/18.028/18.040/0.155 ms
```

## <font color='#0000dd'>telnet 命令</font>

登录远程主机

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# telnet www.baidu.com
Trying 180.101.50.188...
```


# <font color='006600'>系统管理</font>

## <font color='#0000dd'>date 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date
Fri Jun  9 01:00:51 PM CST 2023
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date '+%D'
06/09/23
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date '+%x'
06/09/2023
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date '+%T'
13:01:41
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date '+%X'
01:01:47 PM
```
```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date +'%F %X'
2023-06-09 01:02:23 PM
```

## <font color='#0000dd'>exit 命令</font>

退出目前的shell

## <font color='#0000dd'>sleep 命令</font>

```shell
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# date; sleep 3; date
Fri Jun  9 01:06:10 PM CST 2023
Fri Jun  9 01:06:13 PM CST 2023
```

## <font color='#0000dd'>kill 命令</font>

1 (HUP)：重新加载进程。
9 (KILL)：杀死一个进程。
15 (TERM)：正常停止一个进程

```shell
kill -9
```

## <font color='#0000dd'>ps 命令</font>

-aux 显示所有包含其他使用者的进程

```shell
ps -aux | grep "worker"
```
```shell
root           6  0.0  0.0      0     0 ?        I<   May21   0:00 [kworker/0:0H-events_highpri]
root          82  0.0  0.0      0     0 ?        I<   May21   0:07 [kworker/0:1H-events_highpri]
root         147  0.0  0.0      0     0 ?        I<   May21   0:00 [kworker/u5:0-xprtiod]
root        1070  0.0  0.0      0     0 ?        I<   May21   0:00 [kworker/u5:1]
root      144739  0.0  0.0      0     0 ?        I    12:34   0:00 [kworker/0:1-cgroup_pidlist_destroy]
root      145348  0.0  0.0      0     0 ?        I    12:51   0:00 [kworker/0:2-cgroup_pidlist_destroy]
root      145872  0.0  0.0      0     0 ?        I    12:56   0:00 [kworker/u4:1-ext4-rsv-conversion]
root      145892  0.0  0.0      0     0 ?        I    12:58   0:00 [kworker/0:3-cgroup_pidlist_destroy]
root      146246  0.0  0.0      0     0 ?        I    13:02   0:00 [kworker/u4:2-ext4-rsv-conversion]
root      146491  0.0  0.0      0     0 ?        I    13:07   0:00 [kworker/0:0-cgroup_pidlist_destroy]
root      146492  0.0  0.0      0     0 ?        I    13:07   0:00 [kworker/u4:0-events_unbound]
root      146975  0.0  0.0 221528   864 pts/0    R+   13:10   0:00 grep --color=auto worker
```

```shell
ps -ef | grep "worker"
```
```shell
root           6       2  0 May21 ?        00:00:00 [kworker/0:0H-events_highpri]
root          82       2  0 May21 ?        00:00:07 [kworker/0:1H-events_highpri]
root         147       2  0 May21 ?        00:00:00 [kworker/u5:0-xprtiod]
root        1070       2  0 May21 ?        00:00:00 [kworker/u5:1]
root      144739       2  0 12:34 ?        00:00:00 [kworker/0:1-cgroup_pidlist_destroy]
root      145348       2  0 12:51 ?        00:00:00 [kworker/0:2-cgroup_pidlist_destroy]
root      145872       2  0 12:56 ?        00:00:00 [kworker/u4:1-ext4-rsv-conversion]
root      145892       2  0 12:58 ?        00:00:00 [kworker/0:3-events]
root      146246       2  0 13:02 ?        00:00:00 [kworker/u4:2-ext4-rsv-conversion]
root      146491       2  0 13:07 ?        00:00:00 [kworker/0:0-cgroup_pidlist_destroy]
root      146492       2  0 13:07 ?        00:00:00 [kworker/u4:0-events_unbound]
root      147034  145785  0 13:10 pts/0    00:00:00 grep --color=auto worker
```

## <font color='#0000dd'>reboot 命令</font>

重新启动

## <font color='#0000dd'>top 命令</font>

```shell
top
```

## <font color='#0000dd'>sudo 命令</font>

```shell
sudo
```

## <font color='#0000dd'>shutdown 命令</font>

立即关机

```shell
shutdown -h now
```

指定 10 分钟后关机

```shell
shutdown -h 10
```

重新启动计算机

```shell
shutdown -r now
```

## <font color='#0000dd'>who 命令</font>

显示系统中有哪些使用者正在上面

```shell
who
```
```shell
root     pts/0        2023-06-09 13:32 (118.31.243.37)
```

```shell
who -l -H
```
```shell
NAME     LINE         TIME             IDLE          PID COMMENT
LOGIN    ttyS0        2023-05-21 12:11              1058 id=tyS0
LOGIN    tty1         2023-05-21 12:11              1057 id=tty1
```

## <font color='#0000dd'>su 命令</font>

```shell
su
```

## <font color='#0000dd'>free 命令</font>

```shell
free
```
```shell
              total        used        free      shared  buff/cache   available
Mem:        2014428      737684      493664        2120      783080     1118924
Swap:             0           0           0
```

周期性的查询内存使用信息

```shell
free -s 1
```
```shell
              total        used        free      shared  buff/cache   available
Mem:        2014428      738112      493216        2120      783100     1118496
Swap:             0           0           0

              total        used        free      shared  buff/cache   available
Mem:        2014428      738596      492696        2120      783136     1118008
Swap:             0           0           0
```

## <font color='#0000dd'>w 命令</font>

显示目前登入系统的用户信息

```shell
w
```
```shell
13:39:03 up 19 days,  1:27,  1 user,  load average: 0.19, 0.24, 0.13
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/0    118.31.243.37    13:32    0.00s  0.05s  0.00s w
```

## <font color='#0000dd'>cu 命令</font>

用于连接另一个系统主机。

```shell
cu -c 0102377765
```

## <font color='#0000dd'>telnet 命令</font>

登录远程主机

```shell
telnet 192.168.0.5 
```


# <font color='006600'>系统设置</font>

## <font color='#0000dd'>clock 命令</font>

```shell
clock
```

## <font color='#0000dd'>crontab 命令</font>

```shell
*    *    *    *    *
-    -    -    -    -
|    |    |    |    |
|    |    |    |    +----- 星期中星期几 (0 - 6) (星期天 为0)
|    |    |    +---------- 月份 (1 - 12) 
|    |    +--------------- 一个月中的第几天 (1 - 31)
|    +-------------------- 小时 (0 - 23)
+------------------------- 分钟 (0 - 59)
```
```shell
0 6-12/3 * 12 * /usr/bin/backup
```

## <font color='#0000dd'>set 命令</font>

set 指令能设置所使用shell的执行方式，可依照不同的需求来做设置。


## <font color='#0000dd'>export 命令</font>

设置或显示环境变量

```shell
export
```
```shell
declare -x DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/0/bus"
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x HOME="/root"
declare -x HOSTNAME="iZbp10iy3yejxoxq8qhlpiZ"
declare -x LANG="en_US.UTF-8"
declare -x LESSOPEN="||/usr/bin/lesspipe.sh %s"
declare -x LOGNAME="root"
declare -x LS_COLORS="rs=0:di=38;5;33:ln=38;5;51:mh=00:pi=40;38;5;11:so=38;5;13:do=38;5;5:bd=48;5;232;38;5;11:cd=48;5;232;38;5;3:or=48;5;232;38;5;9:mi=01;05;37;41:su=48;5;196;38;5;15:sg=48;5;11;38;5;16:ca=48;5;196;38;5;226:tw=48;5;10;38;5;16:ow=48;5;10;38;5;21:st=48;5;21;38;5;15:ex=38;5;40:*.tar=38;5;9:*.tgz=38;5;9:*.arc=38;5;9:*.arj=38;5;9:*.taz=38;5;9:*.lha=38;5;9:*.lz4=38;5;9:*.lzh=38;5;9:*.lzma=38;5;9:*.tlz=38;5;9:*.txz=38;5;9:*.tzo=38;5;9:*.t7z=38;5;9:*.zip=38;5;9:*.z=38;5;9:*.dz=38;5;9:*.gz=38;5;9:*.lrz=38;5;9:*.lz=38;5;9:*.lzo=38;5;9:*.xz=38;5;9:*.zst=38;5;9:*.tzst=38;5;9:*.bz2=38;5;9:*.bz=38;5;9:*.tbz=38;5;9:*.tbz2=38;5;9:*.tz=38;5;9:*.deb=38;5;9:*.rpm=38;5;9:*.jar=38;5;9:*.war=38;5;9:*.ear=38;5;9:*.sar=38;5;9:*.rar=38;5;9:*.alz=38;5;9:*.ace=38;5;9:*.zoo=38;5;9:*.cpio=38;5;9:*.7z=38;5;9:*.rz=38;5;9:*.cab=38;5;9:*.wim=38;5;9:*.swm=38;5;9:*.dwm=38;5;9:*.esd=38;5;9:*.jpg=38;5;13:*.jpeg=38;5;13:*.mjpg=38;5;13:*.mjpeg=38;5;13:*.gif=38;5;13:*.bmp=38;5;13:*.pbm=38;5;13:*.pgm=38;5;13:*.ppm=38;5;13:*.tga=38;5;13:*.xbm=38;5;13:*.xpm=38;5;13:*.tif=38;5;13:*.tiff=38;5;13:*.png=38;5;13:*.svg=38;5;13:*.svgz=38;5;13:*.mng=38;5;13:*.pcx=38;5;13:*.mov=38;5;13:*.mpg=38;5;13:*.mpeg=38;5;13:*.m2v=38;5;13:*.mkv=38;5;13:*.webm=38;5;13:*.ogm=38;5;13:*.mp4=38;5;13:*.m4v=38;5;13:*.mp4v=38;5;13:*.vob=38;5;13:*.qt=38;5;13:*.nuv=38;5;13:*.wmv=38;5;13:*.asf=38;5;13:*.rm=38;5;13:*.rmvb=38;5;13:*.flc=38;5;13:*.avi=38;5;13:*.fli=38;5;13:*.flv=38;5;13:*.gl=38;5;13:*.dl=38;5;13:*.xcf=38;5;13:*.xwd=38;5;13:*.yuv=38;5;13:*.cgm=38;5;13:*.emf=38;5;13:*.ogv=38;5;13:*.ogx=38;5;13:*.aac=38;5;45:*.au=38;5;45:*.flac=38;5;45:*.m4a=38;5;45:*.mid=38;5;45:*.midi=38;5;45:*.mka=38;5;45:*.mp3=38;5;45:*.mpc=38;5;45:*.ogg=38;5;45:*.ra=38;5;45:*.wav=38;5;45:*.oga=38;5;45:*.opus=38;5;45:*.spx=38;5;45:*.xspf=38;5;45:"
declare -x MAIL="/var/spool/mail/root"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin"
declare -x PWD="/root"
declare -x SHELL="/bin/bash"
declare -x SHLVL="2"
declare -x SSH_CLIENT="118.31.243.37 58022 22"
declare -x SSH_CONNECTION="118.31.243.37 58022 172.30.41.94 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x S_COLORS="auto"
declare -x TERM="xterm-256color"
declare -x USER="root"
declare -x XDG_RUNTIME_DIR="/run/user/0"
declare -x XDG_SESSION_ID="1351"
declare -x which_declare="declare -f"
[root@iZbp10iy3yejxoxq8qhlpiZ ~]# export -p
declare -x DBUS_SESSION_BUS_ADDRESS="unix:path=/run/user/0/bus"
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x HOME="/root"
declare -x HOSTNAME="iZbp10iy3yejxoxq8qhlpiZ"
declare -x LANG="en_US.UTF-8"
declare -x LESSOPEN="||/usr/bin/lesspipe.sh %s"
declare -x LOGNAME="root"
declare -x LS_COLORS="rs=0:di=38;5;33:ln=38;5;51:mh=00:pi=40;38;5;11:so=38;5;13:do=38;5;5:bd=48;5;232;38;5;11:cd=48;5;232;38;5;3:or=48;5;232;38;5;9:mi=01;05;37;41:su=48;5;196;38;5;15:sg=48;5;11;38;5;16:ca=48;5;196;38;5;226:tw=48;5;10;38;5;16:ow=48;5;10;38;5;21:st=48;5;21;38;5;15:ex=38;5;40:*.tar=38;5;9:*.tgz=38;5;9:*.arc=38;5;9:*.arj=38;5;9:*.taz=38;5;9:*.lha=38;5;9:*.lz4=38;5;9:*.lzh=38;5;9:*.lzma=38;5;9:*.tlz=38;5;9:*.txz=38;5;9:*.tzo=38;5;9:*.t7z=38;5;9:*.zip=38;5;9:*.z=38;5;9:*.dz=38;5;9:*.gz=38;5;9:*.lrz=38;5;9:*.lz=38;5;9:*.lzo=38;5;9:*.xz=38;5;9:*.zst=38;5;9:*.tzst=38;5;9:*.bz2=38;5;9:*.bz=38;5;9:*.tbz=38;5;9:*.tbz2=38;5;9:*.tz=38;5;9:*.deb=38;5;9:*.rpm=38;5;9:*.jar=38;5;9:*.war=38;5;9:*.ear=38;5;9:*.sar=38;5;9:*.rar=38;5;9:*.alz=38;5;9:*.ace=38;5;9:*.zoo=38;5;9:*.cpio=38;5;9:*.7z=38;5;9:*.rz=38;5;9:*.cab=38;5;9:*.wim=38;5;9:*.swm=38;5;9:*.dwm=38;5;9:*.esd=38;5;9:*.jpg=38;5;13:*.jpeg=38;5;13:*.mjpg=38;5;13:*.mjpeg=38;5;13:*.gif=38;5;13:*.bmp=38;5;13:*.pbm=38;5;13:*.pgm=38;5;13:*.ppm=38;5;13:*.tga=38;5;13:*.xbm=38;5;13:*.xpm=38;5;13:*.tif=38;5;13:*.tiff=38;5;13:*.png=38;5;13:*.svg=38;5;13:*.svgz=38;5;13:*.mng=38;5;13:*.pcx=38;5;13:*.mov=38;5;13:*.mpg=38;5;13:*.mpeg=38;5;13:*.m2v=38;5;13:*.mkv=38;5;13:*.webm=38;5;13:*.ogm=38;5;13:*.mp4=38;5;13:*.m4v=38;5;13:*.mp4v=38;5;13:*.vob=38;5;13:*.qt=38;5;13:*.nuv=38;5;13:*.wmv=38;5;13:*.asf=38;5;13:*.rm=38;5;13:*.rmvb=38;5;13:*.flc=38;5;13:*.avi=38;5;13:*.fli=38;5;13:*.flv=38;5;13:*.gl=38;5;13:*.dl=38;5;13:*.xcf=38;5;13:*.xwd=38;5;13:*.yuv=38;5;13:*.cgm=38;5;13:*.emf=38;5;13:*.ogv=38;5;13:*.ogx=38;5;13:*.aac=38;5;45:*.au=38;5;45:*.flac=38;5;45:*.m4a=38;5;45:*.mid=38;5;45:*.midi=38;5;45:*.mka=38;5;45:*.mp3=38;5;45:*.mpc=38;5;45:*.ogg=38;5;45:*.ra=38;5;45:*.wav=38;5;45:*.oga=38;5;45:*.opus=38;5;45:*.spx=38;5;45:*.xspf=38;5;45:"
declare -x MAIL="/var/spool/mail/root"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin"
declare -x PWD="/root"
declare -x SHELL="/bin/bash"
declare -x SHLVL="2"
declare -x SSH_CLIENT="118.31.243.37 58022 22"
declare -x SSH_CONNECTION="118.31.243.37 58022 172.30.41.94 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x S_COLORS="auto"
declare -x TERM="xterm-256color"
declare -x USER="root"
declare -x XDG_RUNTIME_DIR="/run/user/0"
declare -x XDG_SESSION_ID="1351"
declare -x which_declare="declare -f"
```

## <font color='#0000dd'>enable 命令</font>

用于启动或关闭 shell 内建指令

```shell
enable
enable .
enable :
enable [
enable alias
enable bg
enable bind
enable break
enable builtin
enable caller
enable cd
enable command
enable compgen
enable complete
enable compopt
enable continue
enable declare
enable dirs
enable disown
enable echo
enable enable
enable eval
enable exec
enable exit
enable export
enable false
enable fc
enable fg
enable getopts
enable hash
enable help
enable history
enable jobs
enable kill
enable let
enable local
enable logout
enable mapfile
enable popd
enable printf
enable pushd
enable pwd
enable read
enable readarray
enable readonly
enable return
enable set
enable shift
enable shopt
enable source
enable suspend
enable test
enable times
enable trap
enable true
enable type
enable typeset
enable ulimit
enable umask
enable unalias
enable unset
enable wait
```


# <font color='006600'>备份压缩</font>

## <font color='#0000dd'>zip 命令</font>

## <font color='#0000dd'>unzip 命令</font>

## <font color='#0000dd'>tar 命令</font>


# <font color='006600'>其他命令</font>

## <font color='0000dd'>tail 命令</font>

```shell
tail -f cron_temp
```


## LINUX

[TOC]



### 软件安装

- 源：类似于一个软件管家的东西

  - 相关操作：（需要管理员权限）

    ```c
    sudo apt-get update 更新软件信息
    sudo apt-get upgrade 软件升级（不经常用）
    sudo apt-get install 安装软件
    dpkg -i 安装软件包
    sudo apt-cache search 查找缓存
    sudo !! 执行某些命令时需要管理员权限（给上一句命令加上管理员权限）
    ```

- linux里，所有 `.d` 的文件都是一个目录  (一般弄不到)

- 安装`nmon`

- linux下一切皆文件



-----



### 常用命令

- `.`是当前目录，`..`是父目录

- `>`：重定向

#### alias


- **alias命令**：用来设置别名，使用该命令可以将一些较长的命令进行简化，使用alias时必须使用单引号`‘ ’`将原来的命令引起来

  - alias 新的命令=‘原命令 -选项/参数‘
  - alias 新的命令=’脚本路径‘   （.bashrc)

#### ls
- **ls命令** ：用来显示目标列表

  - ls (选项) (参数)    `ls -a /etc`
  - ls -a 显示所有档案及目录
  - ls -l 以长格式显示目录下的内容列表
  - ls -a -l  ==  ls -al （没有顺序关联）

#### cp
- **cp命令** ：将一个或多个源文件或者目录复制到指定的目的文件或目录

  - cp (选项) (参数)
  - -R/r 复制目录 (默认情况下cp命令不能复制目录)
  - -i：有交互式作用，如果文件有同名，询问用户
  - -u：源文件比目的文件更新才拷贝

#### mkdir
- **mkdir命令**：用来创建目录

  - mkdir (选项) (参数)
  - -m <文件目标属性> 建立目录的同时对他进行相应的权限设置
  - -p 若想要建立的目录的上一层没有建立，则一并建立上层目录

#### touch
- **touch命令**：(1) 用于把已存在的文件的时间标签更新为系统当前时间（默认方式），他们的数据将原封不动的保留下来；(2) 用来创建新的空文件

#### echo
- **echo 命令** ：用于在shell中打印shell变量的值（echo $HOME），或者直接输出指定的**字符串**

#### pwd
- **pwd命令**：以绝对路径的方式打印当前路径

  - -L：显示逻辑工作目录
  - -P ：显示物理工作目录（就是不是一整条目录，只是当前的）

#### cd
- **cd命令**：切换工作目录 （可以是绝对路径也可以是相对路径）

  - cd (选项) (参数)
  - `cd - ` ：返回之前工作目录所在的路径
  - `cd .` ：目前所在的目录
  - `cd `： 进入用户主目录 （回到家目录）
  - `cd ~` ：进入用户主目录
  - `cd -` ：返回进入此目录之前所在的目录
  - `cd ..` ：返回上级目录 （若当前目录为“/”，执行后还在“/”）
  - `cd ../..` ： 返回上两级目录
  - `cd !$`  ：把上个命令的参数作为cd参数使用
  - HOME ：家目录            
    - cd  $HOME  ($：取变量值，是一个变量引用)  
    - /home 不是家目录
    - cd  /  cd  ~   （回到家目录的方法）
    - HOME = / ：让家目录变成根目录，这种赋值方法是临时的

#### rm
- **rm命令** ：可以删除一个目录中的一个或多个文件或目录

  - rm (选项) (参数)
  - rm -f ： **强制**删除文件或目录
  - -i 删除已有文件或目录之前先询问用户一并处理
  - rm -r/-R ： **递归**处理，将指定目录下的所有文件与子目录一并处理
  - rm -r -f  ：如果后面不加路径或者当前路径为空都会默认为删除当前目录

#### mv
- **mv命令**  ：用来对文件或目录重新命名，或者将文件从一个目录移到另一个目录中

  - mv (选项) (参数)
  - -b 文件存在时，在覆盖之前自动生成备份
  - -f 文件存在时直接覆盖现有文件或目录
  - -i 文件存在时先询问用户，是否进行覆盖

#### uptime
- **uptime命令** ：系统运行时长，平均负载

  - uptime -p ：更美观的方式

#### w
- **w 命令**：获取当前登录用户和正在执行的进程

  - TTY ：虚拟终端，IDLE：空闲时间，
  - w -h ：不打印头信息
  - w - s : 使用短输入格式
  - w -f : 切换显示FROM项，默认显示

#### who
- **who 命令**：显示当前登录系统的用户信息

  - whoami：打印当前有效的用户名称
  - id：查看当前用户
  - who am i ：实际用户到底是谁（就算在root权限下显示的也是实际用户）
  - logname：现实的也是实际用户

#### last
- **last 命令**：显示最近登录信息（放在 /var 下）

  -  -f：指定记录文件
  - -n：指定输出记录数
  - -x：显示系统关机信息

#### uname
- **uname命令** :打印当前系统信息

  - -a：全部信息
  - -m：电脑类型
  - -n：网络上主机的名字
  - -v：os版本
  - -p：处理器类型
  - -i：硬件平台
  - -o：操作系统名称

#### date
- **date命令**：显示或设置系统时间日期

  - -d “string” : 显示字符串所指日期
  - -s “string”：设置时间
  - -u：显示GMT
  - +日期格式：显示使用的日期格式

#### cat
- **cat命令** ：正向连续读

  连接文件并打印到标准输出设备上，他经常用来显示文件的内容（强制读）

  - cat (选项) (参数)

  - -v 列出看不出的字符

  - -n 从1开始对所有输出的行号编号

  - -b 和-n 相似，只是不对于空白行编号

  - 实例：

    ```
    设m1 m2是当前目录下的两个文件
    cat m1 在屏幕下显示文件m1的内容
    cat m1 m2 同时显示文件m1和m2的内容
    cat m1 m2 > file 将文件m1和m2何斌后放入文件file中
    ```

#### tac
- **tac 命令：**反向连续读，行反向

#### nl
- **nl命令：**输出行号显示文件

  - -b 行号指定的方式
    - -b a ：相当于cat -n
    - -b t ： 相当于cat -b
  - -n：列出行号表示方式
    - -n ln 行号在屏幕最左边显示
    - -n rn 行号在自己字段最右边显示
    - -n rz 行号在自己字段的最右边显示，前边自动补全0
  - -w (num) ：行号所占位数

#### more
- **more命令**：一页一页显示文件内容

  - more file 

#### less
- **less命令**：与more类似，但是可以上下翻看，在搜索时会高亮显示

#### head
- **head命令：**只看头几行

  - -n num 显示前num行
  - -n -num 除了后num行外，其他都显示

#### tail
- **tail命令：**只看末尾几行

  - -n num 显示后num行
  - -n -num 除了前num行外，其他都显示

#### od
- **od命令：**以二进制方式查看文件内容

#### chattr
- **chattr命令：**文件隐藏属性

  - a：不能修改atime
  - S：同步写入
  - a：只能增加数据
  - c：自动压缩，解压
  - d：备份文件时不会被备份
  - i：不能删除修改，建立连接
  - s：文件删除时，直接从磁盘删除
  - u：文件删除时，数据内容存在磁盘中

#### which
- **which命令：**寻找路径下可执行文件

#### whereis
- **whereis命令：**寻找特定文件

#### locate
- **locate命令：**模糊定位

#### find
- **find命令：**高级查找

  - 时间相关
    - -mtime n：n天前的 ” 一天之内“修改的文件
    - -mtime +n：n天之前，不包含n，修改过的文件
    - -mtime -n：n天之内，包含n，修改过的文件
    - -newer file：比file还新的文件
    - -mmin：分钟
  - 用户相关
    - -uid n：用户uid为n
    - -gid n：群组gid为n
    - -user name：用户名为name
    - -group name：群组名为name
    - nourse：文件所有者不存在
    - nogroup：文件所有组不存在
  - 文件权限相关
    - -name filename：文件名为filename
    - -size [+-] SIZE：查找比SIZE大或小的
    - -type TYPE：f(file) b(block) c(string) d(dir) l(link) s(socket) p(pipe)（七种文件类型）
    - -perm mode：mode 刚好等于的文件
    - perm -mode：全部包含mode的文件
  - find  ...  -exec ls -l {} \;

#### 数据提取操作

#### tr

- **tr命令**：对标准输入的字符替换,压缩，删除
  - c ：取代所有不属于第一字符集的字符
  - d ：删除所有属于第一字符集的字符
  - s ：将连续重复的字符以单独一个字符表示
  - t ：先删除第一字符集较第二字符集多出的字符

#### cut
- **cut命令**：切分
  - -d  c：以c字符分割
  - -f num：显示num字段的内容 （n-; n - m; -m）
  - -b num：字节
  - -c num：字符

#### grep
- **grep命令**：检索
  - -a：将二进制文件以普通文件的形式搜寻数据
  - -c：统计搜寻到的次数（count）
  - -i：忽略大小写
  - -n：顺序输出行号
  - -v：反向输出（输出没有找到的）

#### sort
- **sort命令**：排序
  - -f：忽略大小写
  - -b：忽略最前面的空格符
  - -M：以月份名称排序
  - -n：以纯数字方式排序
  - -r：反向排序
  - -u：uniq
  - -t：分隔符，默认tab
  - -k：以那个区间排序

#### wc
- **wc命令**：统计字符，字数，行数
  - -l：仅列出行号
  - -w：仅列出多少字
  - -m | -c：仅列出多少字符

#### uniq

- **uniq命令**：去重
  - -i：忽略大小写字符的不同
  - -c：进行计数

#### tee
- **tee命令**：双向重导项
  - tee [-a] file
  - -a：append (就是既把他输出到屏幕上又存放进文件里)

#### split
- **split命令**：文件切分
  - -b SIZE：切分为SIZE大小的文件
  - -l num：以num行为大小切分

#### xargs
- **xargs命令**：参数代换
  - -0：将特殊字符还原成普通字符
  - -eEOF：当xargs 读到EOF时停止
  - -p：执行指令前询问
  - -n num：每次执行command时需要的参数个数

--------

#### su

- su命令：切换用户
  - ` -` | -l ：重新登录

#### sudo

- sudo命令：临时切换到root
  - -s：切换到root shell
  - -i：切换到root shell，并初始化
  - -u username | uid ：用其他身份执行命令权限
  - -l：显示自己的权限

#### passwd

- passwd <username> :设定用户密码
  - -d：清除密码
  - -l：锁定账号
  - -e：使密码过期
  - -S：显示密码认证信息
  - -x days：密码修改过后最大使用天数
  - -n days：密码修改间隔时间
  - -s：更改登录shell
  - -f：更改用户信息（用户昵称）
  - -i：密码过期后宽限时间

#### gpasswd

- gpasswd：设置群组及群组密码
  - -a(add) username：将用户加入群组
  - -d(delete) username：将用户从群组中删除
  - -r：删除密码
  - -A(admin)：将用户设置成群组管理员
  - -M(member)：设置群组成员

#### useradd

- useradd：添加用户
  - -d dir：指定$HOME
  - -m：自动建立$HOME
  - -M：不自动建立$HOME
  - -s shell：设置用户登录shell
  - -u uid：设置用户编号
  - -g groupname：设定用户归属群组
  - -G groupname：设置用户归属附加群组

#### userdel

- userdel：删除用户
  - -r：删除用户相关文件和目录（邮件，家目录）













--------



### BASIC

- 树莓派ID：192.168.1.40 ---  192.168.1.49

- 终端(terminal) 其实就是一个子进程，在退出这个进程的时候对终端做的修改就全部失效了，除非把这些更改都改到文件中

- 查阅命令：
  - man  命令
  - tldr 命令    (too long dont read)
  - （info) 也是一个帮助手册

- 上传GitHub命令：
  - git status  ：查看目录处于什么状态
  - git add 文件名称 ：添加上传文件
  - git commit -m "备注"：备注
  - git push -u origin master ：把文件推上去
  - git log：查看上传版本
  - git reset --hard (commit 值)  ：回溯上传版本
  - github 进去没有图像 ，  更改地址：/etc/hosts    

- `#!` ：  需要哪个解释器执行

- Linux 主要应用：大型机，小型机，中低端服务器，智能家居和几乎所有的嵌入式设备都是基于Linux的

- shell是一种人机交互的接口，是指“提供使用者使用的页面” 的软件，是一种命令解释器

- chmod   a (所有人）+ x（可执行权限）：(change mod) 改变权限

- [a-zA-Z]：索引所有大写 A-Z和小写 a-z

- which   (命令)      查找命令所在位置
  - type   （命令）    命令类型

- $PATH ：路径

- kill -9  (进程号)  (查进程号：ps -ef | grep a.out)   （-9强制杀死）

- <<   （ 内容）     标明什么时候结束    

- fstab     文件系统静态信息

- cat >>a.out << EE
  - EE 代表输入的文本段以什么结束
  - 作用：将输入的文本重定向到文件

- 管道 `|`：先进先出，出去就没有了

- history：查看历史记录
  - 执行某一条历史记录：`!(历史记录的某一条)` 

- ctrl + r：检索历史记录

- 目录结构：
  - /usr : 用户级别相关软件
  - /boot : 系统的引导程序
  - /dev : 所有的设备
  - /etc : 所有软件的配置文件
  - /home : 所有用户的家目录
  - /lib : 库文件
  - /media : 媒体文件
  - /mnt : 专门用来挂载设备（可有可无）
  - /bin : 可执行
  - /var : 动态数据

- 三种启动服务方式：只说了一个systemd，别的不常用了

- /etc/fstab : 可以增加挂载

- env : 环境变量
  - OLDPWD存储的是上一次访问的路径，所以用cd - 可以回到上一次访问的路径

- bashrc 文件
  - bashrc 全局用户  (etc/bashrc) (/home/xinyue/.bashrc)
  - proflie用户登录  (etc/ bashrc)  (/home/xinyue/.profile)
  - bash.logout 用户退出 (etc/bash.logout)  (~/.bash.logout)      
  - 执行文件
    - sourse  bash.bashrc
    - . bash.bashrc 

- c ：字符设备

- 作为一个管理员，如何给其他用户发信息
  - echo "Hello" >> /dev/pts/1
  - echo "hello" > /dev/pts1
  - write  xinyue   pts/1
  - wall "Hello"    广播信息（给所有人）

- 修改文件时间与新建文件：
  - mtime ：内容数据改动时更新这个时间
  - ctime：文件权限属性改动时更新这个时间
  - atime：文件被读被打开的时候更新这个时间

- ls不接受标准输入，需要参数代换
  - echo "b" | xargs ls -al

- d｜rwx|rwx|rwx 

  - 第一个d 表示是一个目录， 后面的三段分别表示： 

    ```
    第一段 是指 owner 属主的读、写、执行权限 
    第二段 是指 group 的读、写、执行权限； 
    第三段 是指 other 的读、写、执行权限
    ```

- chown root:usergroup  /(path)
  chmod    770(想要赋予的权限)    /(path)
  chmod   +t(文件的特殊权限)     /(path)

- `chsh -s Shell <username>` ：更改用户shell

- 去掉空行  ： tr -s '\n'





----------



### 海贼笔记

[基础知识](https://www.haizeix.com/course/208/task/9555/show)

[命令系统](https://www.haizeix.com/course/208/task/9556/show)

[基本系统](https://www.haizeix.com/course/208/task/9557/show)

[用户管理](https://www.haizeix.com/course/208/task/9882/show)



--------



### 脚本语言

- 变量定义

  - a=12  (中间没有空格)

- ``  ：命令替换符， 替换成输出结果

- a=$a:a ： (......  :a拼接)，把变量a和字符a拼接起来

- ${  } ： { } 给$ 符限定空间 

- [[ a ]]    test表达式

- if表达式：

  ```shell
  if [[ a ]]; then
  	# 表达式
  fi
  ```

- -eq ：代表 =

- -ne  ：代表 !=

- -n  ：不输出回车      eg: echo -n

- 数组中 赋值的时候不用加$符号

- 做运算时用双括号((  ....   )) 里面的运算可以用c语言

- 在取值时的变量前用$号    运算里((  ....   ))不用再加了

```shell
# 数组初始化
declare -a prime # (数组名字)
for (( i=1 ; i<=MAX ; i++ ));do
    prime[i]=0
done
```

- 关于执行命令
  - ctrl + z  ：后台挂起命令
  - fg ：跳回任务，将后台执行命令转化为前台执行
  - bg：将挂起命令后台执行过
  - jobs  查看当前的挂起任务



--------



### 小脚本和问题

- 查找文件中字符串最长的文件名

- 写一个自己的 rm

- 用C语言实现 ls，ls -al 

- 定时将指定文件写进日志

- 如何查看一个文件的第101行到120行？

  - man ls | nl -b a -w 8 -n rz | head -n 120 | tail -n 20

  



--------------









---------

1. updatedb

2. find / -name "\*" -mtime +365 -perm 666 2>/dev/null -exec cp {} ~ \;

   ​	ls -al `\*`

   ​        rm `\*`

   


df -h   

sda，sdb   

df -T -m -x 

二维数组

 df -T -m -x tmpfs -x devtmpfs | tail -n +2 |awk'{printf("used["NR"]=%d;Ava["NR"]=%d\n",$4,$5)}'

used[1]=11956;Ava[1]=16697

used[2]=21;Ava[2]=21



 df -m | grep "^/dev" | awk '{printf("%s ", $2)}' |xargs

29899 42

-----------



### 项目讲解

- 查找配置文件
  - int get_conf_value(char *pathname, char *key_name, char *value);
  - 主要函数 ：strstr，strlen，strncpy，fopen，getline （获取长度）
- 数据打印到文件里
  - int write_Pi_log (char *PIHealthLog,  const char *format, ...);
  - write_Pi_log(PiHealthLog, "Connection to %s success \n", host_t);
  - 用到函数： vfprintf()， fprintf()
- 多进程 ：共享内存
- 多线程 ：比进程方便



数据分层

PCIE   PCI借口扩展  （内存条）





--------

1. sar 1 -C 5    检查cpu , 一秒一次， 取五次
2. grep -n    输出行号
3. strings    文件
4. arp -a
5. atoi() 字符串转整型


## 安装
###方式一：make安装
**步骤1：**
[Linux man-pages 下载网址](https://www.kernel.org/doc/man-pages/contributing.html)
```bash
安装命令：
sudo git clone https://git.kernel.org/pub/scm/docs/man-pages/man-pages
```
在/home/nvidia路径下执行git命令，会下载至Download文件夹中，
clone之后的地址可能会变，可以打开Linux man-pages 下载网址再次确认。
**步骤2：**
```bash
cd /Downloads/man-pages
make install
```
会将man0至man8安装至/usr/local/share/man

**验证：**
此时执行
```bash
man ll
```
可有结果显示，说明系命令的说明可以找到
由于在jeston设备上首先使用的是方式二，方式二中已单独安装了C、C++、git的manual,所以如果一开始执行的是方式一，当遇到C、C++、git的man命令无法生效时，安装方式二再单独安装一下。

### 方式二：sudo apt-get install命令安装
**不建议用方式二**，会导致各种问题，至少在jeston上会有path-exclude以及man文件夹中文件不齐的问题

Ubuntu默认是没有完全安装man手册的,安装之前先阅读下面的文章
**docker上安装Ubuntu环境man命令出现No manual entry for xxx的问题**
[解决方法](https://blog.csdn.net/lsp_123456/article/details/85932172?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165772450716782350855178%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165772450716782350855178&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-85932172-null-null.142^v32^experiment_2_v1,185^v2^control&utm_term=No%20manual%20entry%20for%20open%20See%20man%207%20undocumented%20for%20help%20when%20manual%20pages%20are%20not%20available.&spm=1018.2226.3001.4187)

**步骤1：**
> sudo apt-get install manpages

先执行安装过程中的一条安装命令，触发/etc/dpkg/dpkg.cfg.d/excludes生成
> #Drop all man pages
path-exclude=/usr/share/man/*

**步骤2：**
> #Drop all man pages
> #path-exclude=/usr/share/man/*

将path-exclude=/usr/share/man/*注释

> sudo apt-get remove manpages

**步骤3**
[安装链接](https://blog.csdn.net/aiwangtingyun/article/details/79273802?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-79273802-blog-121116023.pc_relevant_aa&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-1-79273802-blog-121116023.pc_relevant_aa&utm_relevant_index=1)
只执行：
```bash
1)安装C语言 库函数基本帮助文档:
$ sudo apt-get install libc-dev
$ sudo apt-get install glibc-doc
$ sudo apt-get install manpages
$ sudo apt-get install manpages-de
$ sudo apt-get install manpages-de-dev
$ sudo apt-get install manpages-dev
2)、安装 POSIX 函数帮助文档：
$ sudo apt-get install manpages-posix
$ sudo apt-get install manpages-posix-dev
3)、安装内核函数文档：
$ sudo apt-get install linux-doc
$ sudo apt-get install libcorelinux-dev     #ubuntu上执行不成
4）c++的另外安装
```
**步骤4**
[ubuntu查看c++库或者api](https://blog.csdn.net/caoxiong_tju/article/details/88562707?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522165776370216782350811797%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=165776370216782350811797&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-88562707-null-null.142^v32^experiment_2_v1,185^v2^control&utm_term=ubuntu%E6%9F%A5%E7%9C%8Bc%2B%2B%E7%89%88%E6%9C%AC&spm=1018.2226.3001.4187)

```bash
ubuntu使用如下命令安装
sudo apt-get install cppman
查看需要的函数使用方法时可以使用下面的命令，如查看std::string
cppman std::string
```
**git --help**
[git获取帮助出现No manual entry for git-的解决办法](https://www.codenong.com/js4523b584af44/)
```bash
[root@localhost ~]# cd /usr/local/share/man  
[root@localhost man]# git clone http://git.kernel.org/pub/scm/git/git-manpages.git
[root@localhost man]# ls
git-manpages man1       
[root@localhost man]# ls git-manpages/  
man1  man5  man7
[root@localhost man]# cp -r /usr/local/share/man/git-manpages/* /usr/local/share/man/  
[root@localhost man]# git help config
验证发现出现了帮助信息，这样就可以使用git help命令咯
```

**/usr/local/share/man中man*文件不齐全**
```bash
man ls
显示无法找到
```
由于C、C++、git 等是另外安装的，可以找到，可是系统自带的命令反而不能，查看/usr/local/share/man文件夹，发现man0至man8文件夹并不齐全
改用方式一安装
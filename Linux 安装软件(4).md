# Linux 安装软件



## 下载 

* curl https://www.baidu.com  # 模拟浏览器向百度发送请求 
* curl -0  https://registry.npmmirror.com/-/binary/python/3.7.9/Python-3.7.9.tgz



* wget -c https://registry.npmmirror.com/-/binary/python/3.7.9/Python-3.7.9.tgz



## 压缩和解压缩  

windows压缩格式 

1. rar 
2. zip
3. 7zip 
4. iso  

linux 

	1. zip 
	1. gz   tgz 
	1. bz2 
	1. xz 



### gz  

> gzip 

```shell
gzip 文件1 文件2 文件n  # 支持批量压缩文件 原文件被替换 .gz后缀  
gzip 不能压缩目录 
gzip -d 2.jpg.gz 3.png.gz 4.gif.gz 5.rmvb.gz # 支持批量解压缩 .gz的源文件不在了
```



### bz2

```
bzip2 文件1 文件2 文件n  # 支持批量压缩文件 原文件被替换 .bz2后缀  
bzip2 不能压缩目录 
bzip2 -d 2.jpg.bz2 3.png.bz2 4.gif.bz2 5.rmvb.bz2 # .bz2的源文件 不再了 
```



### xz

```
xz -z 文件1 文件2 文件n  # 支持批量压缩文件 原文件被替换 .xz后缀  
xz 不能压缩目录 
xz -d 2.jpg.xz 3.png.xz 4.gif.xz 5.rmvb.xz # .xz的源文件 不再了 
```



### tar

> 打包命令 上面只能压缩文件  不能压缩目录 
>
> 有了tar 之后 先打包再压缩  



```
-c 打包 
-v 显示打包的过程 
-f 指定文件
-x 解包  
tar -cvf 自己起个名字
.tar 2.jpg 3.png 4.gif 5.rmvb 6.avi 7.mkv 8.txt 13.pdf 14.mp3 

tar -xvf haha.tar 

# 上面仅仅是打包  没有压缩   

-z gz 对tar 进行压缩解压缩
-j bz2 对 tar 进行压缩解压缩
-J xz 对 tar 进行压缩解压缩

tar -zcvf 名字.tar.gz 文件 目录 文件 目录 # 使用gz 的方式 打包并压缩文件或者目录
tar -zxvf 名字.tar.gz # 使用gz 的方进行解包并解压缩  


tar -jcvf 名字.tar.bz2 文件 目录 文件 目录 # 使用bz2 的方式 打包并压缩文件或者目录
tar -jxvf 名字.tar.bz2 # 使用 bz2 的方进行解包并解压缩  


tar -Jcvf 名字.tar.gz 文件 目录 文件 目录 # 使用xz 的方式 打包并压缩文件或者目录
tar -Jxvf 名字.tar.gz # 使用xz 的方进行解包并解压缩  

pwd  # 查看在哪里个目录下  
wget -c https://registry.npmmirror.com/-/binary/python/3.8.0/Python-3.8.0.tgz # 下载 

# gz 的方式解包并解压缩  

tar -zxvf Python-3.8.0.tgz  # 加压 跟 下载的 一个目录  



```



### zip unzip 

```
yum -y install zip unzip 

zip 名字.zip 文件 目录
```



## 软链接 ln

> 就是一个windows 的快捷方式 

```
ln -s 源文件 目标文件  

ln -s /usr/bin/python /root/快捷方式的名字



python  等同于 ./root/快捷方式的名字 # ./等同于函数的() 也就是执行的意思 
```





## linux 软件安装  

* rpm 

  * 像windows安装软件一样  需要下载 rpm 包（windows系统数exe包）
  * 优点 简单 
  * 缺点 要求严格按照安装顺序  因为 软件和软件之间有依赖关系  
  * abcd  b依赖于a c 依赖于b d依赖于c  
  * 先现在rpm包  
  * 然后切换到 包所在的目录
  * rpm -ivh ***.rpm  
  * https://rpmfind.net/ 查找rpm包的网址 

* yum

  * 自动识别依赖关系 并且自动下载依赖包并自动安装  
  * 安装的还是rpm包  

  ```
  yum -y install 包名 # 不用提示直接下载
  yum list # 列出已经安装的包列表
  yum -y remove 包名 # 删除指定的包
  yum -y update 包名# 更新指定的包  
  
  ```

  

* 编译安装

  > linux 软件都是 c c++ 属于底层语言编写  需要编译 
  >
  > 缺点:麻烦 
  >
  > 优点：性能最好 

  1. 安装必备依赖库 

  2. 下载软件  gz bz2 xz tgz 

  3. 解包并解压缩 

  4. 配置 软件装在哪里  启用哪些选项   依赖于哪些选项等 

     ./configure  

     ​		--prerix    指定安装在哪里     /usr 

     ​		no-    禁用选项 

     ​		--with-  依赖于哪些模块

     ​		--enable  启用哪些选项 

  5. 编译  

     make 

  6. 安装 

     make install

    make && make install 

### 数据备份

* cp  拷贝

  * cp 文件  文件1   # 复制文件一份  名字为 文件1 
  * cp -r 目录 新目录  # 复制目录为  名字为新目录  
  * 

* mv  移动  重命名 

  ```
  mv 文件1 新名字 # 同一个目录下面 相当于重命名  
  mv 文件1 其他目录  # 剪切  
  [root@localhost tmp]# mv requirements.txt /root/haha.txt
  # 不同目录移动 也可以指定移动后的文件的新名字  
  ```

  



​	

## yum源切换  

* 阿里云  https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b11m3vH8g
* 清华大学 https://mirror.tuna.tsinghua.edu.cn/
* 搜狐 https://mirrors.sohu.com/centos/
* 163 https://mirror.tuna.tsinghua.edu.cn/







```
1.cat /etc/redhat-release  # 查看你系统的版本 
2.mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup # 将默认的文件进行备份
3.wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo #下载阿里云镜像文件
4.yum clean all # 清空缓存区 
5.yum makecache  # 生成缓存 


```



## 安装 python 

1.安装依赖

```
yum -y install gcc gcc-c++  openssl-static 
```

2.下载python\openssl安装包

```shell
wget -c https://registry.npmmirror.com/-/binary/python/3.8.0/Python-3.8.0.tgz

wget -c https://www.openssl.org/source/old/1.1.1/openssl-1.1.1e.tar.gz 


tar -zxvf openssl-1.1.1e.tar.gz # 解包并解压缩

```

3.安装openssl 

```
cd openssl-1.1.1e # 切换到 解压后的openssl 文件夹
ls -al 
./config --prefix=/usr/local/openssl no-zlib  # 配置安装路径及禁用模块

make && make install  # 编译及安装 
```

4.修改openssl 软连接  

```
rm -rf /usr/include/openssl/  #删除原来的命令  用安装好的进行替换（软连接） 
ln -s /usr/local/openssl/include/openssl  /usr/include/openssl

rm -rf /usr/lib64/libssl.so.1.1
ln -s /usr/local/openssl/lib/libssl.so.1.1 /usr/lib64/libssl.so.1.1

rm -rf /usr/lib64/libcrypto.so.1.1
ln -s /usr/local/openssl/lib/libcrypto.so.1.1  /usr/lib64/libcrypto.so.1.1

rm -rf /usr/bin/openssl
ln -s /usr/local/openssl/bin/openssl /usr/bin/openssl

echo '/usr/local/openssl/lib' >> /etc/ld.so.conf

cd ~ 

[root@localhost ~]# openssl version

```

5.安装python 

```
cd Python-3.8.0/

./configure --prefix=/usr/local/python3 --with-openssl=/usr/local/openssl

make && make install 
```

6.查找python所在的位置

```shell
which python

cd /usr/bin 
ls -al | grep python # 发现 python-> python2 python2-> python2.7

rm -rf /usr/bin/python

ln -s /usr/local/python3/bin/python3 /usr/bin/python

cd ~  # 切换到家目录 

测试:

[root@localhost ~]# python
Python 3.8.0 (default, May 23 2022, 16:40:42) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-44)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import ssl
>>> 

以上证明没有问题  


上面没有问题 但是 yum 出问题了 
vim /usr/bin/yum 

第一行 将  #!/usr/bin/python   改成#!/usr/bin/python2.7 
保存并退出  

vim /usr/libexec/urlgrabber-ext-down
#! /usr/bin/python 改成 #! /usr/bin/python2.7
保存并退出 
vim /usr/bin/yum-config-manager

#!/usr/bin/python -tt  改为  #!/usr/bin/python2.7 -tt



将pip 进行配置 跟 python配套  

/usr/bin 下面的命令 可以直接输入  
rm -rf /usr/bin/pip 
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip


# 设置国内pip 源  
mkdir -p ~/.pip

vim ~/.pip/pip.conf

[global]
timeout = 60
index-url = http://pypi.douban.com/simple
trusted-host = pypi.douban.com


保存并退出 
:wq



pip install requests 

pip install --upgrade pip # 更新一下pip  warning 黄色 可以忽略 error 红色 
```

## 创建虚拟环境

### windows 



```
python -m pip install --upgrade pip 
pip install virtualenvwrapper-win 

mkvirtualenv 环境的名字  # 创建一个新的虚拟环境 
deactivate # 退出当前的虚拟换景 

lsvirtualenv # 列出使用mkvirtualenv创建的所有虚拟环境 
workon 虚拟环境名字  # 进入执行的虚拟环境 

查看虚拟环境所在的位置 

1.先进入指定的虚拟环境
C:\Users\neyo>workon python3_crawl
2.cdvirtualenv 
(python3_crawl) C:\Users\neyo>cdvirtualenv
(python3_crawl) C:\myvirtualenv\python3_crawl>

# C:\myvirtualenv\python3_crawl 这就是 python3_crawl 所在的位置 
```


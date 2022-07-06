### 登录服务器



### 修改命令行配色

复制粘贴下面两行代码：

```sh
echo  'export PS1="\[\033]2;\h:\u \w\007\033[33;1m\]\u \033[35;1m\t\033[0m \[\033[36;1m\]\w\[\033[0m\]\n\[\e[32;1m\]$ \[\e[0m\]"' >> ~/.bashrc
source  ~/.bashrc
```

### 查看帮助文档

man 命令，help 命令，或者某个命令的  --help  参数     

```sh
man  ls		## 用 man 命令查看 ls 命令的帮助文档
help  ls	## 用 help 命令查看 ls 命令的帮助文档	
ls  --help	## 用 --help 参数查看 ls 命令的帮助文档
```

### ls 命令

列出目录文件情况：

```sh
ls				## 列出当前目录的文件
ls  ./			## 同上，‘.’号代表当前目录
ls  ./*txt		## 列出当前目录下以 txt 结尾的文件
ls  ../ 		## 列出上层目录的文件
ls  -a			## 列出当前目录下的所有文件，包括隐藏文件
ls  -l			## 列出当前目录下文件的详细信息
ll				## ls  -la 的简写
ls  -lh 		## 加上 -h 参数，以 K、M、G 的形式显示文件大小
ls  -lh  /		## 列出根目录下文件的详细信息
```

### cd 命令

切换工作目录

```sh
cd  ..       ## 切换到上层目录，相对路径
cd  /        ## 切换到根目录
cd  /teach/  ## 切换到根目录下的teach，绝对路径
cd  -        ## 返回上一次的工作目录
cd  ~        ## 回到用户家目录
cd           ## 同上，回到用户家目录
```

### mkdir

```sh
# 创建目录
mkdir dir0
ls
mkdir dir0/sub1/sub2
ls
ls dir0
mkdir -p dir0/sub1/sub2
ls dir0
ls dir0/sub1/
mkdir -p  test{1..3}/test{1..3}
tree
```

### touch

```sh
ls
touch  file.txt  new.txt
ls
touch  file{1..5}
ls
```

### rm

```
rm  -i  file.txt
ls  file*
rm  file*
rm  -r  test1

```

### mv

```sh
mv  file1   Data/file2

```

### cp

```sh
cp   readme.txt   Data/
mkdir  dir0
cp  -r  dir0  Data/


```

### ln

```sh
ln -s /teach/software/Miniconda3-latest-Linux-x86_64.sh  ./


```

### tar

```sh
## 解压    tar  [参数]  [待解压包]
tar  -zxvf  Data.tar.gz
## 压缩    tar  [参数]  <压缩后文件名>  [待压缩文件/目录]        (-j 压缩为 .bz2)
tar  -zcvf  Data.tar.gz    Data  ...               

## .zip  .gz  .bz2  的压缩文件  通常是 一个文件一个压缩包
# tar.gz  是多个文件打包在一个压缩文件中

```

### cat

```sh
cat  readme.txt
cat  -n  readme.txt
## 写入文件
cat >file
Welcome to Biotrainee() !
^C			## 这里是按Ctrl  C
## 查看
cat file
Welcome to Biotrainee() !

zcat  # 查看压缩文件

```

### head、tail

```sh
head  -n  20  Data/example.fq
## 查看 .bashrc 的最后 10 行
tail  ~/.bashrc
## 查看第20行
head  -n  20  Data/example.fq | tail -1


```

### less

按 q 退出

```sh
less  Data/example.fq
less -S Data/example.fq
less -N Data/example.fq
zless -N Data/reads.1.fq.gz


```

### wc

```sh
cat -n readme.txt
cat readme.txt | wc   # 返回结果只有数字
wc -l readme.txt      # 返回数字和文件名

wc  # 统计文本  常见参数 -l 统计行数  -w 统计字符串数  -c 统计字节数（空格 换行符 都算一个字节）

```

### cut

```sh
less -S Data/example.gtf | cut -f 1,3-5
less -S Data/example.gtf | cut -d 'h' -f 1

cut  # 文本切割  对列切割
常见参数： -d  指定分隔符，默认\t
         -f  输出哪几列 （字段fields） 

```

### sort

```sh
less -S Data/example.gtf | sort -k 4 | less -S
less -S Data/example.gtf | sort -n -k 4 | less -S


```

### uniq  去除重复行

```sh
less -S Data/example.gtf | cut -f 3 | sort | uniq -c

# 常见参数： -c:统计每个字符连续出现的行数    
# 去除的是 两个相邻的一模一样的行 

```

### paste  文本合并

```sh
less -S Data/example.fq | paste - - - | less -S
paste file1 file2  

# 常见参数：-d:指定分隔符  -s:按行合并   
paste  - -      # 合并成两列   
paste  - - -    # 合并成三列
paste  - - - -  # 合并成四列

```

### tr 字符替换

```sh
cat readme.txt | tr 'e' 'E'
cat readme.txt | tr '\n' '\t'
cat readme.txt | tr -d 'e' 


```


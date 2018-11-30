----
本篇文章的产生，是为了应对花样查找到文件进行处理

## 参数

-print 将查找到的文件输出到标准输出

-exec   command   {} \;      将查到的文件执行command操作,{} 和 \;之间有空格

-ok           和-exec相同，只不过在操作前要询用户


## 敲黑板

mtime ls -l 最近修改文件内容的时间

atime ls -lu 最近访问文件的时间

ctime ls -li 最近文件有所改变的状态 ,如文件修改,属性\属主 改变 ,节点 ,链接变化等 ,应该是不拘泥只是时间前后的改变



## 时间查询

  查找在系统中最后10分钟访问的文件    
 ```
    find    /   -amin    -10     
 ```
  查找在系统中最后48小时访问的文件       
 ```
    find    /   -atime   -2 
 ```
  查找在系统中最后5分钟里修改过的文件                           
```
    find    /   -mmin   -5      
```
  查找在系统中最后24小时里修改过的文件       
 ```
   find    /   -mtime   -1           
 ```
  在/home下查60分钟前改动过的文件   
 ```
   find /home -mmin    +60    
 ```
  查最近30分钟前被存取过的文件        
 ```
   find /home   -amin   +30         
 ```
  在/home下查更新时间比tmp.txt近的文件或目录    
 ```
   find /home   -newer   tmp.txt     
 ```
  在/home下查存取时间比tmp.txt近的文件或目录       
 ```
  find /home   -anewer   tmp.txt     
 ```
  列出文件或目录被改动过之后，在2日内被存取过的文件或目录      
 ```
find   /home   -used   -2   
 ```
 在/home下查最近两天内改动过的文件               
 ```
  find   /home   -mtime   -2      
 ```
  查1天之内被存取过的文件        
 ```
  find /home    -atime -1    

 ```
----

## 模糊查询（通配符）

  在当前目录下查找以april开始的文件
```
 find   -name april*     
```
  在当前目录下查找以april开始的文件，并把结果输出到file中   
 ```
 find   -name   april*   fprint file      
 ```
  查找以ap或may开头的文件         
 ```                         
 find   -name ap* -o -name may*    
 ```
  在/tmp下查找名为wa开头且类型为符号链接的文件   

 ```
 find   /tmp   -name wa* -type l  

 ```
查以大写字母开头的文件      
 ```
 find   .    -name   "[A-Z]*"   -print   
 ```
 查以两个小写字母和两个数字开头的txt文件   
 ```     
find   .   -name   "[a-z][a-z][0–9][0–9].txt"    -print   
 ```

## 文件系统类型

在/mnt下查找名称为tom.txt且文件系统类型为vfat的文件  

 ```
   find   /mnt   -name tom.txt   -ftype vfat     
 ```

  在/mnt下查找名称为tom.txt且文件系统类型不为vfat的文件  
​       
 ```
    find   /mnt   -name t.txt ! -ftype vfat         
 ```

 在/tmp下查找名为wa开头且类型为符号链接的文件   

 ```     
  find   /tmp   -name wa* -type l   
 ```
当前目录下查找以yao开头的文件并显示出文件类型  
   ```   
 find . -name "yao*"   | xargs file
   ```
----
## 文件长度

查长度为100c的文件并打印
 ```                                 
find   .   -size   100c      -print       
 ```
查长度超过期作废10块的文件（1块=512字节）     
```
find   .   -size   +10   -print               
```
查长度大于1Mb的文件       
 ```
 find   .   -size   +1000000c   -print       	
 ```

----

## 文件属主权限

列出/home目录内属于用户cnscn的文件或目录     
 ```
   find   /home   -user cnscn   
 ```
 列出/home目录内用户的识别码大于501的文件或目录  
 ```
 find   /home   -uid   +501      
 ```
列出/home内组为cnscn的文件或目录     
 ```
 find   /home   -group   cnscn    
 ```
 列出/home内组id为501的文件或目录       
 ```
  find   /home   -gid 501    
 ```
   列出/home内不属于本地用户的文件或目录     
 ```
   find   /home   -nouser     
 ```
  列出/home内不属于本地组的文件或目录     
 ```
   find   /home   -nogroup    
 ```
   查找在系统中属于组lijinghua的文件    
 ```                            
find    /      -group   lijinghua   
 ```
 查权限为700的文件或目录   
 ```
  find   /home   -perm   0700 
 ```
 查找在系统中属于作废用户的文件    
 ```
   find    /      -nouser         
 ```
  查找在系统中属于FRED这个用户的文件      
 ```
   find    /      -user    fred       
 ```

## 文件大小

查找大小为0的文件或空目录               
 ```
   find   /home   -empty       
 ```
查大于512k的文件       
 ```
 find   /home   -size   +512k         
 ```
 查小于512k的文件                
 ```
  find   /home   -size   -512k     
 ```
----


## 目录深度

  列出/home内的tmp.txt 查时深度最多为3层            
 ```
   find   /home    -name tmp.txt    -maxdepth      #max最大为3层

 ```
  从第2层开始查       
 ```
 find   /home    -name tmp.txt    -mindepth       
 ```
----

## 其他 

 查找在系统中为空的文件或者文件夹        
 ```
  find    /   -empty   
 ```
 查硬连接数大于2的文件或目录           
 ```
 find   /home   -links   +2    
 ```
 在/tmp目录下查找tmp.txt文件，并打开该文件    
​        
 ```
   find   /tmp   -name tmp.txt   -exec cat {} \;
 ```
 在/tmp目录下查找tmp.txt文件，并询问是否要删除          
 ```
  find   /tmp   -name   tmp.txt   -ok   rm {} \;
 ```
 在/tmp下查找名为wa开头且类型为符号链接的文件   
 ```
 find   /tmp   -name wa* -type l  
 ```
## 扩展

删除多少天之前的文件
```
find /yourpath -mtime +31 -exec rm {} \;
find /yourpath -mtime +366 -exec rm {} \;
```
查询当天改过的文件
```
find   ./   -mtime   -1   -type f   -exec   ls -l   {} \;
```
查询当前目录下的文件并复制到/tmp 目录下
```
find -type f   -print | cpio -pdv  /tmp
```
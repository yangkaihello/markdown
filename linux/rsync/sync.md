## rsync 同步

* 本地增量同步

  > ```
  > rsync -au -pv /源目录 /目标目录
  > ```
* 远程增量同步

  >  ```
  >  #远程服务器目录同步到本地
  >  rsync -au -pv USER@HOST:/SRC /DEST
  >
  >  #本地同步到远程服务器目录
  >  rsync -au -pv /SRC USER@HOST:/DEST
  >  
  >  #rsync传输
  >  rsync  -au -pv rsync://USER@HOST[:PORT]/SRC /DEST
  >  ```

* 排除某些文件传输

>  ```
>  #rsync传输 SRC 源目录下的 certain 目录不进行传输
>  rsync  -au -pv -f "- SRC/certain" rsync://USER@HOST[:PORT]/SRC /DEST
>  ```

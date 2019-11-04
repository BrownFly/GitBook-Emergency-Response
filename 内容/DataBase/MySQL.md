## 日志分析

### 配置

查看`log`配置信息：
```bash
$ show variables like '%general%';
```
开启日志：
```bash
$ SET GLOBAL general_log = 'On';
```
指定日志文件路径：
```bash
$ SET GLOBAL general_log_file = '/var/log/mysql/mysql.log'
```

### 分析

```bash
# 查看哪些IP在爆破
$ grep  "Access denied" mysql.log |cut -d "'" -f4|uniq -c|sort -nr
# 爆破用户字典有哪些
$ grep  "Access denied" mysql.log |cut -d "'" -f2|uniq -c|sort -nr
```

### 查看目录是否有异常文件

目录：
```bash
mysql\lib\plugin
c:/windows/system32/wbem/mof/
```
`UDF`提权痕迹：
```bash
$ select * from mysql.func;
```
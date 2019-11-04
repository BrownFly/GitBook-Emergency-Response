## 场景

`Redis`未授权访问导致远程植入挖矿脚本。

## 处理

### 重要日志备份

#### 系统日志

压缩打包整个`/var/log`目录：
```bash
$ tar -czvf /var/log.tar.gz /var/log
$ mv log.tar.gz /tmp 
```

#### 历史命令

```bash
$ mv ~/.bash_history /tmp/history
```

### 系统状态

#### 查看在线用户

```bash
$ w
$ last -xad
```

#### 查看系统服务

```bash
$ chkconfig --list
```

#### 查看最近一个月更改的文件

```bash
$ find -type f  -mtime -30
```
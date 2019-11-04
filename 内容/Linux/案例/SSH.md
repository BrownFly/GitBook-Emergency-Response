## 登录成功

```bash
$ grep 'Accepted' /var/log/secure | awk '{print $11}' | sort | uniq -c | sort -nr
# 或者
$ last # 读取 /var/log/wtmp 文件
```

## 登录失败

```bash
$ grep 'Failed' /var/log/secure | awk '{print $11}' | sort | uniq -c | sort -nr
# 或者
$ lastb # 读取 /var/log/btmp 文件
```

## 检查后门

### 对比ssh版本

```bash
$ ssh -V
```

### 查看配置文件和/usr/sbin/sshd时间

```bash
$ stat /usr/sbin/sshd
```

### 查看信息

```bash
$ strings /usr/sbin/sshd
```

### 监控sshd进程读写文件操作

```bash
$ ps axu | grep sshd | grep -v grep
root 65530 0.0 0.1 48428 1260 ? Ss 13:43 0:00 /usr/sbin/sshd
$ strace -o aa -ff -p 65530
grep open aa* | grep -v -e No -e null -e denied| grep WR
aa.102586:open("/tmp/ilog", O_WRONLY|O_CREAT|O_APPEND, 0666) = 4
```
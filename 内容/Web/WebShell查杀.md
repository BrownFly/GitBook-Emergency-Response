## Windows

`D`盾

## Linux

### 命令查找

```bash
$ find  /site/* -type f -name "*.php"  |xargs grep "eval"
$ find /site/* -type f -name "*.php" |xargs grep "base64_decode"
$ find /site/* -type f -name "*.php" |xargs grep "@$"
$ find /www/ -name "*.php" |xargs egrep 'assert|phpspy|c99sh|milw0rm|eval|\(gunerpress|\(base64_decoolcode|spider_bc|shell_exec|passthru|\(\$\_\POST\[|eval \(str_rot13|\.chr\(|\$\{\"\_P|eval\(\$\_R|file_put_contents\(\.\*\$\_|base64_decode'
```

查找`24`小时内被修改的`PHP`文件：
```bash
$ find ./ -mtime 0 -name "*.php" 
```

### 工具

[河马](http://www.shellpub.com)
[深信服Webshell网站后门检测工具](http://edr.sangfor.com.cn/backdoor_detection.html)

### 创建Audit审计规则

```bash
$ vim /etc/audit/audit.rules
-a exclude,always -F msgtype=CONFIG_CHANGE
-a exit,always -F arch=b64 -F uid=48 -S execve -k webshell
```
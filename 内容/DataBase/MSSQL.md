## 日志分析

## 功能检查

### xp_cmdshell

查看`xp_cmdshell`是否被启用：
```sql
Exec master.dbo.xp_cmdshell 'whoami'
```
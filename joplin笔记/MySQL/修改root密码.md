> 在日常使用数据库中，有的时候想要修改数据库的root的密码，在这记录一下

1. 首先配置好MySQL的环境变量 
2. 配置完成后 输入`mysql -u root -p` 进入登录窗口
3. 输入之前的密码进入，进入成功后输入`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '新密码';`来修改密码
4. 如果MySQL 5.7.6及以上版本的，还需要输入一条命令`ALTER USER 'root'@'localhost' PASSWORD EXPIRE NEVER;`,这将确保密码永不过期。
5. 最后输入`FLUSH PRIVILEGES;`来刷新权限。
6. 至此，root密码就已经修改成功了。
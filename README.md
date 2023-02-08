## 📄 MySQL 快速安装指南

#### 1, 复制 `my.ini` 和 `startup.bat` 至 MySQL 根目录 .

```
mysql
  ├── bin
  ├── docs
  ├── include
  ├── lib
  ├── share
  ├── LICENSE
  ├── my.ini *
  ├── README
  └── startup.bat *
```

#### 2, 如果没有 `data` 目录, 则需要进行 [初始化](https://dev.mysql.com/doc/refman/8.0/en/data-directory-initialization.html) (你会获得一个 `临时密码`) .

```
.\bin\mysqld.exe --initialize --console
```

#### 3, 运行 MySQL 服务器 , 双击 `startup.bat` 或 执行如下命令 .

```
.\bin\mysqld.exe --console
```

#### 4, 使用 `临时密码` 进行登录 .

```
.\bin\mysql.exe -u root -p
Enter password: 临时密码
```

#### 5, 设置 `新密码` .

```
ALTER USER 'root'@'localhost' IDENTIFIED BY '新密码';
```

#### 6, 配置远程连接 (注意 : 生产环境不建议开启远程连接,可能会造成安全性的问题 !!!) .

```
将 'mysql' 库下 'user' 表对应的用户 'HOST' 字段更改为 '%' 即可 (初始配置时建议删除多余的初始用户)
```

#### 7, 将 MySQL 安装为 Windows 服务 并启动 (注意 : 需要管理员权限 !!!) .

```
.\bin\mysqld.exe install 服务名称 (不提供则默认为 'MySQL')
net start 服务名称
```

#### 8, 若要导出数据库, 请使用 `mysqldump` 工具, 命令如下 .

```
.\bin\mysqldump.exe 数据库名称 --result-file="导出的脚本.sql" -u root -p
Enter password: 登录密码
``` 

备注：

- MySQL 服务器需要 [Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170) .

  您可以直接下载安装, 或者将 `lib` 目录下的 `*.dll` 复制到 `.\bin` 目录下 .

- 完整版 [MySQL 安装指南](https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/windows-install-archive.html) .


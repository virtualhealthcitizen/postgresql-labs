### **Login to postgres and launch psql**

```shell
sudo -u postgres psql
```

(First enter the sudo password, then the postgres password.)

![01.png](img/01.png)

You can also specify both the `-U` and `-W` flags:

```shell
psql -U postgres -W
```

- The `-U` flag stands for the user
- The `-W` flag option requires you to provide the password
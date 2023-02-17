### **Log in to postgres and launch psql**

#### Using the terminal

```shell
sudo -u postgres psql
```

If using the above command: First enter the sudo password, then the postgres password.

If this is your first time using PostgreSQL, or you haven't used it for a while and are re-familiarizing yourself, keep the credentials simple:

- User: `postgres`
- Password: `postgres`

<img src="img/01.png" width="500" />

You can also specify both the `-U` and `-W` flags:

```shell
psql -U postgres -W
```

<img src="img/09.png" width="260" />


- The `-U` flag stands for the user
- The `-W` flag option requires you to provide the password

#### Using pgAdmin

Open the pgAdmin application and enter the user password.

<img src="img/06.png" width="500" />

Expand **Servers** in the **Browser** menu and enter the password when prompted.

<img src="img/07.png" width="500" />

To connect to one of the databases shown in the **Browser** menu, select (left-click) a database.

<img src="img/08.png" width="200" />

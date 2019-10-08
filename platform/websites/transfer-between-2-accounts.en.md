+++
title = "How To internally transfer a website"
menuTitle = "Internal website's transfer"
date = 2019-10-08T13:53:19+02:00
layout = "howto"
weight = 10
draft = false
+++

This article explains how move a website in another alwaysdata account.

You need to have **appropriate permissions** on original et destination accounts to proceed the transfer.

To do it, we will use the [SSH access]() rather than FTP which requires to locally repatriate the files to then transfer them to the destination account.
In our example, we consider following information:

- Original account name: _foo_
- Destination account name: _bar_
- Original database name: _foo\_base_
- Destination database name: _bar\_base_
- The website is located in the _~/www/_ directory.
- We use [SSH]() and databases default users. Those created at the account creation (for example, _foo_ for the _foo_ account and _bar_ for the _bar_ account).


## 1. Files copy

We use the [scp](https://linux.die.net/man/1/scp "scp") command after [log in SSH]() on the **destination** account.

```
bar@ssh:~$ scp -r foo@ssh-foo.alwaysdata.net:/home/foo/www/* ~/www/
```

## 2. Database import

This stage is only required if your website is connected to a [database]().
Beforehand you need to have created the database on the _destination_ account.

For MySQL:

```
bar@ssh:~$ mysqldump -u foo -p -h mysql-foo.alwaysdata.net foo_base > foo_base.sql
bar@ssh:~$ mysql -h mysql-bar.alwaysdata.net -u bar -p bar_base < foo_base.sql
bar@ssh:~$ rm foo_base.sql
```

For PostgreSQL:

```
bar@ssh:~$ pg_dump -U foo -W -h postgresql-foo.alwaysdata.net foo_base > foo_base.sql
bar@ssh:~$ psql -h postgresql-bar.alwaysdata.net -U bar -W -d bar_base < foo_base.sql
bar@ssh:~$ rm foo_base.sql
```

**Previously modify the configuration file of the copied website to point on the newly imported database.**

 
## 3. Addresses relocation

It only remains to move addresses that join the website and their autogenerated certificate.
Go on the **Web > Sites** section of the original account, choose the **Transfer to another account** action and follow steps.

`/etc/shadow` is a text file that contains information about the system’s users' passwords. It is [owned](https://linuxize.com/post/chmod-command-in-linux/) by user root and group shadow, and has 640 [permissions](https://linuxize.com/post/linux-chown-command/) .

## `/etc/shadow` Format

The `/etc/shadow` file contains one entry per line, each representing a user account. You can view the contents of the file, with a [text editor](https://linuxize.com/post/how-to-use-nano-text-editor/) or a command such as [`cat`](https://linuxize.com/post/linux-cat-command/) :

```
sudo cat /etc/shadow
```

Typically, the first line describes the root user, followed by the system and normal user accounts. New entries are appended at the end of the file.

Each line of the `/etc/shadow` file contains nine comma-separated fields:

```txt
mark:$6$.n.:17736:0:99999:7:::
[--] [----] [---] - [---] ----
|      |      |   |   |   |||+-----------> 9. Unused
|      |      |   |   |   ||+------------> 8. Expiration date
|      |      |   |   |   |+-------------> 7. Inactivity period
|      |      |   |   |   +--------------> 6. Warning period
|      |      |   |   +------------------> 5. Maximum password age
|      |      |   +----------------------> 4. Minimum password age
|      |      +--------------------------> 3. Last password change
|      +---------------------------------> 2. Encrypted Password
+----------------------------------------> 1. Username
```

1.  Username. The string you type when you log into the system. The user account that exist on the system.
    
2.  Encrypted Password. The password is using the `$type$salt$hashed` format. `$type` is the method cryptographic hash algorithm and can have the following values:
    
    -   `$1$` – MD5
    -   `$2a$` – Blowfish
    -   `$2y$` – Eksblowfish
    -   `$5$` – SHA-256
    -   `$6$` – SHA-512
    
    If the password field contains an asterisk (`*`) or exclamation point (`!`), the user will not be able to login to the system using password authentication. Other login methods like [key-based authentication](https://linuxize.com/post/how-to-setup-passwordless-ssh-login/) or [switching to the user](https://linuxize.com/post/su-command-in-linux/) are still allowed.
    
    In older Linux systems, the user’s encrypted password was stored in the `/etc/passwd` file.
    
3.  Last password change. This is the date when the password was last changed. The umber of days is counted since January 1, 1970 (epoch date).
    
4.  Minimum password age. The number of days that must pass before the user password can be changed. Typically it is set to zero, which means that there is no minimum password age.
    
5.  Maximum password age. The number of days after the user password must be changed. By default, this number is set to `99999`.
    
6.  Warning period. The number of days before the password expires during which the user is warned that the password must be changed.
    
7.  Inactivity period. The number of days after the user password expires before the user account is disabled. Typically this field is empty.
    
8.  Expiration date. The date when the account was disabled. It is represented as an epoch date.
    
9.  Unused. This field is ignored. It is reserved for future use.
    

The `/etc/shadow` file should not be edited by hand unless you know what you are doing. Always use a command that is designed for the purpose. For example, to change a user password, use the [`passwd`](https://linuxize.com/post/how-to-change-user-password-in-linux/) command, and to change the password aging information, use the `chage` command.
# Day 1 - Create User with Non-Interactive Shell

## Task Description

To accommodate the backup agent tool's specifications, the system admin team at xFusionCorp Industries requires the creation of a user with a non-interactive shell.

**Task**: Create a user named `mariyam` with a non-interactive shell on **App Server 3**.

---

## Steps to Solve

### 1. SSH into App Server 3

You can connect to the server using the **Server Name**, **Hostname**, or **IP Address**, depending on what's provided or configured in your environment.

```bash
ssh username@<server-name>
ssh username@<hostname>
ssh username@<ip-address>
```

Example from the task:
```bash
ssh banner@172.16.238.12
```

Enter the password when prompted.

---

### 2. Create the user with a non-interactive shell

Use the `adduser` command with the `-s` option to set the shell as `/sbin/nologin`:

```bash
sudo adduser mariyam -s /sbin/nologin
```

---

### 3. Verify the user shell

Check the user entry in `/etc/passwd`:

```bash
grep mariyam /etc/passwd
```

Expected output:
```
mariyam:x:1002:1002::/home/mariyam:/sbin/nologin
```

This confirms that the user was created and cannot access a shell session.

---

## Explanation: Why a Non-Interactive Shell?

- A **regular user** has a default shell like `/bin/bash`, allowing login and command execution.
- A **non-interactive user** with `/sbin/nologin` cannot open a shell session.
- This is used for system or service accounts where shell access is unnecessary or a potential security risk (e.g., for running background processes like a backup agent).

---

## Further Reading

- [Gist: Linux User with Non-Interactive Shell - Practical Example](https://gist.github.com/AbdullahGhani1/607b952ab75b47820bc3e763008301bb)
- [Unix SE: `/sbin/nologin` vs `/bin/false`](https://unix.stackexchange.com/questions/10852/whats-the-difference-between-sbin-nologin-and-bin-false)
- [Unix SE: Creating a User Without Shell Access](https://unix.stackexchange.com/questions/4676/creating-a-user-who-cannot-get-an-interactive-shell)
- [Medium: Create Linux User with Non-Interactive Shell](https://medium.com/@ikunalsingh/create-linux-user-with-non-interactive-shell-332c91cad6ff)

---

**Task completed.**

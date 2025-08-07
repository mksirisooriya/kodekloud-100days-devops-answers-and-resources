# Day 2 – Create Temporary User with Expiry Date

## Task Description

As part of a temporary assignment to the Nautilus project, a developer named `john` requires access for a limited duration. To ensure proper access management, a temporary user account with an **expiry date** must be created.

**Task**:  
Create a user named `john` on **App Server 3** in Stratos Datacenter.  
Set the **account expiry date** to `2024-04-15`, and make sure the username is in **lowercase**.

---

## Steps to Solve

### 1. SSH into App Server 3

Connect using the server name, hostname, or IP:

```bash
ssh banner@stapp03
```

Enter the password when prompted.

---

### 2. Check if the user already exists

```bash
sudo id john
```

If you see:
```
id: ‘john’: no such user
```
…then proceed to create the user.

---

### 3. Create the user

```bash
sudo adduser john
```

---

### 4. Set the account expiry date

Switch to root if needed:

```bash
sudo su -
```

Set the expiry date:

```bash
chage -E 2024-04-15 john
```

You can verify the account settings:

```bash
chage -l john
```

Expected output should include:

```
Account expires : Apr 15, 2024
```

---

## Explanation

- The `adduser` command is a friendlier wrapper around `useradd`, automatically creating home directories and prompting for user details.
- The `chage` command is used to manage password and account expiry details.
- Setting an expiry date ensures temporary users are **automatically disabled** after the specified date, helping with **access control** and **security**.

---

## Further Reading

- [AskUbuntu: Difference between `adduser` and `useradd`](https://askubuntu.com/questions/345974/what-is-the-difference-between-adduser-and-useradd)
- [Reddit: Difference between `sudo su` and `sudo -s`](https://www.reddit.com/r/linux4noobs/comments/143aw0g/difference_between_sudo_su_and_sudo_su/)

---

**Task completed.**

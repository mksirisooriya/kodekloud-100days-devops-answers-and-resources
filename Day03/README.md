# Day 3 – Disable Direct SSH Root Login

## Task Description

Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.  

**Task**: Disable direct SSH root login on **all app servers** within the Stratos Datacenter.

---

## Steps to Solve

### 1. SSH into each app server

Use the provided usernames and connect to each server one by one. You can use server name, hostname, or IP address.

```bash
ssh tony@stapp01
ssh steve@stapp02
ssh banner@stapp03
```

Enter the password when prompted.

---

### 2. Edit the SSH configuration file

On **each** app server, open the SSH daemon configuration file:

```bash
sudo vi /etc/ssh/sshd_config
```

---

### 3. Locate and update the root login setting

- Search for the line:
  ```
  #PermitRootLogin yes
  ```
- Uncomment it (remove `#` if present) and change `yes` to `no`:
  ```
  PermitRootLogin no
  ```

---

### 4. How to Use Vim to Edit and Save

1. **Enter Insert mode to make changes**:  
   - Press `i` to insert text at the current cursor position.  
   - Press `a` to insert text after the current cursor position.  
   - Press `o` to insert text on a new line below the current one.  
   Once in Insert mode, you can type and edit normally. The bottom of the screen will show `-- INSERT --`.

2. **Return to Normal mode**:  
   - Press `Esc` to exit Insert mode.

3. **Save and quit**:  
   - Type `:` to enter Command-line mode.  
   - Then type one of the following and press `Enter`:
     - `wq` → write (save) and quit  
       ```
       :wq
       ```
     - `x` → save and exit (same as `wq`)  
       ```
       :x
       ```
   - Shortcut: `Shift + ZZ` (press Shift and Z twice) from Normal mode.

---

### 5. Restart the SSH service

After saving changes, restart the SSH daemon on each server:

```bash
sudo systemctl restart sshd
```

---

## Why This Is Important

- Disabling direct root SSH login reduces the risk of brute-force attacks.
- Administrators should log in with a normal user account and then escalate privileges using `sudo` if needed.
- This is a common best practice in system hardening.

---

**Task completed.**

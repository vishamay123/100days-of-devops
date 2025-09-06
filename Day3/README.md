

````markdown
# 🚀 Task: Disable Direct SSH Root Login on All App Servers

## 📌 Overview
For security best practices, it is strongly recommended to **disable direct SSH login for the root user**.  
Instead, administrators should log in with a normal user account and then use `sudo` or `su` for root privileges.  

This prevents brute-force attacks on the root account and enforces better access control.

---

## 🔹 Steps to Disable Root Login via SSH

### 1. Open the SSH configuration file
```bash
sudo nano /etc/ssh/sshd_config
````

### 2. Locate the following line

```
#PermitRootLogin yes
```

### 3. Modify it to

```
PermitRootLogin no
```

👉 This disables SSH access for the `root` user.

### 4. Restart SSH service

```bash
sudo systemctl restart sshd
```

---

## 🔹 Verification

1. Try logging in as root:

   ```bash
   ssh root@server-ip
   ```

   You should see:

   ```
   Permission denied
   ```

2. Log in as a normal user:

   ```bash
   ssh appuser@server-ip
   ```

3. Use `sudo` for admin tasks:

   ```bash
   sudo -i
   ```

---

## 🔹 Why Disable Root Login?

* **Security**: Prevents attackers from directly guessing the root password.
* **Accountability**: Ensures each user logs in with their own account.
* **Best Practice**: Enforces the principle of least privilege.

---

## 🔹 Alternative Secure Methods

* Use **key-based authentication** instead of passwords.
* Allow `root` login only via console, not SSH.
* Set up a **jump server** for admin access.

---

## ✅ Summary

* Edited `/etc/ssh/sshd_config`
* Set `PermitRootLogin no`
* Restarted SSH service
* Verified root login is blocked

Now, all app servers are secured against direct SSH root access. 🔒

```

---

Do you also want me to include **steps for disabling SSH password login (forcing key-based auth)** in the same README, since it’s often done together with root login hardening?
```


````markdown
# 🚀 Day 2 Challenge: Temporary User Setup with Expiry

## 📌 Overview
In this challenge, we created a **temporary user** in Linux that automatically expires after a certain date.  
This is useful for **students, interns, testers, or contractors** who should only have access for a limited time.  

---

## 🔹 Creating a Temporary User

You can use the `useradd` command with the `-e` option to set an **expiry date**.

### Example
```bash
sudo useradd -m -s /bin/bash -e 2025-09-10 tempuser
````

* `-m` → Creates a home directory for the user
* `-s /bin/bash` → Assigns bash as the login shell
* `-e 2025-09-10` → Sets the expiry date (YYYY-MM-DD)
* `tempuser` → The username

After this date, the account will **expire automatically** and the user cannot log in.

---

## 🔹 Verify User Expiry

To check the expiry date of a user:

```bash
sudo chage -l tempuser
```

Example output:

```
Last password change                                    : Sep 04, 2025
Password expires                                        : never
Account expires                                         : Sep 10, 2025
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
```

---

## 🔹 Related Useful Topics

### 1. Why Use Temporary Users?

* Security → Prevents forgotten accounts from being exploited
* Time-bound access → Perfect for guests, interns, or external collaborators
* Easy management → No need to manually delete users later

---

### 2. Difference Between Locking vs Expiring a User

* **Locking a user**: Temporarily disables login (`passwd -l username`), but can be unlocked.
* **Expiring a user**: Sets a permanent expiry date after which login is not possible unless expiry is updated.

---

### 3. Modify Expiry Date

Change expiry for an existing user:

```bash
sudo usermod -e 2025-12-31 tempuser
```

---

### 4. Delete User After Expiry (Optional Cleanup)

If you want to remove the user completely after expiry:

```bash
sudo userdel -r tempuser
```

(`-r` removes home directory too)

---

## ✅ Summary

* `useradd -e DATE username` → Create temporary user
* `chage -l username` → Check expiry date
* `usermod -e DATE username` → Change expiry date
* Temporary users are a **best practice** for limited-time access and security.

---

```


- Why use temporary users  
- Locking vs Expiring  
- Modifying expiry date  
- Cleanup after expiry  

Would you like me to also create a **Day 2 → Day N style README series template** so you can use the same format for all your daily Linux challenges?
```

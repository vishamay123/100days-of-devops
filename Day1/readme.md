Here’s a clean `README.md` file for you:

````markdown
# Linux Shells and User Management

## 🔹 Interactive vs Non-Interactive Shell

### Interactive Shell
- A shell where the **user types commands** and gets immediate responses.
- It displays a **prompt** (`$`, `#`) and waits for user input.
- Example:
  ```bash
  $ ls
  Documents  Downloads  Pictures
````

### Non-Interactive Shell

* A shell that runs commands **without waiting for user input**.
* Commonly used in **scripts, cron jobs, and automation**.
* Example:

  ```bash
  echo "echo Hello" | bash
  ```

  Output:

  ```
  Hello
  ```

---

## 🔹 Creating a Non-Interactive Shell User

In Linux, you can make a user **non-interactive** by assigning them a shell like `/sbin/false` or `/usr/sbin/nologin`.

Example:

```bash
sudo useradd -s /sbin/false yusuf
```

* `yusuf` = username
* `-s /sbin/false` = sets the login shell to `/sbin/false`, which immediately exits.
* Result: The user **exists** but **cannot log in** interactively.

---

## 🔹 Common `useradd` Options (Short Explanation)

| Option         | Meaning                                                  |
| -------------- | -------------------------------------------------------- |
| `-c "COMMENT"` | Add a description for the user                           |
| `-d DIR`       | Set custom home directory                                |
| `-m`           | Create home directory                                    |
| `-M`           | Do not create home directory                             |
| `-s SHELL`     | Set login shell (e.g., `/bin/bash`, `/sbin/false`)       |
| `-u UID`       | Assign a custom user ID                                  |
| `-g GROUP`     | Set primary group                                        |
| `-G g1,g2`     | Add user to extra groups                                 |
| `-N`           | Don’t create group with same name as user                |
| `-r`           | Create a system account (for services)                   |
| `-e DATE`      | Set account expiration date                              |
| `-f DAYS`      | Days after password expiry before disabling              |
| `-p PASSWORD`  | Set encrypted password (not recommended directly)        |
| `-k DIR`       | Copy files from skeleton directory (default `/etc/skel`) |
| `-o`           | Allow duplicate UID (not recommended)                    |

---

## 🔹 Example Usage

1. Create a user with a home directory and bash shell:

   ```bash
   sudo useradd -m -s /bin/bash alice
   ```

2. Create a non-interactive service account:

   ```bash
   sudo useradd -r -s /usr/sbin/nologin nginx
   ```

3. Create a user that expires on Dec 31, 2025:

   ```bash
   sudo useradd -m -e 2025-12-31 student1
   ```

---

✅ Don’t forget to set a password after creating a user:

```bash
sudo passwd username
```

```

---



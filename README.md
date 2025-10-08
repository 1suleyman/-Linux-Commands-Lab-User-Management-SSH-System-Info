# 🐧 Linux Commands Lab – User Management, SSH & System Info

In this lab, I practiced fundamental Linux commands to identify users, switch accounts, use SSH for remote access, explore system directories, and gather OS information. I also learned to download files via the command line and inspect privilege-restricted directories using `sudo`.

---

## 📋 Lab Overview

**Goal:**

* Strengthen understanding of user management commands
* Practice privilege escalation and file access under `/root`
* Use SSH to connect between servers
* Learn methods to download files using `wget` or `curl`
* Retrieve Linux OS and version details from system files

**Learning Outcomes:**

* Identify the current user and user ID
* Switch users using `su`
* SSH into remote servers with specific usernames
* Use `sudo` to list protected directories
* Download files from the internet
* Locate and read OS release information

---

## 🛠 Step-by-Step Journey

### **Step 1: Identify Current User**

**Task:** Check which user is currently logged in.

```bash
whoami
```

**Output:**

```
thor
```

✅ Confirms that the active user is **thor**.

---

### **Step 2: Check User ID**

**Task:** Display the UID, GID, and group memberships for the current user.

```bash
id
```

**Output Example:**

```
uid=1001(thor) gid=1001(thor) groups=1001(thor)
```

✅ The **user ID (UID)** of Thor is **1001**.

---

### **Step 3: Switch to Another User**

**Task:** Switch to the `ansible` user account.

```bash
su ansible
```

Explanation:

* `su` = “switch user” command.
* Prompts for the target user’s password.

✅ Switched successfully.

---

### **Step 4: SSH into Another Server**

**Task:** Log into a remote server with IP `172.16.238.3` as the user `thor`.

```bash
ssh thor@172.16.238.3
```

✅ Establishes a secure shell connection to the target host.

---

### **Step 5: View Files Under the Root Directory**

**Task:** List files in `/root` (requires elevated privileges).

```bash
sudo ls /root
```

**Output:**

```
anaconda-ks.cfg
```

✅ File visible only with `sudo` since `/root` is restricted to the root user.

---

### **Step 6: Identify Commands for Downloading Files**

**Question:** Which commands can download files over the internet?

✅ **Correct options:**

* `curl`
* `wget`
  ❌ `ping` does *not* download files.

---

### **Step 7: Download a File to a Target Directory**

**Task:** Download `dummy.pdf` to `/home/thor`.

```bash
wget -O /home/thor/dummy.pdf <URL>
```

Alternative:

```bash
curl -o /home/thor/dummy.pdf <URL>
```

✅ File successfully downloaded and saved in `/home/thor`.

---

### **Step 8: Locate OS Information Files**

**Task:** Identify where Linux OS information is stored.

```bash
ls /etc/*release*
```

✅ OS details are stored in files like `/etc/os-release` and `/etc/centos-release`.

---

### **Step 9: Identify the Operating System**

**Task:** Display OS information.

```bash
sudo cat /etc/*release*
```

**Output Example:**

```
NAME="CentOS Stream"
VERSION="9"
```

✅ The operating system is **CentOS**.

---

### **Step 10: Determine the OS Version**

**Task:** Verify version number from the same file.

```bash
cat /etc/os-release | grep VERSION_ID
```

**Output:**

```
VERSION_ID="9"
```

✅ CentOS version **9** confirmed.

---

## ✅ Key Commands Summary

| Task                         | Command                           |
| ---------------------------- | --------------------------------- |
| Show current user            | `whoami`                          |
| Show user ID & groups        | `id`                              |
| Switch user                  | `su <username>`                   |
| SSH into remote server       | `ssh <user>@<ip>`                 |
| List files in root directory | `sudo ls /root`                   |
| Download file (wget)         | `wget -O <path/filename> <url>`   |
| Download file (curl)         | `curl -o <path/filename> <url>`   |
| Show OS info files           | `ls /etc/*release*`               |
| Display OS name & version    | `cat /etc/*release*`              |
| Find version only            | `grep VERSION_ID /etc/os-release` |

---

## 💡 Notes / Tips

* `whoami` is a quick way to confirm your current login identity.
* `id` provides both user and group information in one command.
* Access to `/root` requires `sudo` privileges.
* Always use `wget` or `curl` for reliable file downloads; `ping` only tests connectivity.
* The `*release*` files under `/etc` are standard across most Linux distributions.
* `su` switches users temporarily without logging out.

---

## ✅ References

* [Linux `whoami` and `id` Commands](https://www.geeksforgeeks.org/id-command-in-linux-with-examples/)
* [Using SSH on Linux](https://man7.org/linux/man-pages/man1/ssh.1.html)
* [Wget and Curl Documentation](https://www.gnu.org/software/wget/manual/wget.html)
* [Understanding `/etc/os-release`](https://www.freedesktop.org/software/systemd/man/os-release.html)

# Ubuntu Server Quick Start Guide (After Boot)

---

## On the SERVER

### 1. Check IP Address

```bash
ip a
```

Look for:

```
inet 192.168.x.x
```

---

### 2. Ensure SSH is Installed & Running

```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
```

Check:

```bash
sudo systemctl status ssh
```

---

### 3. Disable Sleep

```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

---

### 4. Prevent Sleep on Lid Close (Optional)

```bash
sudo vim /etc/systemd/logind.conf
```

Set:

```
HandleLidSwitch=ignore
```

Then:

```bash
sudo systemctl restart systemd-logind
```

---

### 5. Increase Terminal Font Size (Server Console)

```bash
sudo dpkg-reconfigure console-setup
```

Choose:

* Encoding: UTF-8
* Font: Terminus
* Size: 16x32

Apply:

```bash
sudo setupcon
```

---

### 6. Create Working Directory

```bash
mkdir -p ~/projects
cd ~/projects
```

---

## On the Client

### 1. Connect via SSH

```bash
ssh username@192.168.x.x
```

---

### 2. Use VS Code Remote SSH

* Install extension: Remote - SSH
* Connect:

```
ssh username@192.168.x.x
```

* Open:

```
/home/username/projects
```

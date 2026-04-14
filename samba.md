# Samba Setup

## 1. Install Samba

```bash
sudo apt update
sudo apt install samba -y
```

---

## 2. Create Linux User

```bash
sudo adduser smbuser
```

---

## 3. Create Samba User

```bash
sudo smbpasswd -a smbuser
sudo smbpasswd -e smbuser
```

---

## 4. Configure Share

```bash
sudo vim /etc/samba/smb.conf
```

Add:

```ini
[SharedFolder]
   path = /home/gowtham
   valid users = smbuser
   read only = no
   browsable = yes
   writable = yes
```

---

## 5. Set Permissions

```bash
sudo chown -R smbuser:smbuser /home/gowtham
sudo chmod -R 775 /home/gowtham
```

---

## 6. Restart Samba

```bash
sudo systemctl restart smbd
```

---

## 7. Allow Firewall

```bash
sudo ufw allow samba
```

---

## 8. Access from Windows

```
\\192.168.x.x\SharedFolder
```

Login:

* Username: smbuser
* Password: (your smb password)

---

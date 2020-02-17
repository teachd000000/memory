# SSH를 사용하여 EC2 인스턴스에 로그인할 때 키 페어(.pem) 대신 암호 로그인하려면?


## 1. SSH 클라이언트에서 EC2 인스턴스에 로그인한다.

```
$ ssh -i "sample.pem" root@XXX.XXX.XXX.XXX
```

---

## 2. 사용자의 암호를 설정합니다. 

---

```
$ sudo passwd teachd000000
Changing password for user teachd000000.
New password:
Retype new password:
```

## 3. /etc/ssh/sshd_config 파일에서 PasswordAuthentication 설정을 변경한다.

---

```
# PasswordAuthentication no
PasswordAuthentication yes
```

## 4. SSH 서비스를 다시 시작합니다.

---

```
$ sudo service sshd restart
```

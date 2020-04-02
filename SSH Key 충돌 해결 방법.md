# SSH Key 충돌 해결 방법


## 문제 상황

ssh로 원격 서버에 접속하는 과정에서 아래의 경고 메시지가 노출되고 접속할 수 없는 문제가 발생

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Please contact your system administrator.
Add correct host key in /home/username/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/username/.ssh/known_hosts:41
ECDSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
```

---

## 해결 방법

- 기존에 접속하던 시스템의 변경으로 인해, 원격 시스템의 고유값이 기존에 저장된 값과 다를 때 발생 
- /home/username/.ssh/known_hosts 파일에 들어가서 키 값이 저장된 라인을 삭제 후, 재접속을 시도



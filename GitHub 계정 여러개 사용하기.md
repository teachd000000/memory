# GitHub 계정 여러개 사용하기

## 순서
1. 새로운 ssh key 를 만든다.
2. 깃허브 계정에 ssh key 를 추가한다.
3. 터미널에서 ssh key 를 추가한다.
4. Config 파일 생성하기
5. 끝

## 1. 새로운 ssh key 를 만든다.

#### 깃허브 개인 계정 이메일 주소로 ssh 키를 생성한다.

~~~
$ ssh-keygen -t rsa -C 'second@gmail.com'
~~~

~~~
Generating public/private rsa key pair.
Enter a file in which to save the key (/Users/yourusername/.ssh/id_rsa) : id_rsa_second
~~~

~~~
$ ~/.ssh

$ ls

id_rsa.pub    id_rsa_second.pub    id_rsa    id_rsa_second    known_hosts
~~~

## 2. 깃허브 계정에 ssh key 를 추가한다.

#### 위에서 생성한 ssh 키를 깃허브 계정에 추가한다.

1. 깃허브에 second@gmail.com 으로 로그인한다.
2. Edit profile -> SSH and GPG keys -> New SSH key 를 클릭한다.
3. Title 에는 구분을 위한 이름을, Key 에는 cat 명령어의 결과를 복사해서 넣는다.

~~~
$ cat id_rsa_second.pub

ssh-rsa AAAAB3Nza... second@gmail.com
~~~


## 3. 터미널에서 ssh key 를 추가한다.

~~~
# 기존에 등록된 계정 삭제
$ ssh-add -D

# 첫벉째 계정 등록
$ ssh-add ~/.ssh/id_rsa			

# 두번째 계정 등록
$ ssh-add ~/.ssh/id_rsa_second	
~~~

## 4. Config 파일 생성하기

#### 로컬에서 작업한 내용을 깃허브로 푸시할 때, 어떤 키를 참조할 것인지 결정하는 Config 파일을 생헝한다.

~~~
# 첫번째 계정
Host github.com-first
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa

# 두번째 계정
Host github.com-second
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_second
~~~

## 5. 끝

~~~
$ ssh -T git@github.com-first
Hi first! You've successfully authenticated, but GitHub does not provide shell access.

$ ssh -T git@github.com-second
Hi second! You've successfully authenticated, but GitHub does not provide shell access.
~~~

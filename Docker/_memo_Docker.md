# Docker
## Links
### Mac OS X에서 docker 설치하기
    http://www.devblog.kr/r/8y0gFPAvJ2Y9JCGYZ9qoZY8my3GyFTYJ42IJjcgOEPF
    https://docs.docker.com/engine/installation/mac/
### Docker 기본 사용법
    http://pyrasis.com/Docker/Docker-HOWTO
    http://zeroturnaround.com/wp-content/uploads/2016/03/Docker-cheat-sheet-by-RebelLabs.png
### 동영상
    * 서버 운영자가 꼭 알아야 할 Docker(김훈민) :  https://www.youtube.com/watch?v=mECbDs9nPnM
#### Book
    http://pyrasis.com/book/DockerForTheReallyImpatient/
# Install
- link : https://docs.docker.com/engine/installation/

## Mac
```
brew install docker
```
## centos7
1. yum install docker -y
2. service docker start
3. chkconfig docker on


## Ubuntu - easy
    curl -s https://get.docker.com/ | sudo sh

## Ubuntu - hard
apt update
apt install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
apt update
apt-cache policy docker-ce
apt install -y docker-ce
apt install -y systemd
systemctl status docker

### 일반 유저 Docker 가능하게 하기
sudo groupadd docker
sudo usermod -aG docker $(whoami)
sudo chown -R root:docker /var/run/docker.sock
sudo chmod 777 /var/run/docker.sock
docker run --name h1 hello-world
docker rm -f h1
docker rmi hello-world
### 일반 유저 Docker 가능하게 하기2
    sudo gpasswd -a ${USER} docker
    sudo service docker restart

### Docker Image load
    docker load -i bi_deeplearning.docker
    docker load -i opencv3

## Windows
### Winodws 10 pro버전이상 install
- Docker for window로 설치
- link : https://docs.docker.com/docker-for-windows/
### Windows 10 Home 이전 버전 설치
- Docker Toolbox로 설치
- link : https://github.com/docker/toolbox/releases

#### Window용 Docker사용시 주의 사항
* **주의** : Windows보안 레벨이 일반 이상인 경우 docker창을 실행시킬때 마우스 오른쪽 버튼으로 클릭해서 "관리자 권한으로 실행"을 선택해서 실행할 것.
*/usr/share/nginx/html
#### Docker-toolbox사용시 주의 사항
* **주의1** : "folder"라는 이름의 폴더를 윈도우의 경우 내문서 자기 계정 하위 폴더에 위치시킨 상태에서 다음과 같이 루트 지정해야 함.  ... /c/Users/LeeKwangHyun/Folder:/home/admin -p 8000:8000 ..... 처럼 설정해야함
* **주의2** :  docker-machine ip default 명령을 통한 가상머신의 IP주소 확인후 해당 주소로 접속해야 함. DockertoolBox의 경우 가상머신을 사용하기 때문에 IP주소가 새롭게 부여됨
* **주의3** : Windows10 Pro에서 Docker for Windows사용시 sharefolder 사용시에는 따로 셋팅에서 등록해 줘야함.https://docs.docker.com/docker-for-windows/#docker-settings

## Setting
### 현재 계정을 docker 그룹에 포함
```bash
sudo usermod -aG docker ${USER}
sudo service docker restart
```


# docker-compose
## docker-compose info
* link : 도커 컴포즈를 활용하여 완벽한 개발 환경 구성하기 (컨테이너 시대의 Django 개발환경 구축하기) : https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose
## Command
### up
```
docker-compose up -d
```
* -d: 서비스 실행 후 콘솔로 빠져나옵니다. (docker run에서의 -d와 같습니다.)
* --force-recreate: 컨테이너를 지우고 새로 만듭니다.
* --build: 서비스 시작 전 이미지를 새로 만듭니다.

### rm
```
docker-compose rm -f
```
### down
* --volume: 볼륨까지 삭제합니다.

### ps
* -q, --quiet          Only display IDs
* --services           Display services
* --filter KEY=VAL     Filter services by a property
* -a, --all            Show all stopped containers (including those created by the run command)

## Yaml Component
### version
### services
* Container
### image
### ports
### volumes
### environment
## Example1
```
version: '3.3'
services:
  u1:
    image: nginx
    ports:
      - "8888:80"
    restart: always
```

## Example2 : just syntax
```
services:
  container2:
    command:
      - bash
      - -c
      - |
        /wait-for-it.sh db:5432 -t 10
        python manage.py runserver 0:8000
```

## Example 3
```
mkdir html
echo "<h1>hi</h1>" > html/index.html
echo "
---
version: '3'

services:
  t1:
    image: nginx
    volumes:
      - ./html:/usr/share/nginx/html/
    ports:
      - 8888:80
    restart: always
">docker-compose.yml
docker-compose up -d
open http://127.0.0.1:8888
```

## Example 4
```
echo "
version: '3.3'

services:
   db:
     image: mysql:5.7
     volumes:
       - /Users/nowage/work-etc/docker/db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
       WORDPRESS_DB_NAME: wordpress
volumes:
    db_data: {}
" > docker-compose.yml

```
open http://127.0.0.1:8000



# docker-machine
## command
* docker-machine ip


## Docker toolbox : Machine Disk 용량 모자를 때 (NoSpace left )
```
docker-machine rm default
docker-machine create --driver virtualbox --virtualbox-disk-size "60000" default
docker-machine env default
```

# Command
## Machine repository Search & Pull
```
docker search <imageName>
docker pull <imageName>
docker images
```


## run
```
docker run -i -t --name <ContainerName> <imageName> /bin/bash

docker run -ti                --name <ContainerName> -v $home/storage /root/stoarge <imageName>
docker run                    --name <ContainerName> -d <imageName>
docker run -d  -p 2222:22     --name <ContainerName> -v $home/storage /root/stoarge <imageName>:0.1
docker run -d  -p 2222:22 -rm --name <ContainerName> -v $home/storage /root/stoarge <imageName>:0.1
```
- option
```
-d : detach
-i : interactive
-t : tty
-p : publish value(port)
-e : Set environment variables
--rm : 기존 컨테이너 지우기
--name : 컨테이너 이름
--restart="always"
--restart="on-failure:10"
```

* docker Terminal에서 나오기 :  ctl+p+q
    - exit로 나오면 start를 다시 해줘야 됨.


### run --restart
* https://blog.naver.com/foxrain93/220670672186
* by Option
```
--restart="always"
--restart="on-failure:10"
```
* by Systemd
* /etc/systemd/system/docker.service
```
[Unit]
Description=서비스 이름(ex. Nginx container)
Requires=docker.service
After=docker.service
[Service]
Restart=always
ExecStart=/usr/bin/docker start [컨테이너 이름]
ExecStop=/usr/bin/docker stop [컨테이너 이름]
[Install]
WantedBy=local.target
```

## ps
```
docker ps -a
```

### Filter
* Example
```
docker ps --filter publish=80/tcp
```
* Filter Options
| Filter   | Description                                                                                                                         |
|----------|------------------------------------------------------------------------------------------------------------------------------------|
| id       |Container’s ID                                                                                                                      |
| name     |Container’s name                                                                                                                    |
| label    |An arbitrary string representing either a key or a key-value pair. Expressed as <key> or <key>=<value>                              |
| exited   |An integer representing the container’s exit code. Only useful with --all.                                                          |
| status   |One of created restarting running removing paused exited or dead                                                                    |
| ancestor |Filters containers which share a given image as an ancestor. Expressed as <image-name>[:<tag>] <image id> or <image@digest>         |
| before   |or since Filters containers created before or after a given container ID or name                                                    |
| volume   |Filters running containers which have mounted a given volume or bind mount.                                                         |
| network  |Filters running containers connected to a given network.                                                                            |
| publish  |or expose   Filters containers which publish or expose a given port. Expressed as <port>[/<proto>] or <startport-endport>/[<proto>] |
| health   |Filters containers based on their healthcheck status. One of starting healthy unhealthy or none.                                    |
| isolation|Windows daemon only. One of default process or hyperv.                                                                              |
| is-task  |Filters containers that are a “task” for a service. Boolean option (true or false)                                                  |


### Format
* Example
```
docker ps  --format "table {{.ID}}\t{{.Mounts}}"
```
* Formats
|Placeholder |Description                                                                                   |
|------------|---------------------------------------------------------------------------------------------|
| .ID        |Container ID                                                                                  |
| .Image     |Image ID                                                                                      |
| .Command   |Quoted command                                                                                |
| .CreatedAt |Time when the container was created.                                                          |
| .RunningFor|Elapsed time since the container was started.                                                 |
| .Ports     |Exposed ports.                                                                                |
| .Status    |Container status.                                                                             |
| .Size      |Container disk size.                                                                          |
| .Names     |Container names.                                                                              |
| .Labels    |All labels assigned to the container.                                                         |
| .Label     |Value of a specific label for this container. For example '{{.Label "com.docker.swarm.cpu"}}'|
| .Mounts    |Names of the volumes mounted in this container.                                               |
| .Networks  |Names of the networks attached to this container.                                             |




## Container start/stop/restart/kill
```
docker start <ContainerName>
docker stop <ContainerName>
docker restart <ContainerName>
docker
```
### example
```
docker kill $(docker ps -q)
```

## atache/excute
```
docker attach <ContainerName>
docker exec <ContainerName> pwd
```

### example
```
docker exec -ti <ContainerName> do.sh
docker exec -u 0 -it <ContainerName> bash
```

## rm
```
docker rm <ContainerName>
docker rmi <imageName>
```
### example
```
docker rm $(docker ps -a -q)
          ← docker rm -f $(docker ps -a |awk 'BEGIN{FS="\ {2,}"}FNR>1{printf "%s\n", $NF}')
docker rmi $(docker images -q -f dangling=true)
          ← # docker rmi $(docker images|awk 'BEGIN{FS="\ {2,}"}FNR>1{printf "%s\n", $3}')
docker images

```
## cp
```
docker cp hello-nginx:/etc/nginx/nginx.conf ./
```

## Network
* Link는 obsolete 되었음
```
docker network create n1
docker rm -f u1
docker rm -f u2
docker run -it --name u1  --network n1 ubuntu
    apt update -y
    apt-get install -y iputils-ping
    ping u2                               ←  2
docker run -it --name u2  --network n1 ubuntu
    apt update -y
    apt install -y net-tools
    ifconfig                              ←  1
```



## Command
### up
```
docker-compose up -d
```
* -d: 서비스 실행 후 콘솔로 빠져나옵니다. (docker run에서의 -d와 같습니다.)
* --force-recreate: 컨테이너를 지우고 새로 만듭니다.
* --build: 서비스 시작 전 이미지를 새로 만듭니다.

### rm
```
docker-compose rm -f
```
### down
* --volume: 볼륨까지 삭제합니다.

### ps
* -q, --quiet          Only display IDs
* --services           Display services
* --filter KEY=VAL     Filter services by a property
* -a, --all            Show all stopped containers (including those created by the run command)


## history
```
docker history <imageName>
```
## log
* It is useful when docker is executed by -d option
```
docker logs -ft <ContainerName> >> /tmp/<ContainerName>.log &
```
## Version Control
```
docker commit -a "NamJungGu <nowage@gmail.com>" -m "add ip" <ContainerName> nowage/<imageName>:0.1
docker diff <ContainerName>
docker inspect <ContainerName>
```

## Login
* 주의 점 : https://hub.docker.com/settings/security → New Access Tokcken을 비번으로 할 것
```
docker login
```
## Push
* docker login 필요
```
docker push
```




# Job
## Get Docker host ip
* get base ip
```
ip -4 addr show docker0 | grep -Po 'inet \K[\d.]+'
# or
ip -4 addr show eth0 | grep -Po 'inet \K[\d.]+'
```
* may guest ip : 172.17.0.2
* use host ip  : 172.17.0.1


## Root login
```
docker exec -it --user root artifactory bash
```



## ifconfig & ping 가능하게
apt install -y net-tools
apt-get install -y iputils-ping


## 특수 문자 안 먹는 문제 해결
- kapeli Dash 작동안하는 문제를 해결함.
```
cat >> /etc/inputrc << EOF
set input-meta on
set output-meta on
set convert-meta off
EOF
```

## kapeli Dash 안될때 - Debian
### Build로 해결
* docker build 할때 아래 추가하면 간단하게 해결.
```
ENV LC_ALL en_US.UTF-8
```
### Run으로 해결
* 아래 옵션 추가
-e LC_ALL=C.UTF-8                        \

### 실행 중인 컨테이너
```
echo "export LC_ALL=C.UTF-8" >> /etc/bash.bashrc
bash
```

## kapeli Dash 안될때 - RedHat
### Build로 해결
* docker build 할때 아래 추가하면 간단하게 해결.
```
ENV LANG en_US.UTF-8
```
### Run으로 해결
* 아래 옵션 추가
-e LANG=en_US.UTF8                       \

### 실행 중인 컨테이너
```
echo "export LANG=en_US.UTF8" >> /etc/bash.bashrc
bash
```

* ubuntu와 비슷하나 LANG=en_US.UTF8


## Git-Bash 사용시
### Volume Mapping 주의
* ~/df 같은 방식 작동 안함.
* /c/Users/nowage/df 같은 방식도 작동 안함.
* 작동하는 경우
```
docker run -it --name u1 --rm -v c:/Users/nowage/df:/df ubuntu
docker run -it --name u1 --rm -v c:\\Users\\nowage\\df:/df ubuntu
docker run -it --name u1 --rm -v c:/Users/$USERNAME/df:/df ubuntu
docker run -it --name u1 --rm -v $USERPROFILE/df:/df ubuntu
```
## ssh 가능하게 하기
* Centos 용이며, make할때 추가는 것을 권장함.
* 단순히 추가 세션을 여는 것을 목적으로 한다면 "docker exec -it c명 bash"을 쓰는 것 권장

1. ssh Daemon 설치(Container)
```
yum -y update; yum clean all
yum -y install openssh-server passwd; yum clean all
mkdir /var/run/sshd
ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''
```
* 주의 : sshd 작동 잘 안할때는 config파일에서 key값 제거 수정
```
    vi /etc/ssh/sshd_config
        #HostKey /etc/ssh/ssh_host_ecdsa_key
        #HostKey /etc/ssh/ssh_host_ed25519_key
```

2. User추가(Container)
```
useradd nowage
echo 'nowage' | passwd --stdin root
echo 'nowage' | passwd --stdin nowage

```
3. Docker Commit
```
docker commit -a "Buss NamJungGu <nowage@gmail.com>" -m "added ssh" c1 nowage/centssh:0.1
```
4. 새로운 Container실행
```
docker run --entrypoint /usr/sbin/sshd -it --name=c5 -p 22:22 --rm -v /Users/nowage/df/:/root/df nowage/centssh:0.2 -D
```
5. 접속
```
ssh nowage@localhosts
```




# Tools
## dcs
* CLi mode dashboard for Docker
* link : https://github.com/goody80/docker_cli_dashboard
* Usage : https://asciinema.org/a/166084
* 설치
```
curl -sL bit.ly/dcs_ -o ./dcs
sudo chmod 755 ./dcs
sudo mv ./dcs /usr/bin/dcs
# macOS : sudo mv ./dcs /usr/local/bin/dcs
```

## Docker sshd 가능하게 하기[old]
참고 : https://github.com/CentOS/CentOS-Dockerfiles/blob/master/ssh/centos7/Dockerfile
```Dockerfile
FROM centos:centos7
MAINTAINER The CentOS Project <cloud-ops@centos.org>
RUN yum -y update; yum clean all
RUN yum -y install openssh-server passwd; yum clean all
ADD ./start.sh /start.sh
RUN mkdir /var/run/sshd
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''
RUN chmod 755 /start.sh
ENTRYPOINT ["/usr/sbin/sshd", "-D"]
```

```
#!/bin/bash

__create_user() {
# Create a user to SSH into as.
useradd user
SSH_USERPASS=newpass
echo -e "$SSH_USERPASS\n$SSH_USERPASS" | (passwd --stdin user)
echo ssh user password: $SSH_USERPASS
}
```

 Call all functions
```
__create_user
```

# Docker Build 시 문제
* (Windows버전 2019년 4월 30일 기준.)
```
SECURITY WARNING: You are building a Docker image from Windows against a non-Windows Docker host. All files and directories added to build context will have '-rwxr-xr-x' permissions. It is recommended to double check and reset permissions for sensitive files and directories.
```
* Docker에서 빌드하고 push하면 되겠죠...
```
docker rm -f d1;docker run --privileged --name some-docker -d --name d1  docker:dind
docker exec -it d1 sh
apk add git
git clone https://github.com/Finfra/dockers.git
cd dockers
docker build --rm -t nowage/ubuntu .
docker images
docker run -it --name u1 -e USER=nowage -e PASSWD=nowage nowage/ubuntu
su - nowage
```


## Pydoc에 접근하기
* Container에서 아래와 같이 pydoc실행
```
pydoc -n 0.0.0.0 -p  9900
```

# Docker 종합 연습문제
* Docker생성 전용 Container를 사용하는 경우
## 요건
* ubuntu image로 nginx image building
* image → dockerhub
* build script → github

## 1. Github Repository 만들기
* github에 docker build script를 저장할 레포지터리 만들기.
* github 페이지에서 README.md를 만들어요.
## 2. Clone
* local에서 위 1번의 레포지터리를 clone (현재 셋팅은 d1 container)
* 빈 레포지터리를 clone하는 이유는 init/remoteRepository등록이 귀찮아서.
* cf
```
docker rm -f d1;docker run --privileged -d --name d1  -v /c/Users/xx/df:/root/df nowage/docker
docker exec -it d1 sh
    apk add curl
    cd /root/df
    git clone https://github.com/Finfra/nginx
    cd nginx
```

## 3. docker build 스크립트 작성
* https://github.com/Finfra/dockers 참고
* vi 어려우신 분은 d1컨테이터를 Volume Mapping해서 다시 만들고, Sublime으로 스크립트 만드세요.
* "FROM ubuntu"
* "apt install -y nginx"
* cf
```
cat <<EOF> Dockerfile
FROM ubuntu
MAINTAINER The NamjungGu < nowage@gmail.com >
COPY ./start.sh /
RUN chmod 755 /start.sh
RUN /start.sh
VOLUME "/var/www/html"
EXPOSE 80
CMD nginx
CMD bash
EOF
cat <<EOF> start.sh
apt update -y
apt install -y nginx
chown -R www-data:www-data /var/www/html
EOF
```

## 4. docker build
* docker image를 생성
* cf
```
docker build --rm -t nowage/nginx .
```

## 5. test
* Docker run으로 Container만드세요.
* Browser 혹은 curl로 접속해 보세요
```
docker rm -f n1;docker run -it --name n1 -p 80:80 -v /root/df:/var/www/html nowage/nginx
  cd /var/www/html
  echo "<h1>hi</h1>">index.html
  exit
curl 127.0.0.1:80
```

## 6. docker image push
```
docker login
docker push nowage/nginx
```

## 7. dockerhub에서 description작성
* github link 포함시키세요.

## 8. Docker Build Script를 Github에 push
```
git config --global user.name "Steve J. South(NamJungGu) "
git config --global user.email "nowage@gmail.com"
git add -A
git commit -m "."
git push
```

## 9. 본인의 Sns에서 광고.


# Docker build
[](_memo_Docker_build.md)

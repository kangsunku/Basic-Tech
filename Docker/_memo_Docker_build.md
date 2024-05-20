

# Build
## 관련 파일
* Github : https://github.com/Finfra/dockers
  * 

## Dockerfile
|구문      |내용                                                                                |
|----------|------------------------------------------------------------------------------------|
|FROM      |FROM은 어떤 이미지를 기반으로 이미지를 생성할지 설정                                |
|MAINTAINER|이미지를 생성한 사람의 정보를 설정                                                  |
|RUN       |FROM에서 설정한 이미지 위에서 스크립트 혹은 명령을 실행                             |
|CMD       |컨테이너가 시작되었을 때 스크립트 혹은 명령을 실행                                  |
|ENTRYPOINT|컨테이너가 시작되었을 때 스크립트 혹은 명령을 실행                                  |
|EXPOSE    |호스트와 연결할 포트 번호를 설정                                                    |
|ENV       |환경 변수를 설정                                                                    |
|ADD       |파일을 이미지에 추가                                                                |
|COPY      |파일을 이미지에 추가합니다. (압축 파일을 추가할 때 압축을 해제하지 않음)            |
|VOLUME    |디렉터리의 내용을 컨테이너에 저장하지 않고 호스트에 저장하도록 설정                 |
|USER      |명령을 실행할 사용자 계정을 설정합니다.                                             |
|WORKDIR   |RUN, CMD, ENTRYPOINT의 명령이 실행될 디렉터리를 설정                                |
|ONBUILD   |생성한 이미지를 기반으로 다른 이미지가 생성될 때 명령을 실행(trigger)               |

# Build Example

# Build Issue
## Interactive mode 실행시
## Detach 모드 실행시
* 아래와 같이 CMD로 서비스 추가해 줄것.
```
FROM ubuntu
RUN apt update
RUN apt -y install nginx
CMD ["nginx", "-g", "daemon off;"]
```

```
미션 이름
내 컴퓨터에 개발자용 '작업실' 꾸미기
```
```
미션 목표
도커 설치 및 기본 점검
도커 기본 운영 명령 수행
권한 실습 및 증거 기록
컨테이너 실행 실습
기존 도커파일 기반 커스텀 이미지 제작
포트 매핑 및 접속 증거
도커 볼륨 영속성 검증
깃 설정 및 깃허브 연동
보안 및 개인정보 보호

보너스 과제
docker compose 기초
docker compose 멀티 컨테이너
compose 운영 명령어 습득
환경 변수 활용
github ssh 키 설정
(HTTPS 대신SSH 로 푸시가 가능하도록 키를 등록하고 동작 확인)
```
```
os 환경  macos
git 버전 
```jeonyeongjin05222811@c6r9s4 git-practice % git --version```
git version 2.53.0
```
```터미널 조작 로그 기록```
```현재 위치 확인 pwd 결과: /Users/jeonyeongjin05222811/git-practice```
```목록 확인(숨김 파일 포함) ls -al #- 뒤 옵션 a는 전부 보이게함, l은 세부사항, 수정 가능 여부 등 접근 권한 보임```
```````````````결과 ls -a # -l 길어서 제외```
```.		..		.git		README.md```
```빈 파일 만들기 touch [파일 이름] #이 파일 이름이 있으면 이 파일의 생성 시간 등이 나옴```
```

touch helo

```

```

디렉터리 생성 mkdir

```

```

mkdir rid

```
```

파일 지우기 rm, 디렉터리 지우기 rmdir

rm -r "디렉터리 이름" 으로도 지워짐 recursive(재귀적으로 하위 폴더를 다 지우기 때문에)

touch abd
rm abd
mkdir adbdf

```
```
rmdir 로그

jeonyeongjin05222811@c6r9s4 nginx-custom % mkdir df   
jeonyeongjin05222811@c6r9s4 nginx-custom % ls
df              Dockerfile      index.html
jeonyeongjin05222811@c6r9s4 nginx-custom % rmdir df 
jeonyeongjin05222811@c6r9s4 nginx-custom % ls
Dockerfile      index.html
jeonyeongjin05222811@c6r9s4 nginx-custom % 

rm 로그

eonyeongjin05222811@c6r9s4 nginx-custom % touch ad  
jeonyeongjin05222811@c6r9s4 nginx-custom % ls 
ad              Dockerfile      index.html
jeonyeongjin05222811@c6r9s4 nginx-custom % rm ad 
jeonyeongjin05222811@c6r9s4 nginx-custom % ls
Dockerfile      index.html
```
파일 이동/이름 바꾸기 mv

```

이름 바꾸기 mv [파일명] [바꿀 이름]

```

```

사용법: mv [파일명] [옮길 디렉터리]

```
mv helo rid

```

```

파일 복사 cp [복사할 파일 명] [복사할 위치]

```

```

cp helo rid

```

```

권한 확인법 ls -l

```

```

ex)jeonyeongjin05222811@c6r9s4 git-practice % ls -l 
total 16
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md

```
```
```권한 수정법 chmod```
```8진수로 표현, rwx순으로,1은 가능 0은 불가능 유저, 모든 사용자, 그룹```
```chmod 755 README.md```
```파일 수정 로그```
```jeonyeongjin05222811@c6r9s4 git-practice % ls 
README.md
jeonyeongjin05222811@c6r9s4 git-practice % touch a 
jeonyeongjin05222811@c6r9s4 git-practice % ls
a               README.md
jeonyeongjin05222811@c6r9s4 git-practice % ls -l
total 16
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811     0 Aug  3 18:20 a
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md
jeonyeongjin05222811@c6r9s4 git-practice % chmod 777 a 
jeonyeongjin05222811@c6r9s4 git-practice % ls -l
total 16
-rwxrwxrwx  1 jeonyeongjin05222811  jeonyeongjin05222811     0 Aug  3 18:20 a
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md
```디렉터리 수정 로그```
```jeonyeongjin05222811@c6r9s4 git-practice % mkdir b 
jeonyeongjin05222811@c6r9s4 git-practice % ls -l 
total 16
-rwxrwxrwx  1 jeonyeongjin05222811  jeonyeongjin05222811     0 Aug  3 18:20 a
drwxr-xr-x  2 jeonyeongjin05222811  jeonyeongjin05222811    64 Aug  3 18:22 b
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md
jeonyeongjin05222811@c6r9s4 git-practice % chmod 777 b 
jeonyeongjin05222811@c6r9s4 git-practice % ls -l 
total 16
-rwxrwxrwx  1 jeonyeongjin05222811  jeonyeongjin05222811     0 Aug  3 18:20 a
drwxrwxrwx  2 jeonyeongjin05222811  jeonyeongjin05222811    64 Aug  3 18:22 b
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md
jeonyeongjin05222811@c6r9s4 git-practice % ```


```docker installation & setting```
도커 버전 확인
커맨드
docker --version
결과
Docker version 28.5.2, build ecc6942
```
```
도커 인포
커맨드 docker info
```
```
docker info
Client:
 Version:    28.5.2
 Context:    orbstack
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.29.1
    Path:     /Users/jeonyeongjin05222811/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.40.3
    Path:     /Users/jeonyeongjin05222811/.docker/cli-plugins/docker-compose

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 28.5.2
 Storage Driver: overlay2
  Backing Filesystem: btrfs
  Supports d_type: true
  Using metacopy: false
  Native Overlay Diff: true
  userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 1c4457e00facac03ce1d75f7b6777a7a851e5c41
 runc version: d842d7719497cc3b774fd71620278ac9e17710e0
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.17.8-orbstack-00308-g8f9c941121b1
 Operating System: OrbStack
 OSType: linux
 Architecture: x86_64
 CPUs: 6
 Total Memory: 15.67GiB
 Name: orbstack
 ID: 3385d27c-7b1e-4d81-b68a-d8da9c7f9869
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: 192.168.97.0/24, Size: 24
   Base: 192.168.107.0/24, Size: 24
   Base: 192.168.117.0/24, Size: 24
   Base: 192.168.147.0/24, Size: 24
   Base: 192.168.148.0/24, Size: 24
   Base: 192.168.155.0/24, Size: 24
   Base: 192.168.156.0/24, Size: 24
   Base: 192.168.158.0/24, Size: 24
   Base: 192.168.163.0/24, Size: 24
   Base: 192.168.164.0/24, Size: 24
   Base: 192.168.165.0/24, Size: 24
   Base: 192.168.166.0/24, Size: 24
   Base: 192.168.167.0/24, Size: 24
   Base: 192.168.171.0/24, Size: 24
   Base: 192.168.172.0/24, Size: 24
   Base: 192.168.181.0/24, Size: 24
   Base: 192.168.183.0/24, Size: 24
   Base: 192.168.186.0/24, Size: 24
   Base: 192.168.207.0/24, Size: 24
   Base: 192.168.214.0/24, Size: 24
   Base: 192.168.215.0/24, Size: 24
   Base: 192.168.216.0/24, Size: 24
   Base: 192.168.223.0/24, Size: 24
   Base: 192.168.227.0/24, Size: 24
   Base: 192.168.228.0/24, Size: 24
   Base: 192.168.229.0/24, Size: 24
   Base: 192.168.237.0/24, Size: 24
   Base: 192.168.239.0/24, Size: 24
   Base: 192.168.242.0/24, Size: 24
   Base: 192.168.247.0/24, Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set
```
```
도커 이미지
```
```
jeonyeongjin05222811@c6r9s4 git-practice % docker images #로컬 이미지 목록
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE

만든 이미지가 없어서 아무것도 뜨지 않음
```
```

전체 컨테이너 목록 
커맨드
jeonyeongjin05222811@c6r9s4 git-practice % docker ps -a 
결과
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

"도커 실행 
jeonyeongjin05222811@c6r9s4 git-practice % docker run hello-world 

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

```실행```
```
jeonyeongjin05222811@c6r9s4 git-practice % docker run -it --name ubuntu-practice ubuntu bash
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
ed819469700f: Pull complete 
a3679419df18: Pull complete 
Digest: sha256:3131b4cc82a783df6c9df078f86e01819a13594b865c2cad47bd1bca2b7063bb
Status: Downloaded newer image for ubuntu:latest
root@3a47eb89625c:/# ls 
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@3a47eb89625c:/# echo 

root@3a47eb89625c:/# echo "hi" 
hi
```

## 7. 기존 Dockerfile 기반 커스텀 이미지 제작

### 7.1 선택한 기존 베이스 이미지

커스텀 이미지의 베이스로 `nginx:alpine` 이미지를 선택했다.

`nginx:alpine`은 경량 Linux 배포판인 Alpine Linux 위에 NGINX 웹 서버가 설치된 이미지이다. 웹 서버를 직접 설치하지 않고 정적 HTML 파일만 교체하면 간단한 웹 서비스를 만들 수 있어 선택했다.

### 7.2 적용한 커스텀 포인트

* 기본 NGINX 화면을 직접 작성한 `index.html`로 교체했다.
* 이미지 작성자와 용도를 `LABEL`로 기록했다.
* NGINX가 사용하는 80번 포트를 `EXPOSE`로 명시했다.

각 커스텀 포인트의 목적은 다음과 같다.

| 커스텀 항목            | 목적                           |
| ----------------- | ---------------------------- |
| `COPY index.html` | 기본 NGINX 페이지를 사용자 정의 페이지로 변경 |
| `LABEL`           | 이미지 작성자와 용도 기록               |
| `EXPOSE 80`       | 컨테이너가 사용하는 웹 포트 명시           |

---

### 7.3 정적 웹페이지 작성

#### 실행 명령

```bash
cat > index.html <<'EOF'
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Docker Mission</title>
</head>
<body>
  <h1>Docker Custom NGINX</h1>
  <p>nginx:alpine 기반으로 만든 커스텀 이미지입니다.</p>
  <p>작성자: IlleJiViN</p>
</body>
</html>
EOF
```

#### 파일 내용 확인

```bash
cat index.html
```

#### 출력 결과

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Docker Mission</title>
</head>
<body>
  <h1>Docker Custom NGINX</h1>
  <p>nginx:alpine 기반으로 만든 커스텀 이미지입니다.</p>
  <p>작성자: IlleJiViN</p>
</body>
</html>
```

---

### 7.4 Dockerfile 작성

#### Dockerfile 내용

```dockerfile
FROM nginx:alpine

LABEL maintainer="IlleJiViN"
LABEL description="Custom NGINX image for Docker mission"

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

#### 파일 내용 확인 명령

```bash
cat Dockerfile
```

#### 출력 결과

```dockerfile
FROM nginx:alpine

LABEL maintainer="IlleJiViN"
LABEL description="Custom NGINX image for Docker mission"

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

---

### 7.5 커스텀 이미지 빌드

#### 실행 명령

```bash
docker build -t custom-nginx:1.0 .
```

#### 핵심 출력 결과

```text
[+] Building 6.8s (7/7) FINISHED
 => [internal] load build definition from Dockerfile
 => [internal] load metadata for docker.io/library/nginx:alpine
 => [1/2] FROM docker.io/library/nginx:alpine
 => [2/2] COPY index.html /usr/share/nginx/html/index.html
 => exporting to image
 => => writing image sha256:510eaf3c9388c7ec95e18407ebc73ef5029a0161cf269ca17f7b3ffaa0159f1b
 => => naming to docker.io/library/custom-nginx:1.0
```

#### 검증 내용

Dockerfile을 기반으로 `custom-nginx:1.0` 이미지가 정상적으로 생성되었다.

---

### 7.6 생성된 이미지 확인

#### 실행 명령

```bash
docker images
```

#### 출력 결과

```text
REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
custom-nginx   1.0       510eaf3c9388   6 seconds ago   62.4MB
ubuntu         latest    de7345b16e94   2 weeks ago     100MB
hello-world    latest    e2ac70e7319a   4 months ago    10.1kB
```

#### 검증 내용

`custom-nginx` 이미지가 `1.0` 태그로 생성되었으며 이미지 크기는 62.4MB임을 확인했다.

---

### 7.7 커스텀 컨테이너 실행

#### 실행 명령

```bash
docker run -d \
  --name custom-nginx-container \
  -p 8080:80 \
  custom-nginx:1.0
```

#### 출력 결과

```text
48bd860b90bc51ca588c6dc1533153ad4c9c17d347abebae5c2b412f1d6884ce
```

출력된 문자열은 생성된 컨테이너의 ID이다.

---

### 7.8 컨테이너 실행 상태 확인

#### 실행 명령

```bash
docker ps
```

#### 출력 결과

```text
CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS         PORTS                                     NAMES
48bd860b90bc   custom-nginx:1.0   "/docker-entrypoint.…"   6 seconds ago   Up 5 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   custom-nginx-container
```

#### 검증 내용

`custom-nginx-container` 컨테이너가 정상적으로 실행 중임을 확인했다.

포트 매핑은 다음과 같이 설정되었다.

```text
macOS의 8080번 포트 → 컨테이너의 80번 포트
```

---

## 8. 포트 매핑 및 접속 증거

### 8.1 HTTPS 접속 실패 관찰

처음에는 HTTPS로 접속을 시도했다.

#### 실행 명령

```bash
curl https://localhost:8080
```

#### 출력 결과

```text
curl: (35) LibreSSL/3.3.6: error:1404B42E:SSL routines:ST_CONNECT:tlsv1 alert protocol version
```

#### 원인

현재 NGINX 컨테이너에는 HTTPS 인증서와 TLS 설정을 적용하지 않았으며 HTTP 서비스만 실행 중이다. 따라서 `https://`가 아니라 `http://`로 접속해야 한다.

---

### 8.2 HTTP 접속 성공

#### 실행 명령

```bash
curl http://localhost:8080
```

#### 출력 결과

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Docker Mission</title>
</head>
<body>
  <h1>Docker Custom NGINX</h1>
  <p>nginx:alpine 기반으로 만든 커스텀 이미지입니다.</p>
  <p>작성자: IlleJiViN</p>
</body>
</html>
```

#### 검증 내용

macOS의 `localhost:8080`으로 접속했을 때 컨테이너 내부 NGINX 서버가 직접 작성한 `index.html` 내용을 정상적으로 반환했다.

이를 통해 다음 항목을 검증했다.

* 커스텀 이미지 빌드 성공
* 커스텀 이미지 기반 컨테이너 실행 성공
* 호스트 8080번 포트와 컨테이너 80번 포트 연결 성공
* NGINX 웹 서버 응답 성공
* 직접 작성한 HTML 콘텐츠 제공 성공

### 8.3 브라우저 접속 주소

```text
http://localhost:8080
```

브라우저 접속 화면을 캡처한 뒤 저장소에 추가하고 다음과 같이 첨부한다.

```markdown
![커스텀 NGINX 브라우저 접속 결과](images/nginx-browser.png)
```




```
깃허브에 푸쉬 작업
```
```
jeonyeongjin05222811@c6r9s4 git-practice % git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 6 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 2.02 KiB | 2.02 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
```


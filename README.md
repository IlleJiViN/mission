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
```
```터미널 조작 로그 기록```
```현재 위치 확인 pwd 결과: /Users/jeonyeongjin05222811/git-practice```
```목록 확인(숨김 파일 포함) ls -al #- 뒤 옵션 a는 전ㅂ누 보이게함, l은 세부사항, 수정 가능 여부 등 접근 권한 보임```
```결과 ls -a # -l 길어서 제외```
```.		..		.git		README.md```
```빈 파일 만들기 touch [파일 이름] #이 파일 이름이 있으면 이 파일의 생성 시간 등이 나옴```
```touch helo```
```디렉터리 생성 mkdir```
```mkdir rid```
```파일 이동/이름 바꾸기 mv```
```이름 바꾸기 mv [파일명] [바꿀 이름]```
```사용법: mv [파일명] [옮길 디렉터리]```
```mv helo rid```
```파일 복사 cp [복사할 파일 명] [복사할 위치]```
```cp helo rid```
```권한 확인법 ls -l```
```ex)jeonyeongjin05222811@c6r9s4 git-practice % ls -l 
total 16
-rw-r--r--  1 jeonyeongjin05222811  jeonyeongjin05222811  5182 Aug  3 18:15 README.md```

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
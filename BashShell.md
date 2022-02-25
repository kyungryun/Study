### 유용한 Bash 커맨드라인 단축키

```bash
Tab : 명령 자동완성
Ctrl + c : 프로세스 중단
Ctrl + a : 라인 맨 앞으로 커서 이동
Ctrl + e : 라인 맨 뒤로 커서 이동
Ctrl + r : history 검색
```

### 파일 시스템 관련 명령어

```bash
cd (Change Directory)
	: 현재 작업 디렉토리를 지정한 위치로 변경

ls (List)
	: 현 디렉토리의 파일 목록 출력
ls -al 옵션 (ex ls -alt alh alr ...)
- h 용량 변환 (k,m,g 단위)
- t 시간순 정렬
- r 역순 정렬

df (Disk Free)
	: 마운트된 모든 장치에 대한 현재 디스크 공간 통계 출력
- h 용량 보기 편하게 변환
- T 디스크 타입
- i Inodes 정보 출력

mkdir (Make Directory)
	: 디렉토리 생성

rmdir (Remove Directory)
	: 디렉토리 삭제

pwd (Print Working Directory)
	: 현재 위치한 디렉토리의 절대경로를 출력

mount
	: 디스크 장치를 표시하거나 가상 파일 시스템으로 지정한 디렉토리를 연결
-t : 타입 지정 (nfs, fat ..)
mount -t [type] [host volume] [volume directory] 
   
stat
	: 지정한 파일의 파일통계 출력
stat [파일명]

```

### 파일 관련 명령어


```bash
touch
	: 지정한 이름의 파일을 생성 or 존재하는 파일의 타임스탬프 업데이트

cat
	: 파일의 내용 출력

head
	: 지정한 파일의 1라인부터 지정한 라인까지 출력 (default 10)
-n 숫자

tail
	: 지정한 파일의 마지막 라인부터 지정한 수 만큼의 라인 출력 (default 10)
로그 실시간 갱신 옵션
tail -f 파일명

cp
	: 지정한 파일을 지정한 위치와 이름으로 복사
-r 하위 디렉토리까지 포함
-f 강제 복사 (덮어쓰기)
-p 권한 복사

mv
	: 지정한 파일을 지정한 위치와 이름으로 이동

rename 변경전파일명 변경후파일명 대상파일
ex) rename test test0 test?
	test 파일을 test0으로 변경하는데 test인 파일들에 대해 적용
	test1,test2 -> test01,test02
rm
	: 파일 삭제

less 
	: 상하로 커서 이동이 가능한 파일보기

ln
	: 지정한 파일에 대한 심볼릭링크나 하드링크 생성
ln 옵션 링크의원본파일패스/이름 링크파일패스/이름
-s 심볼릭링크 : 윈도우의 바로가기와 동일함

paste
	: 지정한 파일들의 행을 읽어 탭으로 구분하여 병합

dd (Dataset Definition)
	: 블록 단위로 데이터셋을 정의하여 파일을 쓰고 읽음
dd if=[인풋파일] of=[아웃풋파일] bs=바이트(크기) count=블럭을복사할횟수

tar (Tape Archive)
	: 디렉토리나 파일을 하나의 파일로 만듬
압축 할때
tar -cvzf 파일명 디렉토리명/파일명
-c (create)
-x (extract)
-v (vervose) 로그확인가능
-z (zip)
-f (file name)
압축 풀때
tar -xvzf 파일명
tar -tf 압축 파일 내부를 확인할때
```

### 프로세스 관련 명령어

```bash
ps
	: 실행 중인 프로세스에 대한 정보 출력
ps aux  cpu 메모리 사용량 출력
ps axfwwwww  전체 명령어를 출력 (기본은 짤려있음)

pstree
	: 실행 중인 프로세스에 대한 정보를 트리구조로 출력

top
	: 프로세스 목록을 일정 시간마다 새로고침하여 화면에 출력

nohup
	: 쉘 스크립트 파일을 데몬 형태로 실행 표준 출력을 지정한 파일로 리다이렉트

kill
	: 지정한 프로세스에 시그널을 보내 프로세스 종료
```

### 네트워크 관련 명령어

```bash
ifconfig
	: 네트워크 인터페이스의 활성/비활성화 및 설정

ip
	: ip 조회 및 설정
ip address show

netstat
	: 네트워크 프로토콜의 통계와 연결상태를 출력
옵션
n : 정해진 포트명의 포트 숫자로 출력
l : listen 상태인 포트만 출력
t : tcp 통신
p : program 이름
u : udp 통신
네트워크의 상태 전체를 보는 명령어
-tan(u)

ss
	: 네트워크 소켓의 통계와 연결상태를 출력

iptables
	: 방화벽구성이나 NAT구성에 사용
-nL : 방화벽 리스트 확인

ufw
	: iptables의 제어를 쉽게 하기 위한 도구

ping
	: ICMP 프로토콜의 응답 확인 도구
-c 몇번 핑을 보낼지 설정 옵션

wget
	: 웹서버로부터 컨텐츠를 가져오는 도구

curl
	: 다양한 프로토콜을 사용하여 데이터를 전송하게 해 주는 도구
-L redirect 링크를 따라가는 옵션
-k https 인증 무시
-s slient 모드로 실행 / 통계 출력 x
-o output 파일 지정

route
	: 네트워크의 경로 정보의 출력, 변경하는 도구
```

### 검색/탐색 관련 명령어

```bash
find
	: 지정한 파일명 또는 정규표현식을 이용하여 파일을 검색
find 패스 -name 파일명(정규식)
ex) find ./ -name testfile.txt
expr) name, type [f/d], perm, e

which
	: 환경변수 PATH에 등록된 디렉토리에 있는 명령어를 찾아주는 도구
which ls

grep
	: 텍스트 검색 기능을 가진 도구
grep 옵션 "찾을문자열" 파일명
-i : 대소문자 구분 안함
-r : 하위 디렉토리까지 포함

history

```

+ touch : 파일 생성
  + touch {파일명.확장자명}

<br>

+ cp : 파일 복사
  + cp abc.txt def.txt : abc.txt 파일을 def.txt로 이름을 바꾸어 복사한다.
  + (example) cp *.txt bak : txt 형식 파일의 모든 파일을 복사하고 bak에 저장한다.

<br>

+ mkdir : 디렉토리 생성
  + mkdir {디렉토리명}
  + **중복된 디렉토리가 있으면 오류**

<br>

+ rm : 디렉토리 or 폴더 삭제
  + rm -rf {디렉토리명} : 디렉토리 및 해당 디렉토리 내 파일 전체 삭제
  + rm {디렉토리명}/{파일명} : 해당 디렉토리 내 특정 파일 삭제

<br>

+ echo : 출력문
  + echo "hello" : hello 출력
  + echo $0 : 현재 무슨 쉘 애플리케이션을 쓰고있는지 나타내어줌(bash or zsh)

<br>

+ who : 사용자 이름(username), 현재 콘솔 모드(tty1), 로그인 시간(UTC 기준) 출력

<br>

+ whoami : 사용자 이름 출력

<br>

+ date : 현재 시간(기본 UTC 기준) 출력

<br>

+ cal : 달력 보기

<br>

+ su : 현 사용자를 로그아웃하지 않고 다른 사용자의 권한을 얻을 때 사용한다.
  + su : root 계정 권한을 얻어옴
  + su "username" : username 계정 권한을 얻어옴

<br>

+ sudo timedatectl : 지역별로 현재 시간 확인하기
  + sudo timedatectl set-timezone "Asia/Seoul" : 현재 시간 서울 기준으로 바꾸기

<br>

+ sudo apt-get install "installname" : 외부 프로그램 설치
  + example) sudo apt-get install zsh : zsh 설치

<br>

+ pwd : 현재 나의 위치(디렉토리)는 어디있는지

<br>

+ cd : 현재 디렉토리를 변경함
  + cd / : /(루트) 경로로 이동

<br>

+ ls : 현재 디렉토리를 보여줌
  + ls . : . 은 현재 디렉토리에 있는 디렉토리(자식)를 나타냄(그냥 ls라고만 쳐도 똑같은 결과)
  + ls .. : .. 은 현재 디렉토리의 부모 디렉토리를 나타낸다.
  + ls -l {디렉토리명} : 특정 디렉토리(자식) 내 파일, 디렉토리를 보여줌
  + ls /bin : 기본적으로 리눅스에 탑재되어 있는 기본 프로그램들을 보여줌
    + bin은 이러한 프로그램들을 저장하는 디렉토리
  + ls -al 명령어를 입력하면, 자신이 지금 있는 디렉토리내의 모든 파일 또는 디렉토리 상세정보를 출력
    + 이때 디렉토리 맨 앞에 drwxrwxrwx 같은 문자들은 권한 속성을 나타냄

<br>

+ scp : ssh 파일 전송
  + 원격 -> 로컬
    + scp [옵션] [계정명]@[원격지IP주소]:[원본 경로 및 파일] [전송받을 위치]
    + (example) scp abc@111.222.333.444:/home/abc/index.html /home/me/
  + 로컬 -> 원격
    + scp [옵션] [원본 경로 및 파일] [계정명]@[원격지IP주소]:[전송할 경로]
    + (example) scp /home/me/wow.html abc@111.222.333.444:/home/abc/
    + 로컬서버 /home/me/wow.html 파일을 IP 111.222.333.444 서버의 /home/abc/ 디렉토리에 전송
```
※ scp란?
1. secure copy의 줄임말로 ssh를 이용하여 네트워크로 연결된 호스트간에 파일을 주고받는 명령어
2. 원격지에 있는 파일과 디렉터리를 보내거나 가져올 때 사용하는 파일 전송 프로토콜
3. ssh와 동일한 22번 포트와 identity file을 사용해서 파일을 송수신하기 때문에 안정된 프로토콜
```

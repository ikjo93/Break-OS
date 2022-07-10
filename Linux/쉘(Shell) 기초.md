### 쉘(Shell)이란?
+ 모든 운영체제는 하드웨어를 관리해주고 사용자가 프로그램을 사용하기 쉽게 도와준다. 
+ 예를 들어, 하드웨어의 용량을 확인할 수 있는 것도 운영체제가 보조기억장치를 관리하고 있기 때문에 가능한 것이고, 
+ 프로그램을 설치하고 실행하는 것도 마찬가지이다. 
+ 이때 운영체제의 Core 역할을 하는 것은 바로 "커널(Kernel)"이다. 
+ 하지만 사용자는 네이티브 언어를 다루기 어려워 커널을 직접적으로 다루기 어렵다. 
+ 이때 등장한 것이 바로 "쉘(Shell)"이다. 
+ 메타포로 쉘은 껍데기, 커널은 알맹이라고도 볼 수 있다.
+ 사용자가 쉘에서 작성한 명령어는 커널이 이해할 수 있는 명령어로 변환된다.
+ 즉, 쉘은 사용자가 작성한 명령어를 해석하는 프로그램으로 볼 수 있다.
+ 이때 하나의 컴퓨터에서 하드웨어와 커널은 단 하나뿐이겠지만 쉘과 사용자는 다수일 수 있다.
```
※ 사용자의 쉘 이용 과정 예시
사용자가 쉘에 명령어 입력 → 
쉘에서 명령어를 해석하여 커널 제어 → 
커널이 하드웨어를 제어 → 
하드웨어가 커널에 출력 반환 → 
커널이 이를 해석하여 쉘에 전달 → 
쉘이 이를 다시 해석하여 사용자에 전달(출력)
```

<br>
 
### 쉘의 종류
+ 쉘의 종류는 CLI(Command-Line Interface)와 같이 명령어 인터페이스로 이루어진 형식이 있고 GUI(Graphical User Interface)와 같이 시각적인 인터페이스로 이루어진 형식이 있다. 
+ CLI의 대표적인 프로그램으로는 Bash(우분투 기본 쉘), Git Bash(윈도우 OS에서 주로 사용), zsh(Z Shell) 등이 있다. 
+ 반면 GUI의 대표적인 프로그램으로는 Windows 탐색기 등이 있다. 
+ 이처럼 쉘이라는 것은 형식보다도 해당 프로그램이 사용자와 커널 사이를 이어주는 역할을 얼마나 제대로 하는지가 중요한 것이다.
 
<br>
  
### 터미널(Terminal)이란?
+ 터미널과 쉘이 헷갈릴 수 있는데, 터미널은 말 그대로 입출력 환경(명령어 입력, 결과 출력 등을 표시해주는 창)으로 사용자와 쉘간의 인터페이스 역할을 한다. 
+ 즉, 명령어를 해석하고 처리하는 프로그램인 쉘의 기능과는 무관하지만 
+ 사용자 입장에서는 쉘을 사용하기 위해서는 반드시 터미널을 거쳐야 하므로 터미널은 쉘 프로그램과 일체형으로 볼 수 있다. 
+ 메타포로 브라운관, LCD 등 TV 자체가 터미널이라면, TV에서 방영되는 TV 프로그램이 쉘이다.
+ 윈도우 운영체제에서는 기본적으로 터미널 환경인 명령 프롬프트 창(cmd)을 지원해주는데, 이는 리눅스의 명령어와는 다소 차이가 있다. 
+ 이때 powershell이나 cmder를 이용하면 리눅스와 동일하게 사용할 수 있는데 
+ 이를 위해서는 우선 microsoft store에서 Windows terminal을 별도로 설치해서 환경 설정을 한다.
+ 하지만 윈도우 운영체제에서는 주로 깃 배시(Git Bash) 쉘을 사용하는데
+ 이를 위해서는 사용자가 별도로 설치하거나 Windows terminal에서 따로 환경 설정 파일을 구성해 연동해주어야 한다.

<br>

### 쉘 스크립트란?
+ 스크립트(Script)란 "대본"이라는 뜻으로 연속적인 쉘 명령어들의 순서를 나타낸다. 
+ 이를 통해 사용자는 특정 반복적인 작업들에 대해 자동화 시킬 수 있는데, 
+ 대표적인 예로 데이터 백업(로컬 PC → 리눅스 서버) 등이 있다. 
+ 이때 프로그래밍 언어 대비 쉘 스크립트의 장점은 컴파일 단계가 없기 때문에 스크립트는 디버깅을 하는 동안 빠르게 실행이 가능하다는 점이다.

### 쉘 스크립트 활용(우분투)
+ 우분투 터미널 환경에서 `nano [스크립트 파일명]`을 입력하면 시스템 기본 편집기 화면으로 이동하게 되는데, 
+ 여기서 쉘 스크립트의 코드와 명령어들을 작성하게 된다. 
+ 편집기 첫 줄에는 `#!/bin/bash`을 작성하고 두번째 줄부터 작성을 하게 된다. 작성을 다 마치고 터미널 환경에서 `./[스크립트 파일명]`을 입력하면 해당 쉘 스크립트 프로그램이 실행된다.

#### bak 디렉토리 생성 및 해당 디렉토리에 log 파일 저장
```
#!/bin/bash
if ! [ -d bak ]; then
	mkdir bak
fi
cp *.log bak
```

#### 디렉토리 및 파일 생성
```
#!/bin/bash
for i in $(seq 16)
do
        if ! [ -d day$i ]; then
                echo "day$i not found!!"
                mkdir day$i
                cd day$i/
                touch test$i.cs
                echo "New directory$i and test$i file has been created!!"
                cd ..
        else
                echo "day$i exists!!"
        fi
done
```

#### 디렉토리 삭제
```
#!/bin/bash
for i in $(seq 16)
do
        rm -rf day$i
        echo "day$i has been deleted!!"
done
```

#### 디렉토리 내 파일 압축 및 서버 전송(로컬 → 우분투)
```
#!/bin/bash
DATE=$(date +"%Y-%m-%d")
for i in $(seq 16)
do
        if ! [ -d day$i ]; then
                echo "day$i not found!!"
        else
                cd day$i/
                if ! find . -name "*.cs"; then
                        echo "cs file not found!!"
                else
                        cp *.cs /c/codesquad/
                fi
        cd /c/codesquad/
        fi
done
if ! find . -name "*.cs"; then
        echo "No cs file has been compressioned!!"
else
        zip -r backup_$DATE.zip *.cs
        echo "Success!!"
fi
scp  backup_$DATE.zip ikjo@127.0.0.1:/home/ikjo/backup/
```

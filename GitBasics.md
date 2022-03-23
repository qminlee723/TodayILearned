# Git?

- **분산 버전 관리 시스템** 중 하나
- 코드의 히스토리(버전)을 관리하는 도구
- 개발되어온 과정 파악 가능 > 따라서 이전 버전으로 돌아가는 것이 가능해진다. 
- 이전 버전과의 변경 사항 비교 및 분석(google doc 같은거)

* Git은 변경사항만을 저장한다
* version database: Git(버전관리)
* 버전: 컴퓨터 소프트웨어의 특정 상태
* git은 변경사항만 저장을 함 



### 분산 버전 관리 시스템(Distributed Version Control System)

- CVCS vs DVCS
  - 중앙집중식버전관리시스템은 중앙에서 버전을 관리하고 파일을 받아서 사용
  - **분산버전관리시스템은 원격 저장소(remote repository)를 통해 협업하고, 모든 히스토리를 클라이언트들이 공유**
  - 




# GitHub?

* version database를 저장해주는 **저장소**(service): Github
* Github과 **Gitlab**
  * Github은 MS소유
  * Gitlab은 서버를 자신의 컴퓨터에서 구축할 수 있게 할 수 있는 것 -> 따라서 싸피는 보안상 Gitlab을 사용
  * lab.ssafy(싸피가쓰는깃랩)



git clone

git log --oneline

git remote -v 



원격 저장소에서 직접 수정하지말고

모든 파일변경 수정 삭제 생성은 로컬에서

커밋 열심히 합시다

데일리 커밋



# Shell

* **명령 프롬프트**가 윈도우의 기본 쉘

  * unix 명령어가 되지 않음

    * Unix - 여기서 linux와 mac os가 파생됨

    * Linux

    * Windows

    * | CLI (Command Line Interface)               | GUI(Graphic User Interface)                             |
      | ------------------------------------------ | ------------------------------------------------------- |
      | 명령어를 이용해서 인터페이스를 조작하는 것 | 그래픽을 보면서 컴퓨터에게 명령을 내리는 것들POWERSHELL |

      

* POWERSHELL



# Unix/Linux 명령어



ls 현재 위치의 폴더, 파일 목록보기

cd<path> 현재 위치 이동하기

cd.. 상위폴더로 이동

mkdir<name> 파일 생성하기

touch<name> --- 지원 안되는 리눅스 명령어

rm<name> 파일 삭제하기

rm -r <name> 디렉토리 삭제하기(r = recursive)

~ 홈디렉토리

code . gitbash에서 설정된 장소에서 vs code를 엶



# VS Code

Terminal > New Terminal > dropdown menu (next to +) > Gitbash

단축키: ctrl + shift + `  터미널이 열린다





**Repository** 특정 디렉토리를 버전 관리하는 저장소

* **git init** 명령어로 로컬 저장소를 생성
  * .git 디렉토리에 버전관리에 필요한 *모든 것*이 들어있음
  * 왼쪽에 버전관리 되어있는 애들을 vs code에서 초록색으로 변환해줌
  * 내 PC > C: > 사용자 > 이규민 > ssafy7 > RacingGround 
    * 보기 > 숨긴항목보기 > .git 이라는 폴더 있을 것!
    * RacingGround위치가 Repository 라는 걸 알아놓자



RacingGround 프로젝트 생성

* BaiscCar.py 생성
* README.md 생성 ---- 프로젝트 설명서
* 특정 버전으로 남긴다 = **커밋(commit)**한다
* repoisotry 안에 commit이 쌓여가는 것



**Commit** Commit이란 세 가지 영역을 바탕으로 동작한다

* Working Directory
  * 내가 작업하고 있는 실제 디렉토리 (ex - RacingGround)
  * git init 으로 깃을 시작. 디렉토리 안의 파일은 untracked file로 분류
  * git init이 되면 (master) 표시 생김
  * git은 untracked 파일은 인식은 하지만, track하지는 않음.
* Staging Area
  * *Commit으로 남기고 싶은*, *특정 버전으로 관리*하고 싶은 파일이 *잠시* 있는 곳
  * git add 라는 명령어로 staging area로 올릴 수 있다(untracked file -> traked git으로 변환
  * commit은 아니지만, tracked된 file로 변환할 수 있음
  * unstage: git rm --cached <file>... 
* Repository
  * Commit들이 저장되는 곳
  * git commit 이라는 명령어로 commit을 만들 수 있음
  * working directory에서 수정사항 생기고 > git add > git commit > 하면 새로운 버전의 commit이 생김



**git status**: git의 상태를 알려줌

**git add .**: 추적 되지 않은 모든 파일과 추적하고 있는 파일 중 수정된 파일을 모두 staging area에 올리게 됨. 여기서 "."은 '현재 위치'라는 의미를 담고있음.

**cd ..**: 한칸 부모 directory. "."은 현재 위치 ".." 바로 위의 위치 "..." 두번 위로 가는 위치

**-m ""**:  메시지 버전임. 변경사항이나 뭐 뭔지 설명하는 주석같은거라고 보면 됨

**git commit -m "commit_message"** 단, commit message는 자세하게! 왜 이러한 변경사항이 생겼는지!



처음 git 사용할때 유저네임, 이메일 설정

**git confic user.name "user_name"**

**git config user.email "user_email"**





기존 이메일과 유저네임 바꾸고 싶을때:

**git config global user.name "user_name"**

**git confic global user.email"user_email"**



확인하는것

**git config -- list**

**git log**

commit의 고유 번호와 정보를 보여줌



repository 안에 repository 만들면 헷갈림

만약 만들게 되면 아까 .git 폴더를 지워준다





**git log** : git의 commit history 보기

**git diff**: 두 commit 간 차이 보기

* git log에서 고유 아이디(노란색)간의 차이 볼 수 있음
* 아이디 전부 다 칠 필요 없이, 첫 4자릿수만 비교 가능함.
* 순서 중요함: 앞의 것을 기준으로 뒤의 커밋을 비교해 주는 것. 빈 파일과 안 빈 파일이 비교되면 추가 된 정보를 보여주고, 안 빈 파일을 기준으로 빈 파일이 비교되면, 



git ignore: remote repository에 올리고 싶지 않은 폴더 혹은 파일을 ignore시키는 것

git rm -r --cached . : 이미 remote repository에 올라간 폴더 혹은 파일을 삭제시키는 것(local 에는 존재)



정규표현식: 파일 조건값 (ex. 폴더명에 '1'이 들어가는 모든 폴더를 ignore하기)





^ Local repository



**Remote repository**



1. **Push** Local Repository와 Global Repository를 연결 (Push)
   - 
2. **Clone** Global Repostiory의 코드를 Local로 가져옴 (Clone)
   - git clone 후에 url 붙여넣으면 됨. 그러면 로컬로 복사 해 온 것.
   - 그러면 (main)이 됨
     - main = master (인종차별논란때문에)
3. **Pull** Local 에서  업데이트 된 사항을 global로 가져감
   - git clone 후에 url 붙여넣으면 됨. 그러면 로컬로 복사해온 것.
   - 그러면 (main)이 됨. 
     - main = master (인종차별논란때문에)





Github Repository 

Local Repository



git remote add origin {remote_repo}

- 여기서 origin -> {url}의 이름. origin 이라고 안 해도 되긴 한데 그래도 관례가 origin이므로 익숙해지는게 좋음.

git push -u origin master

- "-u"는 remote repository를 등록한 다음에 쓰면 됩니다. set-upstream의 약자. 
  - master라는 큰 줄기를 가지고 있는데, 이걸 origin으로 보낼 거야 라는 의미



git clone {remote_repo}

remote repo를 local로 복사합니다. 

git push origin master 

local repo의 최신 커밋을 remote repo로 push 합니다

내 master에 있는 변경사항들을 origin에 푸쉬할거야



**GPG Key**

같은 repository 에 다른 사람들이 푸시해도, 누가 푸시하는지 확실히 알려주는 것


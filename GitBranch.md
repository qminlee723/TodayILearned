# Git Branch



1. `git branch`: 브랜치 목록 확인

2. `git branch 브랜치이름`: 새로운 브랜치 생성

3. `git branch -d 브랜치이름`: 특정 브랜치 삭제(merged 된 브랜치만 삭제)

4. `git branch -D 브랜치이름`: 강제 삭제

5. `git switch 브랜치이름`: 해당 브랜치로 이동

6. `git switch -c 브랜치이름`: 브랜치를 새로 생성과 동시에 이동

   * git switch 전에 고려해야될 사항:

     * working directory file이 모두 깃에 버전관리가 되고 있는지 확인

     * 만약 버전 관리가 안 되어있다면? - 독립된 작업공간 성립하지 않음

       <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311094614709.png" alt="image-20220311094614709" style="zoom:67%;" />

1. ㅇ





<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311092448904.png" alt="image-20220311092448904" style="zoom:67%;" />





text 수정후



<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311092514828.png" alt="image-20220311092514828" style="zoom:67%;" />



Login은 master-3

HEAD는 mater-4



현재 test.txt 상태

![image-20220311092928557](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311092928557.png)



login 쪽을 개발해보려고 한다면,

![image-20220311092707347](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311092707347.png)



![image-20220311093003075](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093003075.png)





다시 master로 가고자 한다면,

![image-20220311093034102](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093034102.png)



이처럼 브랜치는 완전히 독립된 환경!



git log --oneline

![image-20220311093210509](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093210509.png)

git log--oneline --all

![image-20220311093146411](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093146411.png)





test_login.txt를 생성 후 add, commit



![image-20220311093437940](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093437940.png)

![image-20220311093459621](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093459621.png)





다시 마스터로 가서 지워보자

![image-20220311093558140](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311093558140.png)



안되네!





**깃 병합하기**

7. `git merge 병합할 브랜치 이름`
   * 단, merge하기 전에 다른 브랜치르 합치려고 하는, 즉 메인 브랜치로 swtich 해야 함
8. 



**fast-forward**

최신 커밋으로 나갔을 뿐



git_merge란 폴더에 test.txt만들고 add commit 한 상태

* fast-forward 통해 login branch를 만들면서 이동

![image-20220311102032181](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311102032181.png)



* login.txt 파ㅇ리 생성 후 add commit, log 확인

  ![image-20220311102303582](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311102303582.png)

* merge를 하려면, main 브랜치로 이동 한 후에 머지해야

* 따라서 switch 명령어를 통해 master로 돌아가준다

  ![image-20220311102437778](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311102437778.png)

  

이 때 login.txt 파일이 사라진 것을 볼 수 있음

* merge해 줌

  ![image-20220311102635055](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311102635055.png)

  

  Fast-forward라고 적힌 것을 볼 수 있음

  HEAD를 앞으로 빼 주는 것일 뿐

  merge가 된 브랜치는 그 역할이 끝난 것 -- 따라서 머지된 브랜치는  삭제를 해 주면 됨

  

* merge된 브랜치 삭제

  ![image-20220311103715313](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311103715313.png)

* 



**3-way merge(merge commit)**

* signout branch

* signout.txt 생성 후 add, commit

  ![image-20220311104015022](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311104015022.png)

* 아까 fastforward 상황과 동일한 상황

* 마스터로 이동

  ![image-20220311104149734](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311104149734.png)

* 또다른 branch 생성 후  master.txt add, commit

  ![image-20220311104242819](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311104242819.png)

* 현재 상황

  ![image-20220311104331552](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311104331552.png)

* signout.txt 생성, add commit

* `git merge signout` (왜인지 모르게 새로운 창이 떠서 ..  일단 유튜브 화면 캡쳐)

  ![image-20220311104740825](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311104740825.png)

* merge 됐으니 signout branch도 삭제해준다

  `git branch -d signout`



**merge conflict**

* merge하는 두 브랜치에서 같은 파일의 같은 부분을 동시에 수정하고 merge 하면, git은 해당 부분을 자동으로 merge해주지 못함
* 반면, 동일 파일이더라도 서로 다른 부분을 수정했다면 conflict없이 자동으로 merge commit된다.
* hotfix branch만듦 ==> test.txt에 수정 후 add commit
* ![image-20220311105440389](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311105440389.png)
* ![image-20220311105327131](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311105327131.png)

* master로 switch -> hotfix에서 작성한 문장이 사라진 걸 볼 수 있음

  ![image-20220311105536768](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311105536768.png)

* master branch인 상태로 ,text.txt 같은 라인에 수정을 해 주고 add commit

  ![image-20220311105715133](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311105715133.png)

* `git merge` 하면, conflict 남

* ![image-20220311105845365](C:\Users\Gyumin\ssafy7\TodayILearned\image-20220311105845365.png)

* status로도 conflict 확인가능

  ![image-20220311110012137](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311110012137.png)

  

* 2번째, 6번째, 4번째 줄 수정해줌

  * 둘 중 비교해서 최종 완성본 니가 만들어
  * conflict 나는 부분을 시각적으로 보여주는 거임
  * 해결하고 커밋하렴

* conflict난 부분(2번째~6번째) 다 지우고 새로 파일을 수정해줌 > add > commit

  ![image-20220311110056201](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311110056201.png)

* `git commit`하면 아래처럼 VIM 화면이 뜸

  ![image-20220311110242792](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311110242792.png)

  `:`, `wq` 로 빠져나온다

  ![image-20220311110339178](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220311110339178.png)

* 머지 끝나면 hotfix branch 삭제해주기

  ` git branch -d hotfix`
# Algorithm String

## :zero: OVERVIEW

문자열

패턴매칭

문자열 암호화

문자열 압축



## :one: 문자의 표현

### 1. 아스키(ASCII) 코드

* 네트워크가 발전하면서 서로간에 정보를 주고받을 때 정보를 달리 해석하는 문제
* 이러한 문제점을 해결하기 위해 표준안 만듦
* 1967년 ASCII(American Standard Code for Information Interchange)라는 문자 인코딩 표준이 제정
* :100: 7bit 인코딩으로 128 문자를 표현하며 33개의 출력 불가능한 제어 문자들과 공백을 비롯한 95개의 출력 가능한 문자들로 이루어져 있다
  * 출력 불가능한 제어 문자: \n
  * 65가 대문자 A고
  * 97이 소문자 a
  * (0~31) NUL등 제어문자, (32~) 부터 문자 나타냄 
* 컴퓨터가 발전하면서 미국 뿐 아니라 각 나라에서도 컴퓨터가 발전했으며, 각 국가들은 자국의 문자를 표현하기 위해 코드체계를 만들어서 사용하게 되었다.
  * 우리 나라도 한글 코드체계를 만들었음. 조합형, 완성형 두 종류
* 

### 1-1. 확장 아스키

* 표준 아스키는 7bit를 표현하는데 비해 확장 아스키는 1B내의 8bit를 모두 사용함으로써 추가적인 문자 표현이 가능
* 총 256개
* 컴퓨터 생산자와 소프트웨어 개발자가 여러 가지 다양한 문자에 할당할 수 있도록 하고 있다. 이렇게 할당된 확장 부호는 표준 아스키와 같이 서로 다른 프로그램이나 컴퓨터 사이에 교환되지 못한다
* 따라서 확장아스키는 프로그램이나 컴퓨터 또는 프린터가 그것을 해독할 수 있도록 설계되어 있어야만 올바로 해독된다.

### 2. 유니코드

* 자국의 코드체계를 타 국가가 가지고 있지 않으면, 정보를 잘못 해석 할 수 있음

* 따라서 다국어 처리를 위해 표준을 마련했다. 이게 유니코드.

* Character Set으로 분류(안외워도 됨)

  * UCS-2(Universal Character Set 2)
  * UCS-4(Universal Character Set 4)
  * 유니코드를 저장하는 변수의 크기를 정의
  * 바이터 순서에 대해서 표준화하지 못함
  * 다시 말해, 파일을 인식 시 이 파일이 UCS-2, UCS-4인지 인식하고 각 경우를 구분해서 모두 다르게 구현해야 하는 문제 발생
  * 그래서 유니코드의 적당한 외부 인코딩이 필요하게 됨

* Big-endian, little-endian

  * 8 bit = 1 byte
  * Big-endian: 높은 자리수를 높은 주소에 
  * Little-endian: 낮은 자리수를 빠른 주소에 

* 유니코드 인코딩

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216092933301.png" alt="image-20220216092933301" style="zoom:50%;" />

  * 여기서 8비투, 16비트는 최소 비트 수

* Python 인코딩

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216094214820.png" alt="image-20220216094214820" style="zoom: 50%;" />

* 





## :two: 문자열

### 1. 문자열의 분류

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216094306649.png" alt="image-20220216094306649" style="zoom:67%;" />

### 2. Java, C언어의 문자열 처리(언어별 특징)

* 다르구나! 정도로만 알고있자

* Java

* C

* 다음 두 코드의 차이 이해하기

  * s1 = list(input())
  * s2 = input()

* strlen()함수 만들어 보기

  ```python
  def strlen(s):
      i = 0
      while s[i]!='\0':
          i += 1
      return 
  ```

* null 과 none

  * null은 코드(타입:string)
  * none 적용되지 않았다

* Python 에서의 문자열 처리

  * char 타입 없음

  * 텍스트 데이터의 취급방법이 통일되어 있음

  * 문자열 기호

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216101736539.png" alt="image-20220216101736539" style="zoom:50%;" />

  * 문자열은 시퀀스 자료형으로 분류되고, 시퀀스 자료형에서 사용할 수 있는 인덱싱, 슬라이싱 연산들을 할 수 있다.
  * 문자열 클래스에서 제공되는 메소드
    * replace(0), split(), isalpha(), find()
  * 문자열은 튜플과 같이 요소값을 변경할 수 없음
  * C, Java의 String 처리의 기본적인 차이점
    * c는 아스키 코드로 저장
    * java는 유니코드(UTF16, 2byte)로 저장
    * 파이썬은 유니코드(UTF8)로 저장

  

### 3. 문자열 뒤집기

* 자기 문자열에서 뒤집는 방법이 있고, 새로운 빈 문자열을 만들어 소스의 뒤에서부터 읽어서 타겟에 쓰는 방법이 있다
* 자기 문자열을 이용할 경우는, swap을 위한 임시 변수가 필요하며 반복 수행을 문자열 길이의 반만을 수행해야 한다. 문자열 길이의 절반만큼의 교환횟수가 필요하다.
* Python 은 reverse함수 혹은 slice notation 을 이용해 구현하면 된다
  * reverse()는 string에서는 동작안함



### 4. 문자열 비교

* c strcmp()함수

  * 문자열이 같으면 0 리턴
  * str1이 str2보다 사전 순서상 앞서면 음수 혹은 -1 리턴
  * str1이 str2보다 사전 순서상 나중이면 양수 또는 1 리턴

* Java에서는 equals

  * equals

* Python 에서는 == 연산자와 is 연산자

  * == 연산자는 내무적으로 트수 메서드 `__q__()`를 호출한다.

  * 참고

    ```python
    s1 = 'abc'
    s2 = 'abc'
    s3 = 'def'
    s4 = s1
    s5 = s1[:2] + 'c'
    ```

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216103407707.png" alt="image-20220216103407707" style="zoom:50%;" />

* 문자열 크기비교

  * 문자열 자체를 크기비교할 수 있는 것은 각 문자열이 숫자에 저장되어 있기 때문

  * UTF의 한글 코드표를 볼 수도 있음(유니코드)

  * 크기는 유니코드 변환표 사전순서대로 가능

  * 예시

    ```python
    a = "abc"
    b = "Abc"
    c = "cba"
    d = "cb"
    e = "가나다"
    f = "다나가"
    
    print(a > b)
    print(c > d)
    print(e > f)
    ```

    

    ```python
    # 1. 슬라이싱 사용
    my_str = "abc"
    my_str = my_str[::-1]
    print(my_str)
    
    # 2. reverse 메소드를 사용하고싶다
    my_str = "abc"
    my_str = list(my_str)
    my_str.reverse()
    print(my_str)
    my_str = "".join(my_star) # 여기 있는 애들은 이터러블 하는 애들 사이 하나하나에 넣어서 연결시켜줭
    
    # 3. 새로운 문자열 생성
    new_str = ""
    my_str = "abc"
    for ch in my_str:
        new_str = ch + new_str
    ```

    

### 5. 문자열 숫자를 정수로 변환하기

* C 언어에서는 atoi(), 역함수 itoa()
* java에서는 parse 메소드
  * Integer.parsheInt(String)
  * 역함수로는 toString()
* Python 에서는 숫자와 문자변환 함수를 제공
  * int(), float(), str()



### 6. 문자열 숫자

#### 1) Brute Force 

* 고지식한 패턴 검색 알고리즘

* index error 주의하자 

  * 패턴이 세개이면 

  * ```python
    for i: 0 -> N - M		 #마지막 끝나는 점을 앞으로 옮기자
        for j: 0 -> M-1
            while j < M
            t[i+j] p[j]
    ```

* 쉽지만 오래 걸린다: O(MN)

  * N이 텍스트의 길이 
  * M이 패턴의 길이

* 예시

  ```python
  pattern = "is"					# 찾을 패턴
  text = "This is a book"			# 전체 텍스트
  M = len(p)						# 찾을 패턴의 길이
  N = len(t)						# 전체 텍스트의 길이
  
  def BruteForce(pattern, text):	
      i = 0						# t의 인덱스
      j = 0						# p의 인덱스
      while j < M and i < N:		# t, p 인덱스 범위 벗어나지 않을 조건
          if text[i] != pattern[j]
          	i = i - j			# 이전 시작 위치
          	j = -1				# 맨 앞
          i += 1					# 다음 시작 위치
          j += 1					# 맨 앞 + 1(맨 앞 다음)
      if j == M : 				# 검색 성공
          return i - M			## 이 위치에 니가 찾는 패턴이 있어!
      else: 						# 검색 실패
          return -1				
       
  ```

  

  



#### 2) 카프-라빈 알고리즘

* 

#### 3) :star: KMP 알고리즘

* 개념

  * 불일치가 발생한 텍스트 스트링의 앞 부분에 어떤 문자가 있는지를 미리 알고 있으므로, 불일치가 발생한 **앞 부분에 대하여 다시 비교하지 않고** 매칭을 수행
  * 패턴을 전처리하여 배열 next[M]을 구해서 잘못된 시작을 최소화함
    * next[M]: 불일치가 발생했을 경우 이동할 다음 위치
  * 시간 복잡도: O(M+N)
  * 스킵배열이 어떤 식으로 만들어 지는지, 그 스킵 배열을 어떻게 쓰는지 알고있기

* 아이디어 설명

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216131138429.png" alt="image-20220216131138429" style="zoom:50%;" />

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216131152521.png" alt="image-20220216131152521" style="zoom:50%;" />

  * 패턴의 불일치가 된 인덱스부터 계산을 시작해!
  * 변수명은 lps, next 등을 많이 씁니다

* 예시

  * 패턴과 텍스트가 명시되어 있지 않은 경우, 어느 것이 더 짧은지를 나타내는 코드 먼저 써줘야 한다.

    ```python
    def kmp(t, p):
        N = len(t)
        M = len(p)
        lps = [0] * (M+1)
        #preprocessing
        j = 0						# 일치 갯수 == 비교할 패턴 위치
        lps[0] = -1
        for i in range(1, M):
            lps[i] = j				# p[i]이전에 일치한 갯수
            if p[i] == p[j]:
                j += 1
            else:
                j = 0
        lps[M] = j
        # search
        i = 0 							# 비교할 텍스트 위치
        j = 0							# 비교할 패턴 위치
        while i < N and j <= M:		
            if j == -1 or t[i] == p[j]:	# 첫글자 불일치 or 일치하면
                i += 1			
                j += 1
            else:						# 불일치
                j = lps[j]
            if j == M:					# 패턴을 찾을 경우
                print(i-M, end = '')	# 패턴의 인덱스 출력
                j = lps[j]
        
        
    ```

  

#### 4) 보이어 무어 알고리즘

* 오른쪽에서 왼쪽으로 비교

* 대부분의 상용 소프트웨어에서 채택하고 있는 알고리즘

* 보이어-무어 알고리즘은 패턴에 오른쪽 끝에 있는 문자가 불일치 하고 이 문자가 패턴 내에 존재하지 않는 경우, 이동 거리는 무려 패턴의 길이 만큼이 된다. 

* 아이디어 설명

  1. 오른쪽 끝에 있는 문자가 불일치 하고, 이 문자가 패턴 내에 존재하지 않는 경우

     ![image-20220216144313885](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216144313885.png)

  2. 오른쪽 끝에 있는 문자가 불일치 하고, 이 문자가 패턴 내에 존재하는 경우

     ![image-20220216144324244](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216144324244.png)

* 예시

  ![image-20220216144402563](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216144402563.png)

  ![image-20220216144551581](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216144551581.png)

  

* 문자열 매칭 알고리즘 비교

  * 찾고자 하는 문자열 패턴의 길이 m, 총 문자열 길이 n
  * 고지식한 패턴 검색 알고리즘: O(MN)
  * 카브-라빈 알고리즘: 세타(N) (세타 = 항상 늘 이정도, 빅오 같은 경우는 최악의 경우)
  * KMP알고리즘: 세타(N)
  * 보이어-무어 알고리즘: 
    * 최선의 경우: 오메가(N)
    * 최악의 경우: 세타(MN)
    * 알고리즘 문제: 호스풀 알고리즘을 사용합니다







## :three: 문자열 암호화(참고)

### 1. 카이사르 암호화

* 줄리어스 시저가 사용했다고 하는 암호

* 평문에서 사용되고 있는 알파벳을 일정한 문자 수만큼 평행이동 시킴으로써 암호화

  ![image-20220216150520977](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216150520977.png)

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216150532666.png" alt="image-20220216150532666"  />

  

### 2. 단일 치환 암호

* 단일 치환 암호의 복호화

  * 모든 키의 조합(key space)가 필요하다

* 단일 치환 암호의 키의 총수는 26!

* 1초에 10억개의 키를 적용하는 속도로 조사한다고 해도, 모두 키를 조사하는데 120억년 이상의 시간이 걸린다.

  ![image-20220216150608528](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216150608528.png)

  

### 3. bit 열의 암호화

* 배타적 논리합(exclusive-or) 연산 사용

  ![image-20220216150634914](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216150634914.png)

* :100: 서술형이 나올지도... 왜 XAND를 안쓰고 XOR쓰는지!



### 4. 문자열 압축

* 예시

  ![image-20220216150809539](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220216150809539.png)

  



## :four: 예시: SWEA > String 문제 찾아보기


# Computational Thinking

## :zero: OVERVIEW

## :one: 논리

### 1. 논리연산자

* 부정(not): ~

* 논리합(or): V

* 논리곱(and): ^

* 배타적논리합(exclusive or): ㊉
  * p, q 중 하나만 참일 때 참이 되는 명제

* 조건(condition): ->

* 쌍방조건(bicondition): <->

* 기타: nand, nor



### 2. 진리표(truth table)

* 모든 명제들의 진릿값이 가능한 경우를 모두 나열한 표



### 3. 증명(proof)

* 연역법
* 귀납법
* 수학적귀납법
  * basis
    * n0 성립함을 보이고
  * hypothesis
    * n=k 성립한다고 가정하고
  * step
    * n = k+1 성립하는지 보이면 성립된다.
* 모순증명법



### 4. 수와표현

* 어떤 값 n 을 표현하기 위해서는 몇 개의 비트가 필요할까?

* 2^k - 1 >= n이 성립해야 한다

  * 즉, 2^k >= n +1

* k >= log(n+1)

  * x = logn 

    * x와 n을 비교하면 x가 더 작고, n이 커질수록 엄청나게 달라진다
    * 100자리로 표현할 수 있는 10진수 값은 읽을 수도 없을 정도로 큰 값이다
    * 컴퓨터 분야에서 로그의 밑은 항상 2

  * 2^x = n 은 같은 말

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321145746454.png" alt="image-20220321145746454" style="zoom:50%;" />

* 2진수 표현에서 logn 비트로 표현할 수 있는 숫자 범위는?
  * k = log n 비트
  * 2^k = n
  * ![image-20220321154215385](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321154215385.png)
  * 



![image-20220321164327003](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321164327003.png)



![image-20220321164822528](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321164822528.png)

![image-20220321165737937](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321165737937.png)

![image-20220321172339071](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321172339071.png)

![image-20220321172623321](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321172623321.png)

![image-20220321173253094](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321173253094.png)

![image-20220321173500505](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321173500505.png)



![image-20220321173918873](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321173918873.png)

![image-20220321185759551](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321185759551.png)

![image-20220321190043003](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321190043003.png)

![image-20220321191111963](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321191111963.png)

등비수열의 합

![image-20220321191433804](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220321191433804.png)
# Python Method

* 함수처럼 생각
* input과 output 



## 순서가 있는 데이터 구조

### 문자열(String)

* 문자열 조회/탐색 및 검증 메소드

  ![image-20220124133701803](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124133701803.png)

  * s.get() : 기본값이 없으면 Non을 반환
  * is 가 들어간다면 boolean 형(T/F)

* 예시

  * s.find(x): x의 첫 번째 위치를 반환 :question:

    ```python
    'apple'.find('p')
    ```

    1

    ```python
    'apple'.find('k')
    ```

    -1

  * s.index(x)

    ```python
    'apple'.index('p')
    ```

    1

    ```python
    'apple'.index('k')
    ```

    Value Error

  * s.isalpha() / s.isupper() / s.islower() / s.istitle()

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134441512.png" alt="image-20220124134441512" style="zoom:80%;" />

    ![image-20220124134547915](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134547915.png)

* 문자열 변경 메소드

  * :question: 문자 immutable??? => 해당하는 원본 문자를 변경시키는게 아니라 변경된 문자열의 값을 반환하는 것이므로 괜찮음

    ![image-20220124134716850](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134716850.png)

  * s.replace(old, new[,count])

    ```python
    'coone'.replace('o', 'a')
    ```

    ```python
    'woooooowoo'.replace('o', '!', 2)
    ```

    'w!!ooowoo'

  * s.strip([chars]) ==> login할 때 많이 쓰임

    ![image-20220124135451152](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124135451152.png)

  * s.split([chars])

    * map(int, input().split()) 

      input으로 들어온 문자열을 공백을 기준으로 쪼갠다. 리스트로 반환됨

    * sep이 None이거나 지정되지 않으면, 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음

    * maxsplit이 -1인 경우에는 제한이 없음

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124135532455.png" alt="image-20220124135532455" style="zoom:67%;" />

    ```python
    'a, b, c'.split(,)
    ```

    ['a', 'b', 'c']

  * :question: 'separator'.join([iterable])

    * 반복가능한 컨테이너 요소들을 seperator(구분자)로 합쳐 문자열 반환.
      * iterable에 문자열이 아닌 값이 있으면 TypeError발생

    ```python
    '!'.join('ssafy')
    ```

    's!s!a!f!y'

    ```python
    ' '.join(['3', '5'])
    ```

    '3 5'

    ```python
    numbers = ['1', '2', '3']
    # 출력: 1 2 3 
    #1. 반복문
    #for number in numbers:
    #    print(number, end='')
    #2. join(string메서드)
    #print(''.join(numbers))
    
    #2. 요소가 문자열이 아닌 경우
    #TypeError:sequence item 0: expected str instance, int found
    numbers = [1, 2, 3]
    print(''.join(numbers))
    print('.join(map(str, numbers))')
    ```

  * 문자열 변경 예시

    <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124140356925.png" alt="image-20220124140356925" style="zoom:80%;" />



### 리스트(List)

* 순서를 가지는 0개 이상의 객체를 참조하는 자료형

* 리스트메소드

  ![image-20220124140459882](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124140459882.png)

  * 리스트 요소를 변경시킬 수 있음

  * L.append(x)

    ```python
    cafe = ['starbucks', 'tomntoms', 'hollys']
    print(cafe)
    cafe.append('banapresso')
    print(cafe)
    ```

    ['starbucks', 'tomntoms', 'hollys']

    ['starbucks', 'tomntoms', 'hollys', 'banapresso']

    

  * L.extend(iterable)

    ```python
    cafe = ['starbucks', 'tomntoms', 'hollys']
    print(cafe)
    cafe.extend('banapresso')
    print(cafe)
    ```

    ['starbucks', 'tomntoms', 'hollys', 'c', 'o', 'f', 'f', 'e', 'e']

    

  * L.insert(i, x)

    ![image-20220124141017605](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141017605.png)

  * L.remove(x)

    ![image-20220124141051404](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141051404.png)

  * L.pop(i)

    ![image-20220124141110645](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141110645.png)

  * L.clear()

    ![image-20220124141156495](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141156495.png)

  * L.index(x)

    ![image-20220124141304193](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141304193.png)

  * L.count()

    ![image-20220124141334415](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141334415.png)

  * L.sort()

    ![image-20220124141357044](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141357044.png)

    ```python
    a = [100, 10, 1, 5]
    b = [100, 10, 1, 5]
    
    #1. .sort() (리스트.sort())
    #원본 리스트를 정렬시키고, None을 return
    print(a)
    print(a.sort())
    print(a)
    
    print('================')
    #[100, 10, 1, 5]
    #None
    #[1, 5, 10, 100]
    
    
    #2. 함수 sorted(리스트)
    # 원본 리스트는 변경 x, 정렬된 리스트를 return
    print(sorted(b))
    print(b)
    print(b)
    # [1, 5, 10, 100]
    
    
    
    #정렬을 시키고 싶다.
    a = [100, 2]
    a.sort()
    
    b = [100, 2]
    b = sorted(b)
    ```

    

  * L.reverse()

    ![image-20220124141430273](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141430273.png)

    * :star: 원본 자체의 순서를 뒤집는다 

    ```python
    a = [100, 2, 6]
    
    #정렬 후 reverse
    
    a.sort()
    print(a)
    a.reverse()
    print(a)
    ```

    [2, 6, 100]

    [100, 6, 2]



### 튜플(Tuple)

* 튜플은 변경할 수 없기 때문에 값에 영향을 미치지 않는 메소드만을 지원
* 리스트 메소드 중 항목을 변경하는 메소드들을 제외하고 대부분 동일



## 순서가 없는 데이터 구조

* 집합의 연산이 가능한 구조
* 

### 셋(Set)

* 셋 메소드

  ![image-20220124143552739](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143552739.png)

  * .add(elem)

    ![image-20220124143832537](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143832537.png)

  * update(*others)

    ![image-20220124143853560](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143853560.png)

  * remove(elem)

    ![image-20220124143907171](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143907171.png)

  * discard(elem)

    ![image-20220124143921169](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143921169.png)

  * .pop()

    ![image-20220124144107831](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144107831.png)

    * vs 리스트
    * 리스트: 인덱스로도 되고, 기본은 마지막
    * 셋: 임의의 원소를 제거해 반환(왜냐면 정의 자체가 순서가 없으므로)
    * 

### 딕셔너리(Dictionary)

* 딕셔너리 메소드

  ![image-20220124144316165](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144316165.png)

  * d.get(key[,default])

    ![image-20220124144353658](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144353658.png)

  * d.pop(key[,default])

    ![image-20220124144431000](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144431000.png)

    ![image-20220124144627257](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144627257.png)

  * .update()

    ![image-20220124144646072](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144646072.png)

    

    

## 얕은 복사와 깊은 복사 (Shallow Copy and Deep Copy)

### 할당(assignment)

* 대입 연산자(=)

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124145551857.png" alt="image-20220124145551857" style="zoom:67%;" />

### 얕은 복사

* slice 

### 깊은 복사 (Deep copy)

* ㅇㅇ

  ```python
  import copy
  a = [1, 2, ['a', 'b']]
  b = copy.deepcopy(a)
  print(a, b)
  b[2][0] = 0
  print(a, b)
  ```

  


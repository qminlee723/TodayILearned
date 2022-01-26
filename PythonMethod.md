# Python Method

* 함수처럼 생각
  - 객체(object) 안쪽에 정의된 함수
* input과 output 





---

## 순서가 있는 데이터 구조(Data Structure)

### 문자열(String Type)

#### 1. 문자열 조회/탐색 메소드

![image-20220124133701803](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124133701803.png)

* s.get() : 기본값이 없으면 Non을 반환
* is 가 들어간다면 boolean 형(T/F)



#### 예시

* **s.find(x)**: x의 첫 번째 위치를 반환, 만약 찾는 글자가 없으면 -1을 반환

  ```python
  'apple'.find('p')
  ```

  1

  ```python
  'apple'.find('k')
  ```

  -1

* **s.index(x)**: find와 같음. 단 없으면 Error

  ```python
  'apple'.index('p')
  ```

  1

  ```python
  'apple'.index('k')
  ```

  Value Error

  

#### 2. 문자열 관련 검증 메소드

*  **s.isalpha() / s.isupper() / s.islower() / s.istitle()**

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134441512.png" alt="image-20220124134441512" style="zoom:80%;" />

![image-20220124134547915](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134547915.png)



#### 3. 문자열 변경 메소드

![image-20220124134716850](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124134716850.png)

* 문자 immutable한데 변경이 가능한가??? 

  * 원본 문자 변경 X. :question:변경된 문자열의 값:question:을 반환하는 것이므로 괜찮음

  

* **s.replace(old, new[,count])**

  ```python
  'coone'.replace('o', 'a')
  ```

  'caane'

  ```python
  'woooooowoo'.replace('o', '!', 2) # count 지정시 해당 개수만큼만 시행
  ```

  'w!!ooowoo'

  

* **s.strip([chars])** 

  * ' ', '\t', '\n' 세 가지 다 공백으로 인식하여 공백 제거해준다. 
  * login 기능 만들 때 많이 쓰인다(불필요한 공백 제거해서 문자열 정리)

  ![image-20220124135451152](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124135451152.png)

  * 문자열 양쪽 제거(strip), 왼쪽 문자열만 제거(lstrip), 오른쪽 문자열만 제거(rstrip)

  

* **s.split([chars])**

  * :question: map(int, input().split()) 

    input으로 들어온 문자열을 공백을 기준으로 쪼갠다. 리스트로 반환됨

  * sep이 None이거나 지정되지 않으면, 연속된 공백문자를 단일한 공백문자로 간주하고, 선행/후행 공백은 빈 문자열에 포함시키지 않음

  * maxsplit이 -1인 경우에는 제한이 없음

    ```python
    'a, b, c'.split(,)
    ```

    ['a', 'b', 'c']

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124135532455.png" alt="image-20220124135532455" style="zoom:67%;" />

  

* **'separator'.join([iterable])**

  * 반복가능한 컨테이너 요소들을 seperator(구분자)로 합쳐 문자열 반환.
    * iterable에 문자열이 아닌 값이 있으면 TypeError발생
    * '글자들 '사이'로 들어가는 것'

  ```python
  '!'.join('ssafy')
  ```

  's!s!a!f!y'

  ```python
  ' '.join(['3', '5'])
  ```

  '3 5'

  :question::question::question::question::question::question::question::question::question:

  ```python
  numbers = ['1', '2', '3']
  # 출력: 1 2 3 
  #1. 반복문
  for number in numbers:
      print(number, end='')
  #2. join(string메서드)
  print(''.join(numbers))
  
  #2. 요소가 문자열이 아닌 경우
  #TypeError:sequence item 0: expected str instance, int found
  numbers = [1, 2, 3]
  print(''.join(numbers))
  print('.join(map(str, numbers))')
  ```



#### **문자열 변경 예시**

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124140356925.png" alt="image-20220124140356925" style="zoom:80%;" />



---

### 리스트(List)

* 순서를 가지는 0개 이상의 객체를 참조하는 자료형

#### 리스트메소드

![image-20220124140459882](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124140459882.png)

* **L.append(x)**

  ```python
  cafe = ['starbucks', 'tomntoms', 'hollys']
  print(cafe)
  cafe.append('banapresso')
  print(cafe)
  ```

  ['starbucks', 'tomntoms', 'hollys']

  ['starbucks', 'tomntoms', 'hollys', 'banapresso']

  * 리스트에 값을 추가함

  

* **L.extend(iterable)**

  ```python
  cafe = ['starbucks', 'tomntoms', 'hollys']
  print(cafe)
  cafe.extend('coffee')
  print(cafe)
  ```

  ```python
  cafe = ['starbucks', 'tomntoms', 'hollys']
  print(cafe)
  cafe.append('banapresso')
  print(cafe)
  ```

  ['starbucks', 'tomntoms', 'hollys']

  ['starbucks', 'tomntoms', 'hollys', 'c', 'o', 'f', 'f', 'e', 'e']

  * 리스트에 iterable 항목이 추가됨

    

* **L.insert(i, x)**

  * 정해진 index에 x를 추가함

  ![image-20220124141017605](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141017605.png)

  

* **L.remove(x)**

  * 리스트에서 값이 x 인 것 삭제
  * 없으면 Error

  ![image-20220124141051404](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141051404.png)

  

* **L.pop(i)**

  * 마지막 항목을 지움
  * 인덱스 지정하면 지정한 인덱스에 있는 것 지움

  ![image-20220124141110645](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141110645.png)

  

* **L.clear()**

  * 모든 항목을 삭제

  ![image-20220124141156495](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141156495.png)

  

* **L.index(x)**

  * x값을 찾아 해당 인덱스 값을 반환

  ![image-20220124141304193](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141304193.png)

  

* **L.count()**

  * 원하는 값의 갯수를 반환

  ![image-20220124141334415](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141334415.png)

  

* **L.sort(key)**

  * L.sort() 원본이 변경이 되지만

  * L.sort<u>ed</u>() 원본에는 변경이 없다.

  * (key) 부분에 어떻게 정의할지 함수를 정의해서 넣어주는 것 

    * 정의하지 않으면 첫번째 index를 기준으로 정렬이 된다.

      ```python
      my_list = [ [1, -2], [9, 4], [5, -6] ]
      ```

      [[1, -2], [5, -6], [9, 4]]

      ```python
      def my_key_func(elem):
      	return elem[1]
      
      my_list.sort(key=my_key_func)
      print(my_list)
      ```

      [[5, -6], [1, -2], [9, 4]]

    * lambda를 자주 이용한다(동일한 결과값 나옴)

      ```python
      my_list.sort(key=lambda x: x[1])
      print(my_list)
      ```

      [[5, -6], [1, -2], [9, 4]]

  ![image-20220124141357044](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141357044.png)

  ```python
  a = [100, 10, 1, 5]
  b = [100, 10, 1, 5]
  
  ####1. .sort() (리스트.sort())
  #원본 리스트를 정렬시키고, None을 return
  print(a)
  print(a.sort())
  print(a)
  
  print('================') # 출력값
  #[100, 10, 1, 5]
  #None
  #[1, 5, 10, 100]
  
  
  ####2. 함수 sorted(리스트)
  # 원본 리스트는 변경 x, 정렬된 리스트를 return
  print(sorted(b))
  print(b)
  # 출력값
  #[1, 5, 10, 100]
  #[100, 10, 1, 5]
  
  
  #정렬을 시키고 싶다.
  a = [100, 2]
  a.sort()
  
  b = [100, 2]
  b = sorted(b)
  ```

  

* **L.reverse()**

  * 순서를 반대로 뒤집는다(정렬하는 거 아니고, 주어진 리스트에서 반대로)

  ![image-20220124141430273](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124141430273.png)

  * :star: 원본 자체의 순서를 뒤집는다 

  ```python
  a = [100, 2, 6]
  
  #정렬 후 reverse 시키고 싶다면?
  
  a.sort()	#먼저 sort로 정렬시키고
  print(a)
  a.reverse()	#reverse 실행
  print(a)
  ```

  [2, 6, 100]

  [100, 6, 2]





---

### 튜플(Tuple)

* 튜플은 변경할 수 없기 때문에 값에 영향을 미치지 않는 메소드만을 지원

* 리스트 메소드 중 항목을 변경하는 메소드들을 제외하고 대부분 동일

  ![image-20220125111655479](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220125111655479.png)

  ```python
  a = (1, 2, 3)
  print(id(a)) 
  # 메모리에 객체가 어디에 할당이 되어있는지 알려주는 것이 id(주소)
  a += 1,
  print(id(a)) 
  # 위의 id값과 다른것이 나온다. 메모리에 두 개가 생성된 것을 알 수 있음
  # 왜냐면 튜플은 변경이 불가능하기 때문이다.
  
  print(a)
  print(type(a))
  ```

  (1, 2, 3, 1)

  <class 'tuple'>

  ```python
  ### 리스트의 경우
  
  a = [1, 2, 3]
  print(id(b)) 
  
  b.append(1)
  print(id(b))
  # 위의 id값과 같은 것이 나온다
  # List는 변경 가능하기 때문
  ```

  ```python
  a == b # 값을 비교
  a is b # id 주소 값을 비교
  ```

  

---

## 순서가 없는 데이터 구조

### 셋(Set)

#### 셋 메소드

![image-20220124143552739](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143552739.png)



#### 예제

* **.add(elem)**

  * 셋에 값을 추가
  * 순서가 없으므로 순서는 마음대로 출력

  ![image-20220124143832537](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143832537.png)

  

* **update(*others)**

  * 여러 값을 추가

  ![image-20220124143853560](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143853560.png)

  

* **remove(elem)**

  * 셋에서 삭제하고, 없으면 KeyError

  ![image-20220124143907171](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143907171.png)

  

* **discard(elem)**

  * 셋에서 삭제하고, 없어도 에러가 발생하지 않음

  ![image-20220124143921169](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124143921169.png)

  

* **.pop()**

  * 임의의 원소를 제거해 반환한다

  ![image-20220124144107831](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144107831.png)

  * Set.pop() vs List.pop()

    * List: 인덱스로도 되고, 기본은 마지막
    * Set: 임의의 원소를 제거해 반환(왜냐면 정의 자체가 순서가 없으므로)

    

### 딕셔너리(Dictionary)

#### **딕셔너리 메소드**

![image-20220124144316165](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144316165.png)



#### 예시

* **d.get(key[,default])**

  * key를 통해 value를 가져온다
  * KeyError가 발생하지 않으며, default 값을 설정할 수 있다.(기본:None)
    * dictionary['key'] ==> 여기서 key가 없는 키면 에러남. 그런데 get은 안남.

  ![image-20220124144353658](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144353658.png)

  

* **d.pop(key[,default])**

  * key가 딕셔너리에 있으면 제거하고 해당 값을 반환한다
  * 그렇지 않으면 default를 반환한다
  * default값이 없으면 KeyError

  ![image-20220124144431000](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144431000.png)

  ![image-20220124144627257](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144627257.png)

  

* **.update()**

  * 값을 제공하는 key, value로 덮어쓴다

  ![image-20220124144646072](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124144646072.png)

  

  

## 얕은 복사와 깊은 복사 (Shallow & Deep Copy)

### 1. 할당(assignment)

* 대입 연산자(=)

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220124145551857.png" alt="image-20220124145551857" style="zoom:67%;" />
  
  * original_list와 copy_list 둘 다 바뀌는가? 
  * 같은 메모리 주소 안에 저장이 되어 있는거임. 같은 메모리 주소를 각자 다른 리스트가 가리키게 한 것 
  * 메모리를 효율적으로 사용하기 위한 것
  * 해당 객체에 대한 객체 참조를 복사 :question:
  * 해당 주소의 일부 값을 변경하는 경우 이를 참조하는 모든 변수에 영향
  
  

### 2. 얕은 복사

* slice 연산자 활용하여 같은 원소를 가진 리스트지만 연산된 결과를 다른 주소에다 복사

* 복사하는 리스트의 원소가 주소를 참조하는 경우. 다른 주소가 같은 리스트를 바라본다.

  ![image-20220125112841085](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220125112841085.png)

  

### 3. 깊은 복사 (Deep copy)

* 원래의 리스트에 다시 접근하고 싶을 경우, 원래 리스트 살려 놓는 것

* deepcopy 많이 쓰면 space를 많이 잡아먹는다(memeory limit)

* 메모리를 새롭게 할당해서 copy list가 새로운 메모리를 바라보게 하는 것 

  ![image-20220125112922858](C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220125112922858.png)
  
* 따라서 copylist를 변경해도 원본도 바뀌지 않는다.

  ```python
  import copy
  
  original_list = [1, 2, ['a', 'b']]
  deep_list = copy.deepcopy(original_list) # 얘는 새로운 메모리에 
  
  print(id(original_list))
  print(id(copy_list))
  
  #다른 id가 나온다
  
  ```
  
  


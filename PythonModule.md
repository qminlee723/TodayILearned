# Python Module

## 모듈과 패키지

#### 모듈과 패키지

* 모듈
  * 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성한 것
* 패키지
  * 특정 기능과 관련된 여러 모듈의 집합
  * 패키지 안에는 또 다른 서브 패키지를 포함

#### 모듈과 패키지 불러오기

* import *module*

* from *module* import *var, function, Class*

* from *module* import *

  * "*" = 전체 ( 제대로 알고 싶다면 => [정규표현식](https://wikidocs.net/4308#dot))

* from *package* import *module*

* from *package.module* import *var, function, Class*

  ```python
  import random
  
  print(random.sample(range(1, 46), 6))
  #[29, 7, 1, 3, 35, 26]
  ```

  ```python
  import pprint
  a = {'a': ['apple', 'banana'], 'b': 'banana' 'c': 'car', 'd': 'drive', e: ['error', 'eat']}
  
  print(a)
  pprint.pprint(a)
  ```

  {'a': ['apple', 'banana'], 'b': 'banana', 'c': 'car', 'd': 'drive', 'e': ['error', 'eat']}

  {'a': ['apple', 'banana'],

  'b': 'banana',

  'c': 'car',

  'd': 'drive',

  'e': ['error', 'eat']}

  :question: 저 위에꺼랑 밑에꺼랑 다른게 뭐지?

  ```python
  from pprint import pprint # pprint
  ```

  





## 파이썬 표준 라이브러리

#### 파이썬 표준 라이브러리(Python Standard Library, PSL)

* [파이썬 표준 라이브러리](https://docs.python.org/3/library/index.html)

  

#### 파이썬 패키지 관리자(pip)

* PyPI(Python Package Index)에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템

* 패키지 설치

  * 최신/특정/최소 버전을 명시하여 설치할 수 있음

  * 이미 설치되어 있는 경우 설치되어 있음을 알리고 아무것도 하지 않음

    ```bash
    $ pip install SomePackage	# 가장 최신의 배포판을 인스톨
    $ pip install SomePackage>=1.0.4	#
    $ pip install 'Somepackage>=1.0.4'	#
    
    (SomePackage 버전 1.0.4보다 최신 버전을 설치)
    ```

* 패키지 삭제

  * 패키지를 업그레이드 하는 경우 과거 버전을 자동으로 지워줌

    ```bash
    $pip uninstall SomePackage
    ```

* 패키지 목록

  ```bash
  $pip list
  ```

* 패키지 정보

  ```bash
  $pip show SomePackage
  ```

* 패키지 freeze

  * 해당하는 목록을 requirements.txt으로 만들어 관리

  ```bash
  $pip freeze
  ```

* **패키지 관리하기**

  * (1) 패키지 목록 관리하고 (2) 설치 할 수 있음
  * 일반적으로, 패키지를 기록하는 파일의 이름은 requirements.txt로 정의
    * 저장된 requirements.txt를 협업하는 누군가와 공유하는데 쓰임

  ```bash
  # 내 컴퓨터에 설치된 패키지 목록을 txt파일로 변환시켜줌
  $pip freeze > requirements.txt
  ```

  ```bash
  # 누군가의 requirements.txt파일 안의 목록에 있는 패키지를 내 컴퓨터에 설피해줌
  $pip install -r requirements.txt
  ```



#### PyTorch

* An open source machine learning library based on the Torch library, used for applications such as computer vision and natural language processing, primarily developed by Facebook's AI Research lab(FAIR).
* 





## 사용자 모듈과 패키지

### 모듈

#### 모듈 만들기

* check.py에 짝수를 판별하는 함수(even)와 홀수를 판별하는 함수(odd)를 만들고, check 모듈을 활용해보시오.

  ```python
  NAME = 'SSAFY'
  
  def odd(n):
  	return n % 2 == 1
  	
  def even(n):
  	return n % 2 == 0
  ```

  

#### 모듈 활용하기

* check

  ```python
  import check import odd
  ```

  ```python
  from check import *
  ```

   

### 패키지

#### 패키지 만들기

* 여러 모듈/하위 패키지로 구조화

* :100: 모든 폴더에는 \_\_init\_\_.py를 만들어 패키지로 인식(python 3.3 부터는 파일이 없어도 되지만, 하위 버전 호환 및 프레임워크 등에서의 동작을 위해 파일 생성을권장한다. )

* 예시

  * math의 tools: 자연 상수 e, 원주율 pi 값, 최대값을 구하는 my_ max함수

  * statistics의 tools: 평균을 구하는 mean 함수

  * 폴더 구조

    ```bash
    my_package/
    	__init__.py
    	math/
    		__init__.py
    		tools.py
    	statistics/
    		__init__.py
    		tools.py
    ```

    ```python
    from my_package import math
    
    import my_package 
    ```

    





## 가상환경

### 가상환경

* 복수의 프로젝트를 하는 경우 버전이 상이할 수 있다
* 이러한 경우 가상환경을 만들어 프로젝트별로 독립적인 패키지를 관리할 수 있음

#### venv(virtual environment)

* 특정 디렉토리에 가상 환경을 만들어, 고유한 파이썬 패키지 집합을 가질 수 있음

  * 특정 폴더에 가상 환경이 있고
  * 실행환경(ex-bash)에서 가상환경을 활성화 시켜
  * 해당 폴더에 있는 패키지를 관리 사용가능

  ```bash
  $source venv/Scripts/activate
  (venv)
  ```

  

#### 가상환경 생성

* 가상환경을 생성하면, 해당 디렉토리에 별도의 파이썬 패키지가 설치됨
* $ python -m venv <폴더명>

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220120101533633.png" alt="image-20220120101533633" style="zoom: 50%;" />



#### 가상환경 활성화/비활성화

* <venv>는 가상환경을 포함하는 디렉토리의 경로
* <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220120101838896.png" alt="image-20220120101838896" style="zoom:67%;" />

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220120102357788.png" alt="image-20220120102357788" style="zoom: 50%;" />

<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220120102630421.png" alt="image-20220120102630421" style="zoom: 50%;" />

* 비활성화시: $ deactivate 명령어 사용

  <img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220120102747385.png" alt="image-20220120102747385" style="zoom:67%;" />

  

#### 가상환경 예시



<img src="C:\Users\Gyumin\AppData\Roaming\Typora\typora-user-images\image-20220119155211464.png" alt="image-20220119155211464" style="zoom:50%;" />

* bash shell 에서는 source 명령어를 사용!





## 유용한 패키지와 모듈



라이브러리 > 패키지 > 모듈 > 함수





##  






# Vue +Django

## :one: Server & Client

### 1. Server

### 2. Client



## :two: CORS

### 1. Same-origin policy(SOP)

#### 1) 기본 개념

* 동일 출처 정책
* 특정 출처(origin)에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용 하는 것을 제한하는 보안 방식
* 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄임



#### 2) Origin(출처)

* 두 URL의 Protocol, Port, Host가 모두 같아야 동일한 출처라 할 수 있음

* URL http://store.company.com/dir/page.html의 출처를 비교한 예시

  ![image-20220516132814614](Vue_+Django.assets/image-20220516132814614.png)



#### 3) Same-origin 예시

* Port까지의 주소가 같을 때 same-origin

![image-20220516132923786](Vue_+Django.assets/image-20220516132923786.png)



### 2. Cross-Origin Resource Sharing(CORS)

#### 1) 기본개념

* "교차 출처 리소스(자원) 공유"
* **추가 HTTP header**를 사용하여, 특정 출처에서 실행중인 웹 애플리케이션이 다른 출처의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제
* 리소스가 자신의 출처(Domain, Protocol, Port)와 다를 때 교차 출처 HTTP 요청을 실행
* 보안 상의 이유로 브라우저는 교차 출처 HTTP 요청을 제한(SOP)
  * 예를 들어, XMLHttpRequest는 SOP를 따름

* **다른 출처의 리소스를 불러오려면** 그 출처에서 **올바른 CORS header를 포함한 응답**을 반환해야 함 - 응답을 반환하는 건 서버 - 서버에서 header 설정을 해 줘야 하는 것



#### 2) CORS Policy

* 교차 출처 리소스(자원) 공유 정책
* 다른 출처(origin)에서 온 리소스를 공유하는 것에 대한 정책 <-> SOP



#### 3) 교차 출처 접근 허용하기

* CORS를 사용해 교차 출처 접근을 허용하기
* CORS는 HTTP의 일부로, 어떤 호스트에서 자신의 컨텐츠를 불러갈 수 있는지 서버에 지정할 수 있는 방법



#### 4) Why CORS? 

* 브라우저 & 웹 애플리케이션 보호
  * 악의적인 사이트의 데이터를 가져오지 않도록 사전 차단
  * 응답으로 받는 자원에 대한 최소한의 검증
  * 서버는 정상적으로 응답하지만, 브라우저에서 차단
* Server의 자원관리
  * 누가 해당 리소스에 접근할 수 있는지 관리 기능



#### 5) How CORS?

* CORS 표준에 의해 추가된 HTTP Header를 통해 이를 통제
* CORS HTTP 응답 헤더 예시
  * **`Access-Control-Allow-Origin /`**
  * ` Access-Control-Allow-Credentials /` 
  * ` Access-Control-Allow-Headers /` 
  * ` Access-Control-Allow-Methods`



#### 6) Access-Control-Allow-Origin 응답 헤더

* 이 응답이 주어진 출처(origin)로부터 요청 코드와 공유될 수 있는지를 나타냄
* 예시
  * `Access-Control-Allow-Origin: *`
  * 브라우저 리소스에 접근하는 임의의 origin으로부터 요청을 허용한다고 알리는 응답에 포함
  * '*' 는 모든 도메인에서 접근할 수 있음을 의미
  * '*' 외에 특정 origin 하나를 명시할 수 있음



#### 7) CORS 시나리오 예시

* `http://localhost:8080`(Vue.js)의 웹 컨텐츠가 `https://lab.ssafy.com`(Django) 도메인의 컨텐츠를 호출하기를 원하는 상황

* 요청 헤더의 Origin을 보면, localhost:8080으로부터 요청이 왔다는 것을 알 수 있음

* 서버는 이에 대한 응답으로, Access-Control-Allow-Origin 헤더를 다시 전송

* 만약 서버 리소스 소유자가 오직 localhost:8080의 요청에 대해서만 리소스에 대한 접근을 허용하려는 경우, '*'가 아닌 Access-Control-Allow-Origin: localhost:8080을 전송해야 함

  ![image-20220516162353507](Vue_+Django.assets/image-20220516162353507.png)

1. Vue.js에서 A 서버로 요청
2. A 서버는 Access-Control-Allow-Origin에 특정한 origin을 포함시켜 응답
   * 서버는 CORS Policy와 직접적인 연관이 없고, 그저 요청에 응답함
3. 브라우저는 응답에서 Access-Control-Allow-Origin을 확인 후 허용 여부를 결정
4. 프레임워크별로 이를 지원하는 라이브러리가 존재
   * django는 django-cors-headers 라이브러리를 통해 응답 헤더 및 추가 설정 가능



#### 8) django-cors-headers 라이브러리

```bash
$ pip install django-cors-headers
```

```python
# settings.py
INSTALLED_APPS = [
    ...
    'corsheaders',
    ...
]

MIDDLEWARE = [
    ...
    # CommonMiddleware보다 위에 위치
    'corsheaders.middleware.CorsMiddleware',
    ...
    'django.middleware.common.CommonMiddleware',
    ...
]

# 교차 출처 자원 공유를 허용할 도메인 등록
CORS_ALLOWED_ORIGINS = [
    'http://localhost:8080',
]
```



* 응답에 CORS header를 추가해주는 라이브러리
* 다른 출처에서 보내는 Django 애플리케이션에 대한 브라우저 내 요청을 허용함
* Django App 이 header 정보에 CORS를 설정한 상태로 응답을 줄 수 있게 도와주며, 이 설정을 통해 브라우저는 다른 origin에서 요청을 보내는 것이 가능해짐





## :three: Authentication & Authrization

### 1. Authentication

* 인증, 입증
* 자신이라고 주장하는 사용자가 누구인지 확인하는 행위
* 모든 보안 프로세스의 첫 번째 단계(가장 기본 요소)
* 즉, 내가 누구인지를 확인하는 과정
* 401 Unauthroized
  * 비록, HTTP 표준에서는 "미승인(unauthorized)"을 하고 있지만, 의미상 이 응답은 "비인증(unauthenticated)"를 의미

### 2. Authorization

* 권한 부여, 허가
* 사용자에게 특정 리소스 또는 기능에 대한 액세스 권한을 부여하는 과정(절차)
* 보안 환경에서 권한 부여는 항상 인증을 따라야 함
  * 예를 들어, 사용자는 조직에 대한 액세스 권한을 부여 받기 전에 먼저 자신의 ID가 진짜인지 먼저 확인해야 함
* 서류의 등급, 웹 페이지에서 글을 조회 & 삭제 & 수정할 수 있는 방법, 제한 구역
  * 인증에 되었어도 모든 권한을 부여 받는 것은 아님
* 403 Forbidden
  * 401과 다른 점은, 서버는 클라이언트가 누구인지 알고 있음



### 3. Authentication vs Authorization

* Authentication(인증)
  * Authentication is the process of verifying who a user is
  * 401 Unauthrized
  * 자신이라고 주장하는 유저 확인
  * Credential(비밀번호, 얼굴 인식) 검증
  * Django -> 게시판 서비스 로그인
  * 인증 이후에 획득하는 권한 (생성, 수정, 삭제)
* Authorization(권한/허가)
  * "Authorization is the process of verifying what they have access to"
  * 403 Forbidden
  * 유저가 자원에 접근할 수 있는지 여부 확인
  * 규칙/규정에 의해 접근할 수 있는지 확인
  * Django -> 일반 유저 vs 관리자 유저
  * 인증 이후에 부여되는 권한
    * 예시 - 로그인 후 글 작성 여부



### 4. Authentication and authorization work together

* 회원 가입을 하고 로그인을 하면 할 수 있는 권한 생성
  * 인증 이후에 권한이 따라오는 경우가 많음
* 단, 모든 인증을 거쳐도 권한이 동일하게 부여되는 것은 아님
  * Django에서 로그인을 했더라도, 다른 사람의 글까지 수정/삭제가 가능하진 않음
* 세션, 토큰, 제 3자를 활용하는 등의 다양한 인증 방식이 존재





## :four: DRF Authentication

### 1. 다양한 인증 방식

* Session Based
* **Token Based**
  * Basic Token
  * JWT
* Oauth
  * google
  * facebook
  * github...



### 2. Basic Token Authentication



### 3. Basic Token Based

![image-20220516205825246](Vue_+Django.assets/image-20220516205825246.png)



### 4. JWT

* JSONO Web Token
* JSON 포맷을 활용하여 요소 간 안전하게 정보를 교환하기 위한 표준 포맷
* 암호화 알고리즘에 의한 디지털 서명이 되어 있기 때문에 JWT 자체로 검증 가능
* JWT 자체가 필요한 정보를 모두 갖기 때문에(self-contained), 이를 검증하기 위한 다른 검증 수단(ex. table)이 필요 없음
* 사용처
  * Authentication, Information Exchange
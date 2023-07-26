# 🎯 Dart 입문하기

## 1.1 다트 소개

#### 다트의 장점

* UI를 제작하는데 최적화되어 있음
* 완전한 비동기 언어이며, 이벤트 기반

- Isolate를 이용한 동시성 기능도 제공
- Null Safety, Spread Operator, Collection if 등 효율적으로 UI를 코딩할 수 있는 기능제공
- 핫 리로딩을 통해 코드의 변경 사항을 즉시 화면에 반영해 효율적인 개발 환경
- 멀티 플랫폼에서 로깅, 디버깅하고 실행 가능
- AOT 컴파일이 가능하며, 어떤 플랫폼에서든 빠른 속도 
- 자바스크립트로의 완전한 컴파일 지원
- 백엔드 프로그래밍 지원

#### 컴파일 방식

- JIT(Just In Time) 컴파일 방식
  - 다트 가상 머신에서 제공하는 기능
  - 빠르게 개발이 가능하여 효율적임
  - 핫 리로드(Hot Reload) 기능
    - 코드의 변경된 사항을 처음부터 다시 컴파일할 필요 없이 즉시 화면에 반영
  - 실시간으로 메트릭스(Metrics)를 확인할 수 있는 기능
  - 디버깅 기능
- AOT(Ahead of Time) 컴파일 방식
  - 소프트웨어를 배포할 때는 컴파일이 돼 있어야 리소스를 효율적으로 사용가능
  - ARM64나 x64 기계어로 다트 언어가 직접 컴파일이 되어서 매우 효율적으로 프로그램을 실행할 수 있다



## 1.2 문법 공부 환경 안내

### 1.2.1 다트패드에서 문법 공부

### 1.2.2 안드로이드 스튜디오에서 문법 공부하기

1. `Main.dart` 파일

   ```dart
   void main() {
     print('hello world');
   }
   ```

2. Terminal 실행 명령어

   ```
   dart lib/main.dart
   ```



## 1.3 기초 문법

### 1.3.1 메인 함수

- 엔트리 함수 기호 `main()` 사용

  ```dart
  void main() {
    
  }
  ```

  - void 는 아무 값도 반환하지 않는다는 뜻
  - 괄호 안에 매개변수 지정 가능



### 1.3.2 주석

* `//`, `/* */`, `///`

  ```dart
  // 한 줄 주석
  
  /*
   * 여러 줄 주석
   * 필수는 아니고, 관행상 중간 줄의 시작으로 * 사용
   */ 
   
  /// 문서 주석을 작성 가능
  /// DartDoc이나 안드로이드 스튜디오같은 IDE에서
  /// 문서로 인식
  ```

  

### 1.3.3 print() 함수

```dart
void main() {
  print('Hello World');
}
```



### 1.3.4 var를 사용한 변수 선언

- 변수는  `var`을 사용해 선언
- 타입 추론 기능을 제공하기 때문에 명시적으로 타입 선언하지 않아도 됨
- 실제 코드가 컴파일 될 때 추론된 타입으로 var가 치환됨

```dart
void main() {
  var name = '이규민';
  print(name);
  
  // 변숫값 변경 가능
	name = '이서윤';
	print(name);
	
  // 변수명 중복은 불가능
}
```



### 1.3.5 dynamic을 사용한 변수 선언

- `dynamic` 키워드를 사용하면 변수의 타입이 고정되지 않아 다른 타입의 값을 저장할 수 있다

```dart
void main() {
  dynamic name = '이규민';
  name = 1;
}
```



### 1.3.6 final/const를 사용한 변수 선언

- `final`, `const` 로 선언한 변수는 선언 후 값 변경이 불가능

  ```dart
  void main() {
    final String name = '블랙핑크';
    name = 'BTS'; // Error. final로 선언한 변수는 선언 후 값 변경이 불가능
    
    const String name2 = 'BTS';
    name = '블랙핑크'; // Error. const로 선언한 변수는 선언 후 값 변경이 불가능
  }
  ```

- `final`은 런타임, `const`는 빌드타임 상수

  ```dart
  void main() {
    final DateTime now = DateTime.now();
    print(now); 
  }
  ```

  ```dart
  void main() {
    const DateTime now = DateTime.now();
    print(now); // 에러
  }
  ```

  - `const` 로 지정한 변수는 빌드타임에 값을 알 수 있어야 하는데, `DateTime.now()`함수는 런타임에 반환되는 값을 알 수 있음



### 1.3.7 변수 타입

```dart
void main() {
  // String - 문자열
  String name = '이규민';
  
  // int - 정수
  int isInt = 10;
  
  // double - 실수
  double isDouble = 2.5;
  
  // bool - 불리언(true/false)
  bool isTrue = true;
  
  print(isInt); //10
  print(isDouble); // 2.5
  print(isTrue); // true
}
```

## 1.4 컬렉션

> 컬렉션은 여러 값을 하나의 변수에 저장할 수 있는 타입
>
> List, Map, Set
>
> 서로의 타입으로 자유롭게 형변환이 가능하다

### 1.4.1 List 타입





####  add() 함수

```dart
void main() {
  List<String> blackPinkList = ['리사', '지수', '제니', '로제'];
  blackPinkList.add('규민'); // 리스트 끝에 추가
  print(blackPinkList); // [리사, 지수, 제니, 로제, 규민]
}
```



#### where() 함수




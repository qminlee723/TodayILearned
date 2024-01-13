# [Course1] 블로그 앱 프로젝트

## 프로젝트 개요

### 1. 프로젝트 개요 및 목적

#### 프로젝트 개요

- React 앱의 구조와 라우팅을 이해하고, 직접 프로젝트 설계
- Firebase의 기본 개념을 익히고 CRUD 원리를 이해
- Firebase로 사용자 인증 구현, 간단한 쿼리 적용 등 심화 기능 적용
- 전역 상태 관리의 필요성과 context API 사용법 이해
- 스타일링 방법론을 알아보고, 직접 스타일링 적용

#### 사용기술

- create-react-app
- React-router-dom
- Firebase auth를 이용한 사용한 인증
- Firebase FIrestore를 이용한 CRUD
- css BEM(Block, Element, Modifier)구조
- Context API를 이용한 상태관리(다크모드, 사용자 인증)
- Firebase CLI로 배포

### 흐름도

![Screenshot 2024-01-13 at 11.12.08 PM](./assets/Screenshot 2024-01-13 at 11.12.08 PM.png)



### 2. 완성 프로젝트 미리보기

- 서비스 주소: https://react-blog-6fd95.web.app/
- github: https://github.com/jen-frontend/fastcampus-react-blog



### 3. 프로젝트 구조

#### 라우팅

- /
- /login
- /signup
- /profile
- /posts
- /posts/[id]
- /posts/new
- /posts/edit/[id]



#### 컴포넌트

- Carousel
- Header
- Loader
- Footer
- PostFrom
- SignupForm
- LoginForm
- PostDetail
- PostList
- Profile
- Comments



#### 폴더 구조

- src안에  pages, component
- components: 공통 컴포넌트
- context: 사용자 인증, 다크모드 상태 관리
- interface: 타입 인터페이스
- pages: 페이지
- firebaseApp: 파이어베이스 설정



## 프로젝트 세팅



## 컴포넌트 만들기



## 사용자 인증 구현



## 게시판 CR(Create, Read) 구현



## 게시판 UD(Update, Delete) 구현



## 다크모드 구현



## 댓글 기능 구현



## 보안 확인하기



## 배포하기




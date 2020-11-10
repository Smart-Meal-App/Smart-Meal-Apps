<!-- @format -->

# Smart-Meal-Apps

## 목차

1. **[개요](#개요)**
2. **[기능](#기능)**<br>
  2-1. [메인](#메인)<br>
  2-2. [서브](#서브)<br>
3. **[구상](#구상)**<br>
  3-1. [sign in](#sign-in)<br>
  3-2. [회원정보](#회원정보)<br>
4. **[화면](#화면)**<br>
  4-1. [인덱스](#인덱스)<br>
  4-2. [로그인, 회원가입](#로그인,-회원가입)<br>
  4-3. [검색](#검색)<br>
  4-4. [제품 정보](#제품-정보)<br>
  4-5. [리뷰](#리뷰)<br>
  4-6. [리뷰 작성](#리뷰-작성)<br>
  4-7. [제품 비교](#제품-비교)<br>
  4-8. [도움말](#도움말)<br>
  4-9. [보류](#보류)<br>
  

## 개요

요즈음 `식품 문제가 대두`되며 자신도 몰랐던 여러 식품의 정보를 알게 되었으며,
피부 질환이나 아토피가 있는 사람들은 자신에게 맞는 식품을 섭취하기 위해
애쓰고 있으며 평균 수명도 길어지면서 건강을 챙기려는 사람들이 많아졌다.

하지만 관련 정보를 찾아보면 하나하나 찾아야 하는 번거로움과
식품에 들어있는 성분이 나쁜 지 좋은 지 `알아보는 시간과 노력`이 많이 들어간다.

또한 식사시간마다 메뉴를 정하는게 귀찮기에 메뉴를 추천해주고자 한다.
해당 문제를 해결하기 위해 `식품 성분을 모아놓고 관련 정보를 제공하는 앱`을 만들게 되었다.

## 기능

### 메인
아래의 3가지를 입력받고 식단을 추천해주는 것
1. 원하는 가격대
2. 건강상태
3. 알레르기 및 피부병 단위

위에서 추천받은 정보는 2가지로 나뉜다.
1. 가정식
  - 이 경우 재료를 기준으로 가격대를 정한다.
2. 외식
  - 이 경우 각 식당들의 가격 평균값으로 정한다.

### 서브

- 신고글 작성 기능
  1. 신고 버튼을 누른다.
  2. 글의 주제를 선택한다.
  3. 신고 내용을 작성한다.
  4. 보낸다
  5. 끄읏
  
- 리뷰 기능
  - 별점
  - 게시글 (맛, 건강, 꿀팁 등)
  
- 유사제품 비교
  - 유해성분 오름차순
  
- 식품 별 **구성 성분** 정보 제공 및 **부가정보** 표시(_예시 이 제품은 아토피를 유발할 수 있습니다._)
  - 유해성분, 유익성분 표시
    - 유해성분은 _빨강_, 유익성분은 _초록_
    - 보기좋게 정리

  - 알레르기, 피부병 **유발 성분** 표시
    - 텍스트 형식

## 구상

### sign in

- Naver, Kakao, Google 지원
- 회원가입 정보
  - 필수 : id, pass, email, 이름
  - 선택 : 프로필사진, 닉네임

### 회원정보(회원가입 한 뒤에 입력)

방식 : 회원가입 후 입력 창 표시

- 알레르기, 아토피, 피부병 유무
  - 관련 정보
- 음식 정보
  - 좋아하는 음식
  - 싫어하는 음식
  - 선호하는 음식 종류(한식, 중식, 일식, 양식 중 택일)

## 화면

### 인덱스

### 로그인, 회원가입

### 검색

### 제품 정보

### 리뷰

### 리뷰 작성

### 제품 비교

### 도움말

### 보류

- 테마
- 랜덤 식품 룰렛
  - 싫어하는 음식 제외한 건강음식으로 랜덤 룰렛

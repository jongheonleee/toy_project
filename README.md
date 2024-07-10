# 📚 toy_project 

> ### 소중한 지식을 미래에게 연결해주는 IT/컴퓨터 서적 전문 업체
> ### 프로그래밍 공부하다 보면, 좋은 책을 구하는게 어렵다. 그 이유는 진입장벽을 낮추고 많은 양의 책을 판매하려는 구조를 갖추고 있기 때문
> ### 우리는 이를 타파한다. 소중한 책들을 누군가에게 연결해주는 가치를 선사하는 쇼핑몰이다.

<br>

> ### 🙋🏻‍♂️ 내가 맡은 파트 : 쿠폰, 상품
> ### 📅 세부 일정 
> - 수요일
>    [ ] 각자 맡은 파트 마무리
>      - 요구사항 정의, ERD, 화면 정의서, 표준 용어, 도메인, 코드 …
> - 목요일
>    [ ] 팀 내 자체 검토 -> 컬럼, 도메인 체크
>    [ ] 피드백 반영
> - 금요일
>    [ ] 발표 준비 -> 자료 정리

<br>

## 🏃🏻 현재 진행 현황
(erd-cloud 작업 링크 : https://www.erdcloud.com/d/kefpypfDzSH6TGWhd) 

- [쿠폰 ERD]
- <img src="https://github.com/jongheonleee/toy_project/assets/87258372/f1fb86a6-2519-4297-bddd-822de0b5bdac" width="500" height="500"/>


- [상품 ERD]
- <img src="https://github.com/jongheonleee/toy_project/assets/87258372/c8f82e25-add9-496f-bfef-39b6ff4ff312" width="500" height="500"/>



<br>

## 요구사항 정의
> ### 1. 🍀 쿠폰
> ### 2. 📖 상품

### 1-1. 🍀 쿠폰 

- 쿠폰 정의 : 회원(내국인, 외국인)에게 발급, 상품 가격 할인 및 다양한 혜택을 누릴 수 있는 우대권
    - 사용 대상 : 회원 기준으로 발급. 또한, 특정 쿠폰은 회원 등급에 따라 제한
    - 적용 대상 
      - (1) 해외 주문 도서 적용 안됨
      - (2) 매장 쿠폰은 사용자에게 동의 받고 사용
      - (3) 무료 배송 쿠폰은 구매금액 제한 x
      - (4) 무료 배송 쿠폰은 국내만 허용 가능하며 1일 1회 
      - (5) 도서정가제 적용 대상에서 이미 10% 할인되어 있으면, 쿠폰 사용 불가(가격 할인해주는 쿠폰)  
      - (6) 온라인/오프라인 통합 쿠폰은 도서 및 상품에 따라 사용 제한, 오프라인은 도서만 가능 

<br>

- 쿠폰은 크게 4 가지로 구분
  - (1) 상품쿠폰 : 상품 별로 쿠폰이 적용, 쿠폰에 따라 1개 혹은 주문 수량에 맞게 적용 -> 가격 할인
  - (2) 주문쿠폰 : 주문이 발생했을 때 적용, 주문시 1장만 사용 가능 -> 가격 할인
  - (3) e-book 쿠폰 : e-book 상품 대상으로 적용할 수 있는 쿠폰, 할인 혜택  -> 가격 할인
  - (4) 배송쿠폰 : 상품 구매시 배송비 할인 혜택을 받음 


<br>

- 쿠폰은 크게 3 가지 유형으로 나뉨
  - (1) 온라인/오프라인 통합쿠폰 : 둘 다 사용 가능 
  - (2) 온라인 전용 쿠폰 : 온라인만 적용 
  - (3) 매장쿠폰 : 오프라인, 매장에만 적용

    
<br>
<br>
    
### 1-2. 쿠폰 정책

<br>

- 현재 파악한 정책 요소(지속적으로 업데이트)
  - (1) 쿠폰 사용 제한 : A 상품을 구매할 때 B 쿠폰을 몇 개 사용할 수 있는지 
  - (2) 적립금 동시 적용 가능 여부 : 적립금과 B 쿠폰을 동시에 적용 가능한지 
  - (3) 주문시 동시 사용 가능 여부 : 상품 자체적으로 적용된 쿠폰이 아닌, 주문 시점에 적용 가능한 쿠폰인지 
  - (4) 취소 반품시 쿠폰 복원 가능 여부 : 주문이 취소/반품이 일어났을 때 쿠폰 복원 가능한지
  - (5) 쿠폰 사용 개수 제한 : B 쿠폰을 몇 개 사용할 수 있는지 제한 
  - (6) 사용 범위 : 어느 범위까지 사용 가능한 쿠폰인지, 온라인, 오프라인, 통합, 매장 
  - (7) 사용 가능 회원 등급 : 어느 회원 등급부터 적용 가능한 쿠폰인지 

<br>


### 2-1. 📖 상품

<br>

- 상품 정의 : IT/컴퓨터 관련 도서 상품과 사은품으로 구성
  - (1) 도서 상품 : IT/컴퓨터 서적 국한 
      - 국내, 해외 도서 모두 포함. 또한, 연령제한 있어도 도서 상품으로 정의. 전자도서, 원서도 포함
      - 다만, 해외에서 직구해오는 도서 상품은 상품으로 정의안함

  - (2) 사은품
      - 이벤트에서 제공하는 부속품. 종류 상관없음
    
<br>

- 상품 카테고리 분류
  - 숫자 두 자리로 구분한다. 예를들어, 상품 카테고리코드는 4자리 숫자 0101 -> 01(국내) - 01(컴퓨터 공학). 즉, '국내 컴퓨터 공학 서적'을 의미함      
  - 대 : 국내/해외
  - 중 : 컴퓨터공학, IT 일반, 컴퓨터입문/활용, OS, 네트워크, 보안/해킹, 데이터베이스, 웹 프로그래밍, 프로그래밍 언어, 모바일프로그래밍, 

<br>

- 국내 : 01
  - 컴퓨터공학 : 01
  - IT 일반 : 02
  - 컴퓨터입문/활용 : 03
  - OS : 04
  - 네트워크 : 05
  - 보안/해킹 : 06
  - 데이터베이스 : 07
  - 웹 프로그래밍 : 08
  - 프로그래밍 언어 : 09
  - 모바일 프로그래밍 : 10

- 해외 : 02
  - (위와 동일)

<br>
    

## 설계 -> 개념 모델링 & 논리 모델링

## 구현 -> 물리 모델링 

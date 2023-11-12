## 미션 - 크리스마스 프로모션

- 미션은 기능 요구 사항, 프로그래밍 요구 사항, 과제 진행 요구 사항 세 가지로 구성되어 있다.
- 12월 이벤트를 위한 개발 요청

<br>

메뉴

```
<애피타이저>
양송이수프(6,000), 타파스(5,500), 시저샐러드(8,000)

<메인>
티본스테이크(55,000), 바비큐립(54,000), 해산물파스타(35,000), 크리스마스파스타(25,000)

<디저트>
초코케이크(15,000), 아이스크림(5,000)

<음료>
제로콜라(3,000), 레드와인(60,000), 샴페인(25,000)
```

<br>

## 기능 요구사항 목록

### 변수

- 날짜와 메뉴
- 주문 메뉴
- 할인 전 총주문 금액
- 증정 메뉴
- 혜택 내역
- 총혜택 금액
- 할인 후 예상 결제 금액
- 12월 이벤트 배지 내용

<br>

### 날짜 객체 생성

- [x] 이벤트의 년도, 월을 통해서 이벤트 달력을 생성한다.
- [ ] 크리스마스 디데이 할인. (크리스마스 디데이 유무)
  - [ ] 12월 1일부터 25일까지 적용
  - [ ] 1,000원으로 시작하여 크리스마스가 다가올수록 날마다 할인 금액이 100원씩 증가
        (1일 0원, 2일 100원, ..., 25일 2,400원 할인)
- [ ] 별이 있으면 총주문 금액에서 1,000원 할인 (특별할인 (별표) 유무)
- [ ] 평일 / 주말 할인 (평일 / 주말 할인 유무)

```
[{
    "date": 1~31,
    "day" : 0~6
    "hasChristmas": true,
    "hasSpecial": true,
    "hasWeekend": false
}, {} ...]
```

<br>

### 메뉴 객체 생성

- [ ] 메뉴판에 있는 메뉴 등록
- [ ] 카테고리, 이름, 가격

<br>

### 방문 날짜 입력기능

- [ ] 식당 예상 방문 날짜를 입력받는다.
- [ ] 입력받은 방문날짜를 미리보기 날짜에 출력한다.

[예외 처리]

- [ ] 방문할 날짜는 1 이상 31 이하의 숫자로만 입력받아 주세요.
- [ ] 1 이상 31 이하의 숫자가 아닌 경우, "[ERROR] 유효하지 않은 날짜입니다. 다시 입력해 주세요."

<br>

### 메뉴 입력 기능

- [ ] 주문 메뉴를 입력받는다.

[예외 처리]

- [ ] 고객이 메뉴판에 없는 메뉴를 입력하는 경우, "[ERROR] 유효하지 않은 주문입니다. 다시 입력해 주세요."
- [ ] 메뉴의 개수는 1 이상의 숫자만 입력되도록 해주세요. 이외의 입력값은 "[ERROR] 유효하지 않은 주문입니다. 다시 입력해 주세요."
- [ ] 메뉴 형식이 예시와 다른 경우, "[ERROR] 유효하지 않은 주문입니다. 다시 입력해 주세요."
- [ ] 중복 메뉴를 입력한 경우(e.g. 시저샐러드-1,시저샐러드-1), "[ERROR] 유효하지 않은 주문입니다. 다시 입력해 주세요."
- [ ] 음료만 주문 시, 주문할 수 없습니다.
- [ ] 메뉴는 한 번에 최대 20개까지만 주문할 수 있습니다. (e.g. 시저샐러드-1, 티본스테이크-1, 크리스마스파스타-1, 제로콜라-3, 아이스크림-1의 총개수는 7개)

<br>

### 주문 메뉴 출력 기능

- [ ] 주문 메뉴와 갯수를 출력한다.

<br>

### 할인전 총주문 금액 기능

- [ ] 주문 메뉴와 갯수를 통해 할인 전 총주문 금액을 계산한다.
- [ ] 총금액은 쉼표(,)를 기준으로 3자리마다 쉼표(,)를 출력하고 원을 붙여 출력한다.
- [ ] 총주문 금액 10,000원 이상부터 이벤트가 적용됩니다.

<br>

### 증정 메뉴 기능

- [ ] 할인 전 총주문 금액이 12만 원 이상일 때, 샴페인 1개 증정한다.
- [ ] 증정 이벤트에 해당하지 않는 경우, 증정 메뉴 "없음"

<br>

### 혜택 내역 기능

- [ ] 입력받은 날짜의 이벤트 내역을 출력한다.
  - [ ] 크리스마스 디데이 할인
  - [ ] 평일 할인
  - [ ] 특별 할인
  - [ ] 증정 이벤트
- [ ] 총금액은 쉼표(,)를 기준으로 3자리마다 쉼표(,)를 출력하고 원을 붙여 출력한다. 앞에 음수(-)를 붙여 출력한다.
- [ ] 적용된 이벤트가 하나도 없다면 혜택 내역 "없음"

- 크리스마스 디데이 할인
  - 이벤트 기간: 2023.12.1 ~ 2023.12.25
  - 1,000원으로 시작하여 크리스마스가 다가올수록 날마다 할인 금액이 100원씩 증가
  - 총주문 금액에서 해당 금액만큼 할인 (e.g. 시작일인 12월 1일에 1,000원, 2일에 1,100원, ..., 25일엔 3,400원 할인)
- 평일 할인(일요일~목요일): 평일에는 디저트 메뉴를 메뉴 1개당 2,023원 할인
- 주말 할인(금요일, 토요일): 주말에는 메인 메뉴를 메뉴 1개당 2,023원 할인
- 특별 할인: 이벤트 달력에 별이 있으면 총주문 금액에서 1,000원 할인
- 증정 이벤트: 할인 전 총주문 금액이 12만 원 이상일 때, 샴페인 1개 증정
- 이벤트 기간: '크리스마스 디데이 할인'을 제외한 다른 이벤트는 2023.12.1 ~ 2023.12.31 동안 적용

<br>

### 총혜택 금액 기능

- [ ] 총혜택 금액 = 할인 금액의 합계 + 증정 메뉴의 가격
- [ ] 총혜택 금액에 따라 다른 이벤트 배지를 부여한다.
- [ ] 총금액은 쉼표(,)를 기준으로 3자리마다 쉼표(,)를 출력하고 원을 붙여 출력한다. 앞에 음수(-)를 붙여 출력한다.

<br>

### 할인 후 예상 결제 기능

- [ ] 할인 후 예상 결제 금액 = 할인 전 총주문 금액 - 할인 금액
- [ ] 총금액은 쉼표(,)를 기준으로 3자리마다 쉼표(,)를 출력하고 원을 붙여 출력한다.

<br>

### 12월 이벤트 배지 기능

- [ ] 총혜택 금액에 따라 이벤트 배지를 부여한다.
- [ ] 이벤트 배지는 별, 트리, 산타 세 가지가 있다.
  - 5천 원 이상: 별
  - 1만 원 이상: 트리
  - 2만 원 이상: 산타
- [ ] 이벤트 배지가 부여되지 않는 경우, "없음"

<br>

## 프로그래밍 요구사항 목록

- [x] Node.js 18.17.1 버전에서 실행 가능해야 한다. Node.js 18.17.1에서 정상적으로 동작하지 않을 경우 0점 처리한다.
- [ ] 프로그램 실행의 시작점은 App.js의 run 메서드이다.
- [x] indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다
- [x] 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
- [ ] Jest를 이용하여 본인이 정리한 기능 목록이 정상 동작함을 테스트 코드로 확인한다.
- [ ] else를 지양한다
- [ ] 도메인 로직에 단위 테스트를 구현해야 한다. 단, UI(Console.readLineAsync, Console.print) 로직에 대한 단위 테스트는 제외한다.
- [ ] 사용자가 잘못된 값을 입력할 경우 throw문을 사용해 예외를 발생시킨다. 그런 다음, "[ERROR]"로 시작하는 에러 메시지를 출력하고 해당 부분부터 입력을 다시 받는다.

<br>

## 추가된 요구사항 목록

- [ ] 제공되는 InputView, OutputView 객체를 활용해 구현한다.
  - [ ] 입력과 출력을 담당하는 객체를 별도로 구현한다.
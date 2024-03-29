### 기본 특징

자바스크립트의 변수는 기본적으로 **선언**이 되고 할당에 의해 **초기화**가 됨

- **var**
  - 선언 후 초기값이 없을 경우 자동으로 **undefined로 초기화**되기 때문에
  - **선언 라인 이전에 변수를 참조**해도 에러가 발생하지 않음
- **let과 const**
  - 선언 라인 이전에 변수를 참조할 수 없는 **일시적 사각지대(TDZ) 구간**을 가짐
- **let**
  - **선언만 하는 것도 가능**하지만 var처럼 **자동으로 초기화되지는 않음**
- **const**
  - **반드시 선언과 동시에 초기화**를 해야 함

### 스코프

- **var**
  - **함수 레벨 스코프**로, 둘러싸고 있는 중괄호가 함수일 때만 스코프로 간주
- **let과 const**
  - **블록 레벨 스코프**로, \*\*\*\*함수뿐만 아니라 조건문이나 반복문의 중괄호도 스코프로 간주
  - var보다 제약이 많아서 의도치 않게 변수가 바뀔 부작용이 적음

### 재할당 여부

- **var와 let**
  - 선언 이후에도 **재할당 가능**
- **const**
  - constant, 즉 상수라는 의미로 **한번 할당한 후에는** **기본적으로 재할당이 불가능**

### 권장되는 방법

- **최대한 const**를 쓰되 **재할당이 필요한 경우에만 let**을 사용하고 **var는 최대한 지양**

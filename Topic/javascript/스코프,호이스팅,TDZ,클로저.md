작성자: 이숙영

# 스코프 / 호이스팅 / 클로저

## 💎 스코프(scope)
### 특징
식별자(ex. 변수명, 함수명, 클래스명 등)의 유효범위를 의미, 선언된 위치에 따라 유효 범위가 달라진다. 
 
⁉️  전역 변수는 어디에서든지 참조가 가능한 값. <br/>
⁉️  지역 변수는 함수 몸체 내부를 말한다. <br/>
=> 지역 변수는 자신의 지역 스코프와 그 하위 지역 스코프에서 유효하다.

*지역 스코프는 코드의 특정 부분에서만 사용

지역 스코프의 두가지 종류<br/>
🚨 함수 레벨 스코프 <br/>
var 키워드로 선언된 변수는 오로지 함수의 코드 블록만을 지역 스코프로 인정하는 것.<br/>
🚨 블록 레벨 스코프 <br/>
let, const 키워드로 선언한 변수는 모두 코드 블록(ex. 함수, if, for, while, try/catch 문 등)을 
지역 스코프로 인정하는 블록 레벨 스코프를 따른다.<br/>
### var

<img src = 'https://user-images.githubusercontent.com/80618616/139201334-2bcf8a7d-2c9e-43a1-99bd-ceabf93d6cce.png' width='70%' height='70%'/>

### let/const

<img src = 'https://user-images.githubusercontent.com/80618616/139201435-2e404d92-7db5-471a-954c-346fd448b1d3.png' width='70%' height='70%'/>

## 💎 호이스팅(hoisting)
### 특징
함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효범위의 최상단에 선언하는것을 뜻한다.
### 호이스팅의 대상 
var, let, const, function, class 등등의 선언 키워드들은 모두 호이스팅이 되지만,
**var 변수 선언과 함수 선언문** 에서 할당을 끌어올려 사용 시 에러가 나지 않기때문에 실질적인 호이스팅의 대상이 된다.

### 함수 호이스팅
선언 단계와 초기화 단계가 동시에 진행, 런타임 이전에는 실행될 수 없음.<br/>
#### 함수 선언문
런타임 이전에 자바스크립트 엔진에서 먼저 실행되어, 함수 자체를 호이스팅 시킴.<br/>
#### 함수 표현식
런타임 이전에 해당 값을 undefined로 초기화만 시키고, (= var 변수선언방식)
런타임에서 해당 함수 표현식이 할당되어 그때 객체가 된다.

<img src = 'https://user-images.githubusercontent.com/80618616/139202585-c0eb19eb-37ac-478b-bba5-b3ac8df7a6fa.png' width='50%' height='50%'/>
<img src = 'https://user-images.githubusercontent.com/80618616/139202620-2aeb58cd-eb1c-4569-b226-4ff2203231ad.png' width='70%' height='70%'/>
<img src = 'https://user-images.githubusercontent.com/80618616/139202694-042f1e03-290a-47a6-a527-1a1e8a60712d.png' width='70%' height='70%'/>

### let
선언 단계와 초기화 단계가 분리되어 진행
런타임 이전에 자바스크립트 엔진에 의해 선언 단계가 먼저 실행되지만, 초기화 단계가 실행되지 않았을 때 해당 변수에 접근하려고 하면 참조 에러 발생.
<img src = 'https://user-images.githubusercontent.com/80618616/139202057-f71d7656-8811-4200-93eb-d79c98200a82.png'
     width='70%' height='70%'/>

### const
선언 단계와 초기화 단계가 동시에 진행, 런타임 이전에는 실행될 수 없음.

스코프의 시작 지점부터 초기화 단계 시작 지점까지 변수를 참조할 수 없는 
**일시적 사각지대(Temporal Dead Zone: TDZ)** 구간에 존재

## 💎 TDZ (Temporal Dead Zone)
변수가 선언되고 해당 변수에 값이 할당되기 전 까지의 구간 <br/>
let/const 의 경우 만약 초기값이 없다면 (const 는 에러발생)
var 처럼 자동으로 초기값 할당하지 않음
값이 할당되기 전까지 메모리를 할당하지 않기 때문에 선언(값 할당 전)에 사용하려고 하면 메모리에 해당 변수가 존재하지 않아 에러발생.
<img src = 'https://user-images.githubusercontent.com/80618616/139203041-5099d7a2-60a8-4bb5-8ba9-fbde36bec99f.png'
     width='70%' height='70%'/>
     
## 💎 클로저 (Closure)
<img src = 'https://user-images.githubusercontent.com/80618616/139203208-2c1eb1d0-9cfe-49cb-a03f-3c615e31eb81.png'
     width='70%' height='70%'/>
### 렉시컬 환경 (lexical)
자신이 선언 되었을때의 환경을 기억하여 
스코프 밖에서 호출되어도 그 환경에 접근할 수 있는 함수를 의미.

즉, 클로저는 함수를 지칭하며, 그 함수가 선언된 환경과의 관계라는 개념이 합쳐진것.<br/>
자바스크립트에서 클로저는 함수가 생성될 때마다 생성된다.

### 클로저의 형태
클로저가 아닌 함수일때 예시 <br/>
<img src = 'https://user-images.githubusercontent.com/80618616/139203368-4b6b63c8-d6ac-49e6-8b9b-82d6aef15c85.png'
     width='70%' height='70%'/>
변수 name 은 func 함수의 실행 컨택스트가 종료되서 아무런 값이 나오지 않음.<br/>
클로저 함수사용
<img src = 
     'https://user-images.githubusercontent.com/80618616/139203546-ea2b459f-82c8-4b7c-b2d1-1558b6bc0fb9.png'
     width='70%' height='70%'/>
innerFunc 로 실행 lexical 환경이 적용되어 만든뒤를 참조하지 않아도 선언할 때 이미 같이 묶임<br/>
=> 변수 name 사용 가능

### 클로저 특징
#### 💥 전역변수를 줄일 수 있다.
전역변수가 많으면 어디에서든 실수로 접근을 할 수 있기 때문에 
최대한 전역변수를 줄인 코드작성이 좋음.<br/>
=> 전역변수 사용 시 클로저가 유용하게 쓰임
<img src = 
     'https://user-images.githubusercontent.com/80618616/139203638-796a9032-c7d8-40fc-a352-9ca1c8c27b75.png'
     width='70%' height='70%'/>
<img src = 
     'https://user-images.githubusercontent.com/80618616/139203685-0f3506cf-d9a7-4fb1-b16c-aa28d0695710.png'
     width='70%' height='70%'/>

외부함수인 handleClick의 lexical environment를 참조하는 함수를 btn의 콜백함수로 이용해 전역객체 없이 구현

#### 💥 비슷한 형태의 코드를 재사용률을 높일 수 있다.
bold,itealic 등등의 새로운 태그를 만들 수 있는 함수 newTag를 클로져를 이용해 간단하게 구현가능.
인자에 open,close,content를 한번에 다 받는다면,
This is my content! 와 같은 값을 출력을 하고 싶을 때 가독성이 떨어질 수 있음.<br/>
=> 클로저를 이용하여 가독성, 재사용면에서 좋은 코드 구현가능
<img src = 
     'https://user-images.githubusercontent.com/80618616/139203913-9c84e396-cbf8-4edc-8fdf-bda95aa6fc7d.png'
     width='70%' height='70%'/>


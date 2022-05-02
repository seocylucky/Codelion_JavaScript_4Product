# javascript 사용하는 방법
1. html 파일 내부에서 사용 가능
2. js 파일 별도 사용 가능

html 파일 내부에 작성할 때 js 코드는 body 태그가 끝나는 지점에 보통 작성함

```ts
<body>
.
.
<script>
js 코드
</script>
</body>
```

## document.write(); - 브라우저 화면에 원하는 문구를 표시

html 내부에 작성할 때
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>JavaScript 사용 방법</title>
</head>
<body>
    <h1>JavaScript 사용 방법</h1>
    <script>
        document.write('코드라이언 짱짱')
    </script>
</body>
</html>
```

별도의 js 파일을 불러서 작성할 때 
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>JavaScript 사용 방법</title>
</head>
<body>
    <h1>JavaScript 사용 방법</h1>
    <script src = "myScript.js"></script>
</body>
</html>
```

## 세미콜론(;)과 주석

주석의 용도는 코드의 설명을 적어줄 때, 코드를 동작시키고 싶지 않을 때 사용

```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>세미콜론(;)과 주석</title>
</head>
<body>
    <h1>세미콜론(;)과 주석</h1>
    <script>
        //document.write('안녕') document.write('하이') -> 실행 안됨
        document.write('안녕'); document.write('하이');

        // '//'는 한줄 주석, /**/은 여러줄 주석
    </script>
</body>
</html>
```

# 데이터 상자 만들기

## 변수(variable)

```ts
var 변수명 = 값;

var name = "엄준식";
var age = 30;
var eyesight = 1.2;
var single = true;
```

JS ES6은 let과 const를 이용해서 변수를 선언한다.

자료형은 문자열(String), 숫자(정수 int, 실수 float), bool(true, false)로 나뉜다.

typeof는 데이터의 자료형을 나타낸다.
```ts
typeof 데이터
```

## Math.random();

0이상 ~ 1미만의 실수(float)를 랜덤으로 뽑는다.

1부터 45까지의 숫자를 뽑기 위해서는...

Math.random() * 45 + 1;
1이상 ~ 46미만의 실수(float)를 랜덤으로 뽑는다.

실수가 아닌 정수를 뽑기 위해서는...
parseInt(); -> 소수점은 버리고 정수로 변환

즉 parseInt(Math.random() * 45 + 1); -> 1이상 ~ 45이하의 정수(int)를 랜덤으로 뽑는다.

```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기 1</title>
</head>
<body>
    <h1>로또 번호 추첨기 1</h1>
    <script>
        var num = Math.random() * 45 + 1;
        var ball1 = parseInt(num);
        document.write(ball1);
    </script>
</body>
</html>
```

배열을 이용하여 번호 6개 뽑기
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        /* var lotto = [];
        lotto.push(parseInt(Math.random() * 45 + 1));
        lotto.push(parseInt(Math.random() * 45 + 1));
        lotto.push(parseInt(Math.random() * 45 + 1));
        lotto.push(parseInt(Math.random() * 45 + 1));
        lotto.push(parseInt(Math.random() * 45 + 1));
        lotto.push(parseInt(Math.random() * 45 + 1));
        document.write(lotto); */

        # .push()는 배열 안에 마지막 값을 추가하는 것

        var lotto = [];
        for (var i = 0; i < 6; i++){
            lotto.push(parseInt(Math.random() * 45 + 1));
        }
        document.write
    </script>
</body>
</html>
```

lotto 배열 안에 중복된 값이 없게 하려면?

## 조건문 이용!!
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        for (var i = 0; i < 6; i++){
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) { // .indexOf(값) -> 값이 배열 안에 있으면 위치값, 없으면 -1
                lotto.push(num);
            }
        }
        document.write(lotto);
    </script>
</body>
</html>
```

중복되어 하나의 값이  삭제된 후 5개의 값만 나오는 상황 발생
이를 방지하기 위해 while문을 이용하여 배열 안의 값이 6개가 될 때까지 값을 계속 넣는다.

```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {  // .length는 배열의 길이, 즉 배열 안에 값이 몇 개 들어있는지 확인함
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        document.write(lotto);
    </script>
</body>
</html>
```

랜덤으로 나온 6개의 숫자들을 오름차순으로 정리하려면?

## .sort()를 이용해서 배열 값을 정렬한다.
```ts
var lotto = [1,2,3,33,22,11];
        lotto.sort();
        document.write(lotto);
```

위의 예시로 정렬을 해보면 사전식으로 정렬이 된다. ex) 1,11,22,3,33

우리가 원하는 오름차순으로 정렬하기 위해서는 '익명함수'를 이용한다.
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        lotto.sort((a,b)=>a-b); // .sort((a,b) => a-b)
        document.write(lotto);
    </script>
</body>
</html>
```

HTML&CSS를 이용해서 이쁘게 꾸며보자!

HTML 파일
```ts
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>로또 번호 추첨기</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>로또 번호 추첨기</h1>
    <script>
        var lotto = [];
        while (lotto.length < 6) {
            var num = parseInt(Math.random() * 45 + 1);
            if (lotto.indexOf(num) == -1) {
                lotto.push(num);
            }
        }
        lotto.sort((a,b)=>a-b);
        document.write("<div class='ball ball1'>" + lotto[0] + "</div>");
        document.write("<div class='ball ball2'>" + lotto[1] + "</div>");
        document.write("<div class='ball ball3'>" + lotto[2] + "</div>");
        document.write("<div class='ball ball4'>" + lotto[3] + "</div>");
        document.write("<div class='ball ball5'>" + lotto[4] + "</div>");
        document.write("<div class='ball ball6'>" + lotto[5] + "</div>");
    </script>
</body>
</html>
```

CSS 파일
```ts
.ball {
    float: left;
    width: 60px;
    height: 60px;
    line-height: 60px;
    font-size: 28px;
    border-radius: 100%;
    text-align: center;
    vertical-align: middle;
    color: #fff;
    font-weight: 500;
    text-shadow: 0px 0px 3px rgba(73, 57, 0, .8);
    margin-right: 6px;
}

.ball1 {
    background: #fbc400;
}
.ball2 {
    background: #69c8f2;
}
.ball3 {
    background: #ff7272;
}
.ball4 {
    background: #aaa;
}
.ball5 {
    background: #b0d840;
}
.ball6 {
    background: #c7c7c7;
}
```


## "DOM"이란?
Document Object Model의 약자로 document 즉 웹 화면을 구성하는 html 코드를 쉽게 접근할 수 있도록 만든 문서 객체 모델이다.

document.getElementById()
특정 id를 가진 태그를 선택하여 불러온다. 뒤에 .value나 .innerHTML을 붙여서 태그 안에 있는 값을 가져올 수 있다.

console.log()는 브라우저가 아닌 콘솔창에 출력한다.

```ts
<body class="container">
    <h1>자기소개</h1>
    <textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
    <script>
        var content = document.getElementById('jasoseol').value;
        console.log(content); //출력값 -> 저는 인성에 문제가 없습니다.
    </script>
</body>
```

자소서 글자수 계산기를 만들 때 필요한 기능인 글자수 세기를 하기 위해선 문자열을 세는 .length가 필요하다.
이는 앞서 배운 배열값의 개수를 세주는 기능 뿐만 아니라 공백을 포함해서 문자열의 길이를 셀 수 있다.

```ts
<body class="container">
    <h1>자기소개</h1>
    <textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
    <script>
        var content = document.getElementById('jasoseol').value;
        console.log(content.length); //출력값 -> 15
    </script>
</body>
```

현재 몇글자인지 최대 몇글자인지 원하는 위치에 작성하고 싶다. 어떻게 해야할까?

앞서 배운 것들을 이용해서 만들어보자.
```ts
<body class="container">
    <h1>자기소개</h1>
    <textarea class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
    <span id="count">(0/200)</span>
    <script>
        var content = document.getElementById('jasoseol').value;
        document.getElementById('count').innerHTML = '(' + content.length + '/200)';
    </script>
</body>
```

그렇다면 위 코드처럼 글자를 입력할 때마다 저 코드를 매번 써줘야할까? 그렇지 않다. 명령어들의 모임인 함수를 이용해서 이후에 효율적으로 작성할 수 있도록 해보자.

# 함수
function 함수이름() {
    명령어1
    명령어2
    .
    .
}

```ts
<script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
```

글자를 쓸 때마다 자동으로 글자수를 세려면 어떻게 해야 할까?

'이벤트'라는 개념을 이용하자.

### 이벤트는 마우스 클릭, 키보드 누름, 값 변화, 페이지 로딩 같은 사건들이 이에 해당된다.

이벤트 핸들링이란 이벤트가 발생하면 ~해라라는 개념을 가진다.

예를 들어, "키보드를 누를 때마다 글자 수를 세주어라"에서 키보드를 누르는 것은 이벤트, 글자 수를 세주라는 것이 이벤트 핸들링이 된다.

다음 형식으로 써주면 된다.
```ts
<textarea 이벤트 = 이벤트핸들링></textarea>
```

```ts
<body class="container">
    <h1>자기소개</h1>
    <textarea onkeydown='counter();' class="form-control" rows="3" id="jasoseol">저는 인성 문제가 없습니다.</textarea>
    <span id="count">(0/200)</span>
    <script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
</body>
```

글자수가 최대 200자까지일 때, 200자가 넘으면 더이상 안써지도록 하려면 어떻게 할까?

### .substring()을 이용해서 몇글자까지 자른다는 코드를 짜주면 된다. 문자열은 각 한글자마다 인덱스번호를 갖고 있다. 예시로 content.substring(0,5)일 때, 인덱스 0이상 5미만까지만 나타나고 나머지는 잘린다는 뜻이다.


200글자까지만 보여주게 하고 싶을 때는?
```ts
<body class="container">
    <h1>자기소개</h1>
    <textarea class="form-control" rows="3" id="jasoseol" onkeydown="counter();">저는 인성 문제가 없습니다.</textarea>
    <span id="count">(0/200)</span>
    <script>
        function counter() {
            var content = document.getElementById('jasoseol').value;
            if (content.length > 200) {
                content = content.substring(0,200);
                document.getElementById('jasoseol').value = content;
            }
            document.getElementById('count').innerHTML = '(' + content.length + '/200)';
        }
        counter();
    </script>
</body>
```

# jQuery란?
효율적이고 직관적이게 엘리먼트를 선택하고 제어할 수 있도록 해주는 자바스크립트 라이브러리이다.

jQuery의 장점
1. 간결한 문법
2. 편리한 API
3. 크로스 브라우징

가장 기본적인 형태 문법은
```ts
$(선택자).행위();
```

예시
```ts
<body>
    <h1>jQuery 기초</h1>
    <textarea id="content">jQuery를 배워보자</textarea>
    <script
    src="https://code.jquery.com/jquery-3.5.1.js"
    integrity="sha256-QWo7LDvxbWT2tbbQ97B53yJnYU3WhH/C8ycbRAkjPDc="
    crossorigin="anonymous"></script> //code.jQuery.com에서 복사한 코드
    <script>
        console.log($('#content').val());
    </script>
</body>
```

jQuery Event는 어떻게 쓸까?

## jQuery 문법으로 변경 전
```ts
<body>
    <h1>jQuery 이벤트</h1>
    <button id="click" onclick="hello();">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        function hello() {
            console.log('hello');
        }
    </script>
</body>
```

## jQuery 문법으로 변경 후
```ts
<body>
    <h1>jQuery 이벤트</h1>
    <button id="click">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        function hello() {
            console.log('hello');
        }
        $('#click').click(hello); //jQuery의 click 함수 이용
    </script>
</body>
```

# 익명함수란?

말 그대로 이름이 없는 함수, 더 효율적인 코드 작성을 위해 정의하는 과정 없이 바로 함수를 작성과 동시에 호출한다.

```ts
<body>
    <h1>익명 함수</h1>
    <button id="click">클릭</button>
    <script
  src="https://code.jquery.com/jquery-3.5.1.min.js"
  integrity="sha256-9/aliU8dGd2tb6OSsuzixeV4y/faTqgFtohetphbbj0="
  crossorigin="anonymous"></script>
    <script>
        $('#click').click(function(){
            console.log('hello');
        });
    </script>
</body>
```
# 코어측 자바스크립트

## 2장 어휘구조.

> 대소문자 구문 while,While, whilE 모두다 다른 변수이다.
> HTML은 대소문자를 구별하지 않지만 XHTML을 구분한다.
> 유니코드든 뭐든 따로 읽어보고 `\` 이스케이프만 알아두자.
> 정규식,특수문자쓸때 필요하다.


> 지금 쓰는 `>` 한줄 주석

> HTML 태그 안에서는 `<!-- -->`을 사용한다.

>리터럴은 프로그램에 직접 나타나는 데이터값이다.
>쉽게 말하자면 var a = 1; 은 a는 1을 담은 변수값이고 1이 리터럴값이다.
>`{x:1,y:2}` 프로퍼티 x의 리터럴값은 1이다.

>`[1,2,3,4,5]` 배열의 length의 리터럴값은 5이다. 배열의 index[0]의 리터럴값은 1이다.


>식별자의 시작은 알파벳,밑줄(_),혹은 달러($)표시여야한다.
>식별자의 첫글자로 숫자를 쓰지않은건 자주 써보니 숫자를 맨처음에 쓰게해놓으면 진짜 숫자랑 식별자랑 헷갈릴만한 소지가 많을것같다.

>pc에 속한글자도 사용할수있다는데 특별한경우인것같고
>예약어는 한번 살펴보고 자주 쓰다보면 안써야될것들이나 에디터에서 색깔이
>특정언어에서 바뀌는걸 살펴보면 잘 넘어갈수있을것같다.


>### 2.5 선택적인 세미콜론 사용

>그냥 불편하든 안불편하든 뭐든지 끝나는곳에 세미콜론 넣는습관은 꼭 길러야할것같다.

>js를 압축할때 한줄로 만들어버릴때 에러가날수있는데 나는 압축안할건데 뭐 잘동작하는데 꼭 넣을필요가 있을까라고 생각하지말고 아무생각없이 습관을 들이는게 가장중요



## 3장 타입,값,변수

> 맨처음에 설명하고 있는것은 리터럴값등을 계속 활용하고자할때 그 값을 그냥 사용하는게 아니라 특정변수에 담아서 특정변수의 참조를 할수있는 동작방식에대해서 설명하고있다.

> 우리가 잘하는 var a=2; var b=a; b=2가 되는방식인데 왜 이런지 생각해보자면

> 그냥 특정값으로 넘겨버리면 이런형태가 된다. 2=2; 2=2; 2=2;

> 그래서 특별한 변수로 그 값을담아서 참조 할당하는 방식을 넘기는것이라고 보면된다. 나중에 나오겠지만 프로토타입으로 지정된 프로퍼티의 값을 바꾸면 프로토타입 객체들의 값들이 바뀌게 되는데
참조할당이 되어서 모든값이 할당된값을 바라보기 때문이다. 근데 원시값을 바꾸면 그 바꾼 프로토타입 객체값만 바뀌게 되는데 그 값은 할당된 값이 아니기 때문이다.

> 타입은 원시 타입과 객체 타입으로 나뉘는데 원시 타입은 숫자,텍스트(스트링값),불리언(true,false),그리고 특이한값인 null과 undefined가 있다.

> 객체는 이름과 값을 갖는 프로퍼티의 집합이다라고 하는데 특정객체에서 예를들어 `var a ={x:1}`은 a는 변수이자 x프로퍼티 1이란 값을 갖는 객체라고 생각하면된다.

> 즉, `a.x`는 `a`라는 객체는 `x`라는 이름의 프로퍼티를 갖고 있고 `Number값 1`을 갖고있다는 뜻이다.


> 일반적인 자바스크립트 객체는 순서가 없는값들의 집합.

> `ex) var arr = [1,2,3] 배열 arr에서 1번째값은 1 2번째값은 2`

> `var obj = {x:1,y:2,z:3} 객체 obj에서 1번째값은 알수없다.`

> 객체를 length값과 index값이 없는 배열처럼 속일수있지만 배열은 아니다.



>자바스크립트에서 중요한 함수는 특별한객체 객체는 객체인데 함수객체이다. 가장 중요한 점은 함수는 값이고, 우리가 알고있는 객체처럼 사용할 수 있다.
함수는 실행코드(우리가 흔히 부르는 객체의 메소드가 될수있고 함수 그자체가 될수있다.
이 부분은 간단하게 설명했지만 가장 중요한데 객체로 실행되는 함수와 함수 그자체로 실행하는것과는 굉장히 차이가 난다. 그래서 객체지향언어라고 불리는것도 다른점을 이해한후에야 피부로 와닿는것같다.)

>새로 생성된 함수객체를(여러가지로 초기화 시킬수있는데 이 초기화는 this라는 기본적으로 window 'use strict'에선 undefined로 나오기 때문에 초기화가 중요하다.)
함수객체를 초기화를 시키지 않으면 각 함수의 컨스트럭터가 생성되어 지지않아 함수중괄호안의 실행코드에 접근할수없다.


>new라는 생성자 함수로 객체를 초기화

>call,apply로 this값을 객체값으로 초기화

>함수의 특정 메소드값으로 호출하여 객체값으로 초기화

>함수 내부의 특정 변수에 객체값을 받아 리턴값으로 변수값을 나타낸뒤에 그값을 받아 초기화 하는 방법이 있다.


>객체지향언어라고 나오는 예제 a.sort()가 sort(a)의 객체 지향버전이라고 나오는데 객체지향이기 때문에 배열 a를 함수안에 인자로 넣어서 sort시키는것이 아닌 a란 배열의 객체를 가지고 sort를 시킨다는 점에서 객체지향언어라고 불리운다.

>자바스크립트의 타입은 크게 `원시타입(number,string,boolean,null,undefiend)`

>`객체타입(object,function,array,regxp,date)`

>여기서 객체 또 메서드를 가진 타입과 그렇지 않은 타입 수정할수있는타입과 수정할수없는 타입이있는데 이런 값들은 천천히 아래에서 살펴보면서 숙지하면 될것같다.

>### 3.1숫자

>다른 프로그래밍 언어들과는 다르게 정수값과 실수값을 구분하지않는다.아래 여러예제들은 읽으면 이해가 가는내용이고 이해가 가지않더라도 뭐 크게 상관없을것같다.

>### 3.2텍스트

>날짜와 시간을 표현하는 객체 Date() 생성자를 제공한다. 숫자처럼 원시타입이 아니라 각 미리 정해진 여러가지 메서드로 값을 받아올수있다.

>### 3.2.1 문자열 리터럴
>그냥 문자열을 사용하려면 작은 따옴표나 큰따옴표로 둘러쌓일수있는데
똑같이 문자열은 만드는건데 왜 두개를 나누었냐면 ''는 ""에 종속될수있고
""는  ''에 종속될수있다. 같은 따옴표를 쓰게되면 +연산자로 변수의 값으로 합칠수있다.


<pre>
    <code>
        var hi = 'hi';
        hi.toUpperCase()
    </code>
</pre>

>'HI'라고 해서 hi가 HI로 변한게 아니라 toUpperCase를 통해 새로운 문자열로 대문자를 반환한것이라고 생각하면된다.


>### 3.2텍스트

>그냥 참고로 알아두면 정규식의 /^HTML/ 은  첫부분이 HTML으로 시작하는것과 일치
`[1-9][0-9]` 은 이해하기 어렵게 설명해놨는데 []의 정규식 문법은 대괄호사이에 있는 문자와 매칭 1-9니깐 1부터 9까지 매칭되는 값인데 숫자가 처음에 1에서 9사이에 시작하게 매칭을 해놨으니 0이 아닌 숫자와 일치라고 설명해놨는데 `[채식주의자]` -> 배고플때 고기빼고 먹는사람 이렇게 설명한것이랑 비슷한 설명같다.


>그 다음에 이어지는 아무숫자나 따라온다는뜻은 `[0-9]*`은 정규식에서 *앞에 나오는 패턴은 생략이 가능하거나 그 패턴이 하나이상 나오면 전부다 매칭 숫자가 아무거나 나와도 다 일치하고 안나와도 일치한다.


>var text = "testing : 1,2,3" 간단한 문자열이라고 했는데 얼핏보면 :때문에 프로퍼티 정의로 오해할수있는데 그냥 따옴표안에 갖혀있는 장황한 텍스트들이다.


> `var pattern = /\d+/g`

>끝에 나오는 g는 글로벌 정의 `\d`는 `[0-9]`와 동일하고 뒤에 +는 +앞에 나오는 패턴은 무조건 하나 이상은 매칭되어야한니 숫자한개이상 나오면 모든 숫자와 일치하게 된다는 뜻이다.


>pattern.test(text)

>이제 주목해서 볼건 내가 메소드를 정의하지도 않았는데 pattern객체다음에 .으로 시작하고 괄호사이에 뭔 변수값을 넣어서 실행되는거면 내부 메서드라고 보면 된다.

>test는 정규식의 메서드중하나인데 그냥 매칭이 되는게 있으면 무조건 true를 반환하게 되는데 pattern이 아까 숫자하나 이상으로 시작되면 매칭되는거니 text에 1,2,3숫자가 3개나 있으니 당연히 true값을 반환한다.


<pre>
    <code>
        function reg(spec){
            var that = {};
            var text = spec.text;
            var pattern = spec.pattern || /\d+/g;

            that.get_pattern = function(){
                return console.log(pattern.test(text))
            }

            that.get_search = function(){
                return console.log(text.search(pattern))
            }
            that.get_match = function(){
                return console.log(text.match(pattern))
            }
            that.get_replace = function(){
                return console.log(text.replace(pattern,'#'))
            }
            that.get_split = function(){
                return console.log(text.split(/\D+/))
            }
            return that;
        }


        var yam = reg({text:'testing:1,2,3',pattern:/\d+/g});


        console.log(yam.get_pattern())
    </code>
</pre>

> `text.search(pattern)`

>처음보면 굉장히 골까는 부분인것같다. 아까는 숫자 한개 이상 매칭되는 pattern이란 변수를 테스트 하더니 이제는 문자열 testing: 1,2,3을 가지고 pattern이란 매개변수로 search란 메서드를 실행시킨다니

>정규식에는 정규식패턴을 사용하는 String객체의 메서드가 4개있다.
search,replace,match,split인데 그럼 test는 이라고 설명할텐데 regexp(정규식)객체의 메서드이다. 위에는 정규식객체에서 실행시키는 메서드 인자값은 스트링값을 받는다. test하고 exec가 있는데 test는 아까 설명했고 exec는 좀 복잡해서 나중에 정규식에서 다시 보는게 속편하고 이렇게 장황하게 설명해봤자 다 까먹는다.


> `console.log(yam.get_search())`

> 1. search값은 객체값에서 정규식패턴을 일치할때 그 일치한 위치를 반환하는 값인데 저기는 숫자한개이상이 매칭되는거니깐 9가 반환된다. 왜냐면  t,e,s,t,i,n,g,: 공백이 9이고 숫자하나와 매칭되는 기준점인 1이 9번째부터라서 그렇다.

<pre>
    <code>          <em>t<sup>1</sup>e<sup>2</sup>s<sup>3</sup>t<sup>4</sup>i<sup>5</sup>n<sup>6</sup>g<sup>7</sup>:<sup>8</sup>1<sup>9</sup></em>
    </code>
</pre>


> `console.log(yam.get_match())`

> 2. match값은 아까 testing : 1,2,3에서 Number값은 1,2,3밖에 없는데 이 값을 배열로 집어넣어 값을 반환한다. [1,2,3]


> `console.log(yam.get_replace())`

> 3. replace는 잘쓰이는 방식중하난데 여기서는 pattern = 즉숫자로 시작한것을 #으로 바꾸게 해놨는데 testing: #,#,#으로 바뀐다.


>`console.log(yam.get_split())`

> 4. text.split은 또 골까게 설명해놨는데 첫번째 인자의 값을 기준으로 매칭되는값만 나누는것인데 배열에 담는다. /\D+/는 숫자와 ASCII문자 빼고 모든값인데 그래서 저기에서 값이 공백하나 1,2,3이 출력되는것이고, 두번째 인지값은 legth지정하는것이다. 1이면 매치되는 첫번째값만 출력이 되어버린다.

<pre>
    <code>
            that.get_split = function(){
                return console.log(text.split(/\D+/), 1) 이런식으로
            }
    </code>
</pre>


>### 3.3 불리언값

>그냥 불리언값은 참/거짓을 뜻하는 true/false이다.
true는 1과 동등하고 false는 0값과 동등하다.
null과 undefined는 조건식에서 true랑 같지 않아서 else값으로 넘어가는거지  false값이랑 똑같아서 true가 아니기 때문에  else값으로 넘어가는것으로 혼란을 일으키면 안된다.


<pre>
    <code>
            if(null == 0){
                alert('null이 0이야?')
            }else if(null == false){
                alert('null이 false야?')
            }else{
                alert('null은 null이나 undefined랑 비교해야지')
            }
    </code>
</pre>


> 불리언 값은 문자열 'true' 혹인 'false'로 변환할 수 있는 toString()메서드를 가지고 있지만 그 밖의 메서드는 가지고 있지않다.

> 여기서 또 단순하지 않은 &&와 ||연산자를 진짜 쉽게 설명하고 있다. 4.10에서 자세히 설명한다는데 그냥 여기서 설명 더 자세히 먼저 보고 아래를 클릭하여 살펴보자.

[4.10 논리표현식 링크](./ch.04/README.md#410-논리-표현식)


> `if((x==0 && y == 0) || !(z==0))` { x와 y는 둘다 0이거나 z가 0이 아니다}
 이걸 자세히 풀어보자면 &&의 값은 좌변값이 false이면 오른쪽값은 평가도 하지않고 false값을 갖게 된다. 일단 x가 0이 되면 y값으로 넘어가게 되는데 이놈도 0이아니면 이 &&식은 true가 되고 아니면 또 false값을 반환하게 된다. 이 값이 또 하나의 좌변값으로 쓰이게 됐는데 || 연산은 이 좌변식이 true이면 오른쪽으로 갈 필요없이 true를 반환한다 x랑 y가 둘다 0이면 z가 0이든 1이든 10000이든 상관이 없다. 근데 좌변값에서 x가 0이 아니게 되면 바로 오른쪽식으로 평가가 들어가서 z가 0이아니면 이 식은 참조건을 만족해서 조건식이 평가되고 z가 0이면 그냥 조건식이 실행되지않는다. 앞에 !는 !뒤에나오는 식을 불리언값으로 반대값으로바꿔놓는것이라고 생각하면된다.


>### 3.4 null과 undefined


> null은 값이없음 변수에 빈문자열을 할당했을때 나타나고 typeof연산자를 쓰면 object를 반환한다.

> undefined는 null가 달리 빈값이 아니라 그냥 값이 없을때 나타나는데 변수를 초기화 시키지않았거나 존재하지 않는 객체의 프로퍼티나 배열의 원수값 반환값이 없는 함수와 인자가 없는 함수 매개변수의 값에 의해 반환하는데 조금 위험하게  생각하면 값도 없는데 불러오면 다 undefined라고 생각하면 될것같다. undefined는 typeof연산자를 사용할때 undefined가 반환되는데 그냥 undefined는 그 값 자체로 특별한 고유의 값이라고 생각하면 될것같다.

>둘의 차이에도 불구하고 값이 없는것은 같기때문에 동등연산자로는 true를 반환하게 되고 false로 판정되는 값이며 !null과 !undefined로 불리언값으로 변환하면 false를 반환한다.


>### 3.5 전역객체

>자바스크립트 인터프리터가 시작할때(웹브라우저가 새로운 페이지를 불러올때) 새로운 전역객체를 만들고 그 프로퍼티를 초기화한다.
여기서는 전역객체가 생성되고 프로그램 전역에서 사용될 몇 가지 값들이 객체에 추가되는 프로그램에서 정의한 전역 객체를 가진다고 설명이 되어있는데 그냥 console을 찍어봐서 window에 어떤것들이 정의되어있는지 살펴보면 그냥 무난하게 넘어가지 않을까 싶다.


<pre>
    <code>
        var global = this;
        console.log(global.outerHeight)
        console.log(window.outerHeight)
    </code>
</pre>


>### 3.6 레퍼 객체

>자바스크립트 객체는 복합적인 값이고, 객체 안의 값들은 프로퍼티 또는 이름이 있는 값들의 집합이며 표기법을 사용하여 객체다음 . 객체['프로퍼티']값을 참조하고 프로퍼티의 값이 함수일때, 이 프로퍼티에서 불리워지는 함수를 메서드라고 부른다.



<pre>
    <code>
        var s = "hello world!"
        var word = s.substring(s.indexOf('')+1, s.length);

        console.log(word)
    </code>
</pre>


>왜 문자열은 원시값이라고 위에서 그렇게 말했으면서 프로퍼티와 메서드를 가지고 있을까?
문자열 s의 프로퍼티나 메서드를 참조하려고 할 때, 자바스크립트는 new String(s)을 호출한 것처럼 문자열 값을 객체로 변환한다. 이 객체는 문자열 메서드를 상속 하고 프로퍼티 참조를 살펴보는데 사용한다.

[6.2.2 상속 링크](./ch.04/README.md#622-상속)


>s의 프로퍼티를 참조할때 문자열값을 객체로 변환
s.substring()을 참조하게 된다면 s는 새로운 문자열을 갖는 객체로 변환
객체의 기존 substring()메서드는 없으니 s.prototype.substring = function(){}
저런 방식으로 참조할때 값이 나오면 이 일말의 과정은 값을 내놓고 메모리에서 회수되는 방식으로 되는것같다.


<pre>
    <code>
        var beforeString = "test";
        beforeString.len = 4
        console.log(beforeString.len = 4)

        이 단계는 beforeString.len에 4가 담겼다는 것을 console창에 보여주기 위함이다.

        var afterString = beforeString.len;

        console.log(afterString)
    </code>
</pre>

>  위 코드를 실행해 보면 afterString 값은 undefined인데
> 1. 변수 beforeString에 문자열 test를 정의
> 2. beforeString에 len이라는 프로퍼티에 4를 정의 하고 임시객체를 회수한다.
> 3. afterString에 beforeString.len를 호출하는데 beforeString의 len프로퍼티를 참조하기 위해 임시객체를 실행시키지만 len의 값을 정의하지 않았기 때문에 undefined를 호출한다. 위에서 정의한값은 그냥 정의하고 바로 수거되었기때문에 지속되어있지않는다.

>문자열,숫자,불리언의 프로퍼티에 접근하려고 할 때 생성되는 임시객체는 레퍼 객체로 알려져 있는데, 보통 레퍼 객체는 Number또는 Boolean객체에서 String객체와 문자열,숫자 또는 불리언 값을 구별하는 데 필요하다.
여기서 중요한건 문자열과 숫자,불리언 값의 프로퍼티가 읽기 전용이고, 이 값들에 새로운 프로퍼티를 정의할 수 없는 사실과 이 값들이 객체와는 다르고 레퍼객체로 임시로 참조만 가능하다는 사실을 알면 될것같다.

>String()과 Number() 그리고 Boolean()생성자를 사용해 명시적으로 레퍼 객체를 생성할 수있는데 이렇게 사용하는건 좀 복잡스럽고 쓸모가 없는것같다. 아래에서 이유를 설명하자면


<pre>
  <code>
    var newS = "test";
    var newN = 1;
    var newB = true;

    var objectS = new String(newS);
    var objectN = new Number(newN);
    var objectB = new Boolean(newB);


    console.log(objectS.length);
    console.log(newS.length);
    console.log(objectS)
    console.log(newS)
  </code>
</pre>

>그냥 여기서 둘다 4가 나온다 위에서는 명시적으로 new String으로 newS를 인자값으로 받는 객체 objectS를 정의했고 newS는 그냥 test란 문자열값을 가진 변수인데 똑같은 값을가지게 된건 레퍼객체로 newS의 프로퍼티 length를 호출할때 임시로 객체가 만들어지고 참조후에 값을 받은뒤 사라졌기 때문이다.

>이런것때문에 저 new String을 일일히 만들필요가 없다.

>그냥 프로퍼티와 메서드가 뭐가 있는지 알면 자연스레 레퍼객체가 만들어져 읽기전용으로 값을 반환해주기 때문이다. 그러면 왜 쓸모없이 new생성자가 있을까라고 생각을 할수가있겠는데 저렇게 new생성자로 원시값들을 객체로 담는 과정이 없다면 레퍼객체로 똑같이 그 일련의 과정을 거치지 못함에 있어서가 아닐까라고 생각해본다.

>예를 들면 자바스크립트초등학교 1학년 4반 철수의 별명이 똥개인데 똥개는 20번이다.
이걸 공공연하게 자바스크립트초등학교 1학년 4반 철수(별명:똥개)라고 1학년 4반애들에게 알려줄필요가 없다. 그냥 1학년 4반내에선 똥개 몇번이야 라고 말하는게 더 편하다.
1학년4반 학생들은 똥개가 몇번이지 하면 모두들 똥개가 철수인지 인지하기 때문에 20번이라고 알고있을것이기 때문이다.


>### 3.7 원시 타입과 참조타입

>자바스크립트에서 원시타입과 참조타입(배열과 함수를 포함한) 근본적인 차이는 원시타입의 값은 읽기전용값이라 수정할수가없다.

>원시 타입은 값으로도 비교가 되는데 두 값이 같은 값을 가지고 있다면 두 값은 같다. 이는 숫자와 불리언 값, null, undefined에도 마찬가지로 적용이 되는데 이들을 비교할 수 있는 다른 방법은 없다. 하지만 문자열은 두 문자열의 길이가 같고 각 인덱스에 있는 문자들이 같다면 두 문자열을 같다고 판단한다.

>객체는 원시 타입과는 다른데 객체는 자신의 값을 변경할수있다.

<pre>
  <code>
    function object_type(){
        var o = {x :1 };
        console.log(o.x = 2);
        o.y = 3;
        console.log(o)
    }

    object_type();
  </code>
</pre>


> 처음에 o.x의 값은 2로 나올것이다 아래에서 값을 바꿨기 때문이다.
다음에는 o객체에서 y라는 프로퍼티를 추가하고 3의 값을 할당했다.
마지막으로 o객체를 보면 x,y의 두개의 프로퍼티가 있는것을 볼수있다.

<pre>
  <code>
    function array_type(){
        var a = [1,2,3];
        console.log(a[0] = 0)
        console.log(a[3] = 4)
        console.log(a)
    }

    array_type();
  </code>
</pre>

>객체는 값으로 비교되지 않는데 두 객체가 같은 프로퍼티와 값을 가지고 있어도 두 객체는 같지 않다. 같은 순서로 같은 원소를 갖고 있어도 같은 객체가 아니다.

>#### neqObject

<pre>
  <code>
    function neqObject(){
        var o = {x :1};
        var p = {x :1};
        var a = [];
        var b = [];
        console.log(o===p)
        console.log(a===b)

        console.log(o.x)
    }

    neqObject();
  </code>
</pre>

>객체는 참조 타입으로 불리는데, 객체는 참조로 비교된다고 할 수 있다. 두객체의 값은 그들이 같은 객체를 참조한다면 같다.



<pre>
  <code>
    function eqObject(){
       var a = [];
       var b = a;
       b[0] = 1;
       console.log(a[0]);
       console.log(a === b);
    }

    eqObject();
  </code>
</pre>

>방금의 코드를 통해 보듯이 객체를 변수에 할당하는 것은 단순히 참조를 할당하는것인데 이는 객체의 새로운 복사본을 생성하지 않는다.객체 또는 배열의 새로운 복사본을 만들려면 명시적으로 객체의 프로퍼티 또는 배열의 원소를 복사해야한다.



<pre>
  <code>
     function arrayIsarray(){
            var that = {};
            var a = [12,'a','c',55];
            var b = [];
            for(var i=0; i < a.length; i++){
                    b[i] = a[i]
                }
                that.firstA = function(){
                    return a;
                }
                that.firstB = function(){
                    return b;
                }
                return that;            
     }

     arrayIsarray();

  </code>
</pre>


>비슷하게， 두 다른 객체 또는 배 열을 서로 비교하고 싶다면 그들의 프로퍼티 또는 원소를 비교해야 한다. 다음은 두 배 열을 비교하는 함수를 정의한다.

<pre>
  <code>
    function equalArrays(a , b) {
        if (a.length != b.length) return false;  
        크기가 다른 배열은 같지 않다
        for(var i = 0; i < a.length; i++)  
        모든 원소를 순회한다
        if (a[i] !== b[i]) return false;  
        일부 원소가 서로 다르다면， 두배열은같지않다
      return true;
     }


    var arrayVS = arrayIsarray();
    console.log(equalArrays(arrayVS.firstA() , arrayVS.firstB()));

  </code>
</pre>

>### 3.8타입변환

>자바스크립트는 타입에 대해 매우 유연하다. 불리언에서 이런 점에 대해 살펴보았는데 자바스크립트가 불리언 값을 기대할 때, 여러분은 어떤 타입의 값이든 전달할 수 있고, 자바스크립트는 그 값을 필요에 따라 변환할 것이다. 어떤값('참으로 판정되는 값'')은 true로 변환하고 다른값('거짓'으로 판정되는 값들은 false)로 변환한다.


<pre>
  <code>
    function nan(){
        var n = 1 - "x";
        var m = 1 + "x";
        var c = "x" + 1;
        var v = "x" - 1;
        var str = "xs" - "x";
        var nan = n + "object"

        console.log(n)
        console.log(m)
        console.log(c)
        console.log(v)            
        console.log(str)
        console.log(typeof str)
        console.log(nan)
        console.log(typeof nan)
    }

    nan();

  </code>
</pre>


>* 위에서 확인해봤듯이 -연산은 숫자가 우선이고
>* +연산은 문자열이 우선인걸 확인할수있다.
>* 연산은 문자가 나오면 숫자도 문자열로 합친다.
>* -연산은 무조건 숫자연산으로 문자열끼리 빼도 Nan을 반환한다.
>* 그래서 nan값이 Nan값과 문자열을 합치면 "NaN objects"를 반환하는것이
>* NaN의 typeof 값이 넘버이기 때문이다.

>표3-2는 다시한번 천천히 잘 정독해보는게 좋을것같다.
>여기에서의 핵심은 타입변환이 자유롭고 변환후에 무엇으로 반환되는지 잘 알아보는게 중요하다. 그래서 위에서 원시타입에서 객체로의 변환을 설명하는 레퍼객체의 예제에서도 살펴볼수있다. 하지만 객체가 올자리에 null과 undefined를 사용하면 변환을 수행하는 대신 TypeE1Tor 예 외가 발생한다. 그리고 객체에서 원시 타입으로의 변환은 다소 복잡하다.

>### 3.8.1 변환과 동등비교

>자바스크립트는 값의 타입을 유연하게 변환 시킬수있고 == 연산자를 사용해 값이 동등한지에 대한 판단도 손쉽게 할 수 있다.

>4.9.1절에는 두값이 동등한지 판단하기 위해 == 연산자가 수행하는 타입 변환 과정을 설명한다.

>위에서 false와 undefined가 같지 않다고 설명했듯이 불리언값이 올자리에 사용되면 false로 변환하지만 그자체가 false값은 아니다. ==연산자는 피연산자를 불리언으로 변환하지않기때문이다. 그래서 !연산자가 있는것이다!



<pre>
  <code>
    function ifwhy(){        
       if(!!undefined == false) console.log('hi')
    }

    ifwhy()

  </code>
</pre>

>### 3.8.2 명시적변환

>자바스크립트가 많은 타입의 전환을 자동으로 수행하더라도, 때때로 명시적 변환이 필요할지 모른다. 그리고 코드를 깔끔하게 유지하기 위해 변환을 명시적으로 하는것을 더 선호할 수도 있다.

<pre>
  <code>
      function objectNew(){
          var num3 = Number('3');
          var stringF = String(false);
          var obj = Object();


          console.log(num3)
          console.log(stringF)
          console.log(obj.toString())
      }

      objectNew();
  </code>
</pre>


>null과 undefined를 제외한 모든 값은 toString()메서드를 가지고 있으며 Object()함수는 이런 경우에 예외를 발생시키지 않고 새로 생성된 빈객체를 반환한다. .

>* 특정 자바스크립트 연산자는 암시적 타입변환을 수행하는데
>* 위에서 말했듯이 +는 문자열이있음 문자열중심
>* -는 문자도 숫자로 바꾸고 -x같다. 저 아래 예시는
>* !!x는 위에서 설명했듯이 !값은 자신의 값은 반대로 Boolean값으로 바꾼다.

>Number클래스 toString()메서드는 인자값으로 진수로 변환하는값을 가진다.

>아래 나오는것들은 흥미가 있으면 따로 읽어보는것이 좋겠다. parseInt()나 parseFloat()자주 쓰이니 정독정도는 아니더래도 읽어보자

>### 3.8.3 객체에서 원시 타입으로 변환

>객체에서 불리언으로 의 변환은 간단하다. 모든 객체(배열과 함수를 포함한는)true로 변환된다. 이는 레퍼 객체도 동일하게 적용된다.

>헷갈리게 적어놓은게 있는데 new Boolean(false)는 원시 타입이 아니라 객체이므로 true로 변환된다란 말은

<pre>
  <code>
      function whatOb(){
          var x = new Boolean(false);            
          if(x == true){console.log('x의 값이 트루값이란 이야기가 아니야')}
          else if(x){console.log('x가 참값으로 판단한다는 이야기지')}
      }

      whatOb();
  </code>
</pre>

>위에서 계속 설명한  개념이 안잡히면 뭔소리인지 모를것이다. 말그대로 new Boolean(false)는 false값을 가지고 있는 생성자 함수인데 이 오브젝트는 원시값 그냥 false를 반환하는 1차원적인 값이 아니라 false를 담고있는 새로운 객체인데 이 객체값이 있는지 없는지를 판단하는것값이 true란 이야기로 해석을 하면 될것같다.

>객체에서 문자열로 그리고 객체에서 숫자로의 변환은 변환될 객체의 메서드를 호출함으로써 수행된다. 프로퍼티도 호출하면 된다. [neqObject 참고](./ch.02-3/README.md#neqObject) 앞 링크를 참고하자

>이는 자바스크립트 객체가 변환을 수행하는 두개의 서로다른 메서드를 가지고 있기 때문에 변환 과정이 다소 복잡하다. 그리고 다음과 같은 특별한 경우에도 변환 과정이 다소 복잡하다. 이번 절에서 설명한 문자열과 숫자로의 전환 규칙은 오직 네이티브 객체에만 적용가능하고 호스트 객체들은 그 자체 알고리즘에 따라 숫자와 문자열도 가능하다.

<pre>
  <code>
      function nativeObj(){
          var that = {};
          that.native1 = function(){
              for(obj in window){
                  console.log(obj)
              }
          }    
          that.native2 = function(){
              for(obj in window.document){
                  console.log(obj)
              }
          }
          return that;
      }        


      var nativeObjs = nativeObj();

      console.log(nativeObjs.native1())
      console.log(nativeObjs.native2())
  </code>
</pre>


>코드를 실행해 보면， 호스트 객체만 보이고 네이티브 자바스크립트 객체는 보이지 않는 것을 알 수 있다. 브라우저에서 이런 식으로 호스트 객체와 네이티브 객체를 구분하는 것을보기란 어렵지 않다. 웹 브라우저와 관련 있는 가장 유명한 호스트 객체는 HTML 문서와 동작하는 인터페이스로서 보통은 DOM으로 많이 알려져 있는 것이다.


>모든 객체는 두개의 타입 변환 메서드를 상속하는데 첫 번째 메서드는 toString()인데 이 메서드는 객체가 나타내는 정보를 문자열로 반환한다. 내장된 toString()메서드는 그리 유용한 정보를 제공하지 않는다.(하지만 6-4에서 그 유용함에 대해 살펴본다 한다.)


<pre>
  <code>
      6.4에서 나오는 classof함수

      var objectN = new Number(newN);

      function arrayIsarray(){
          var that = {};
          var a = [12,'a','c',55];
          var b = [];
          for(var i=0; i < a.length; i++){
              b[i] = a[i]
          }
          that.firstA = function(){
              return a;
          }
          that.firstB = function(){
              return b;
          }
          return that;
      }

      var arrayVS = arrayIsarray();

      function nativeObj(){
          var that = {};
          that.native1 = function(){
              for(obj in window){
                  console.log(obj)
              }
          }    
          that.native2 = function(){
              for(obj in window.document){
                  console.log(obj)
              }
          }
          return that;
      }        


      var nativeObjs = nativeObj();

      function classof(o) {
          if (0 === null) return "Null";
          if (0 === undefined) return "Undefined";
          return Object.prototype.toString.call(o).slice(8,-1);

          네이티브 객체 object의 프로토타입의 toString메서드를 call함수로 자신의 값으로 this를 받아서 8번째로 시작하는 [object <-앞에 붙은 8자리 빼고 마지막 ]이부분을 삭제해서 객체의 현재값을 알아 볼수있다.           
       }


        console.log(classof(nativeObjs));
        빈객체에 that값을 반환하는 함수에 할당하는 값이기 때문에 객체임 반환하는값없음 undefined나올거임

        console.log(classof(objectN));
        Number 위에서 찾아보면 new Number로 정의된값

        console.log(classof(nativeObj));
        - function         
        console.log(classof(arrayVS.firstA()));
        - array
  </code>
</pre>

>다른 객체 변환 함수는 valueOf()라고 불리우는데 이 메서드는 자세히 정의 되어있지않다. 만약 객체를 표현하는 원시 타입이 있다면 valueOf()는 객체를 원시 타입으로 변환하려고 할 것이다. 객체는 결합된 값이고 대부분의 객체는 하나의 원시 타입으로 표현할 수 없기 때문에, 기본적으로 valueOf() 메서드는 원시 타입을 반환하지 않고 단순히 객체 그 자신을 반환한다.

<pre>
  <code>
      function valueOfs(){
          var that = {};
          var o = {x : 1, y:"안녕하시오",dd:undefined}

          that.valtoStr = function(){
              console.log(o.valueOf()+1);
              console.log(o.x+1);
              console.log(o.y+1);
              if(o.x.valueOf() > 0){console.log('하이')}
              console.log(o.dd.valueOf());

          }
          that.toStr = function(){
              return true;
          }
          that.values = function(){
              return false;
          }
          that.nums = function(){
              return 1;
          }
          that.obw = function(){
              var nums = new Number(3);
              var strings = new String('겔겔겔');
              var now = new Date();

              console.log(typeof(nums+1))
              console.log(typeof(nums-1))
              console.log(nums == nums.toString())
              console.log(nums > (nums-1));



              console.log(typeof(strings+1))
              console.log(typeof(strings-1))
              console.log(strings == strings.toString())
              console.log(strings > (strings-1));


              console.log(typeof(now+1))
              console.log(typeof(now-1))
              console.log(now == now.toString())
              console.log(now > (now-1));
          }

          return that


      }

      var obto = valueOfs();

      obto.valtoStr()
      console.log(obto.toStr().toString())
      console.log(typeof obto.toStr().toString())
      console.log(obto.values().valueOf())
      console.log(typeof obto.values().valueOf())

      obto.obw()
  </code>
</pre>


>지금껏 설명한 valueOf는 설명을 안하다 시피했으면서 설명을 했다니 위에 살짝 봤을때 객체에서 문자열로 바뀌는거랑 숫자열로 바뀌는거랑 약간 다른 형태로 보이는데 위에 콘솔까보면서 책이랑 읽으면서 이해하면 될것같다.


>자바스크립트에서 +연산자는 숫자 덧셈과 문자열 붙이기를 수행하는데 + 연산자의 피연산자가 객체라면 객체에서 숫자로 변환하는대신 객체에서 원시 타입으로 변환한다. obto.valtoStr()참고

>Date객체는 숫자와 문자열 상호변환 가능하며 객체에서 문자열로의 변환은 Date객체에 한해 toString()메서드를 먼저 사용한다.

>값이 변환될때 Date같은객체 빼고는 valueOf()를 먼저 사용한 후 toString()을 사용한다. 그 값은 숫자나 문자열로 추가 변환없이 바로 사용한다. 먼소리냐면 그냥 객체가 1의 값을 받았다고 해도 number로 변환하지않고 그냥 object1로 연산을 실행한다는 소리같다.

>근데 +나 == !-이런 연산자들은 값의 비교를 위해 문자열에서 원시타입으로의 전환을 수행하고 아래 함수는 number와 string과 date의 상호작용을 보여준다.

>### 3.9 변수선언

>자바스크립트에서 변수를 사용하기 전에 변수 선언을 해야한다. 변수는 다음과 같이 var키워드를 이용하여 선언한다.
다 알고 있지만 var구문에서 변수에 초기값을 지정하지 않으면 변수는 값이 설정될 때 까지 undefined값을 갖게된다. var는 for와 for in문 안에 올수있다. 자바스크립트 변수선언은 타입을 명시하지않아 원시값 함수 객체든 다 담을수있다.

>### 3.10 변수의 유효범위

>변수의 유효범위는 변수가 정의되어 있는 영역을 말한다. 지금 이글을 쓰면서도 전역변수를 가급적 정의안하려고 했는데 몇개 정의해놨는데 지금 까마득히 아래에 있는 이 상태에서도 불러올수있다.
함수의 매개변수도 지역변수 함수안에서 선언된 변수는 함수내부에서만 유효한 변수이다.
지금 선언한것들은 위에 예제를 통해 자연스럽게 설명이 된것같다.

<pre>
  <code>
      function hois(o){
          var i = 0;
          //console.log(j);          
          if(typeof o == "object"){ //객체o를 동등연산자로 오른쪽 string과 비교하여 원시값으로 바뀌었다.
              var j = 'j입니다.';
              for(var k=0; k <10; k++){
                  console.log(k)
              }
              console.log(k);
          }            
          console.log(j);
      }

      console.log(hois(new Object()))
  </code>
</pre>


>예제가 열라 헷갈리게 써놨는데 저게 i는 hois함수몸체 최상단 그다음에 j는 if몸체안 var k는 for문에서 초기화되는값인데 이값은 전체다  함수내부스페이스에서 최상단에 정의된다.

>### 3.10.2 프로퍼티로서의 변수

>여러분이 전역 자바스크립트 변수를 선언할때 실제로는 전역 객체의 프로퍼티를 정의하는것이다. 라고 참 어렵게 써놨다.
자바스크립트는 this키워드로 전역객체를 참조 할수 있도록 한다 하지만 지역 변수가 저장된 객체를 참조할 다른 방법은 꼼수를 써야하겠다. 뭐 나중에 나올것이다.


>### 3.10.3 유효범위체인
자바스크립트는 언어적으로 유효범위를 가지고 있는 언어이고 변수의 유효범위란 변수가 정의된 block범위라고 생각할수있다. 전역변수는 프로그램 전체에 걸쳐 정의되고 지역변수는 변수가 선언된 함수내에서 전체에 걸쳐 정의되는데


<pre>
  <code>
          ------------------윈도우 전역객체 네임스페이스-------------------------

              var s = 1; --네임스페이스안에서 유효

                          --------
                              function ss(){
                                  var k = 0; -----여기서만 유효

                                  여기서도 s가 유효




                               }
                          ----------------


                           --------
                              function ss2(){
                                  var k = 0; -----여기서만 유효
                                  var s = 0; -----s는 이 네임스페이스에서 ss2의 s는 0으로 초기화


                               }
                          ----------------

          여기서도 s


          ------------------윈도우 전역객체 네임스페이스-------------------------
  </code>
</pre>


<pre>
  <code>
      var abcdefg = 3;

      function xxxx(){

          var k = 2;

          return console.log(k+abcdefg);
      }

       function xxxx2(){

          var k = 3;
          var abcdefg = 5;

          return console.log(k+abcdefg);
      }

      xxxx();
      xxxx2();
  </code>
</pre>

>+ 내가 이 일련의 과정을 이해한과정은
>+ window.abcdefg = 3;
>+ window.xxxx().k = 2;
>+ 둘은 +연산으로 5의 값을 반환

>+ 아래에서는
>+ (window.xxxx2().k) = 3;

>+ window.xxxx2()함수안에서 abcdefg를 정의
>+ abcdefg프로퍼티는 xxxx2의 프로퍼티 호출로 인해
>+ window.abcdefg = 3;
>+ (window.xxxx2()).abcdefg= 5;  
>+ 이런식으로 값이 반환되는것같다.

>+ 전역스페이스에서 지정한 var abcdefg = 3;

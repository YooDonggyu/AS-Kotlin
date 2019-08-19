# About Kotlin

>IntelliJ IDEA 라는 제품으로 유명한 JetBrains 사 에서 만든 언어 <br>
>2011년 최초 공개, 2016년 정식 버전 출시, 2017년 구글I/O 2017에서 안드로이드 공식 지원 언어로 채택.

Grammer
---
1. 문장 끝에 세미콜론을 넣지 않음.
2. new 키워드 없이 객체 생성.
3. 타입 추론을 지원 -> 일반적인 경우 타입을 명시하지 않아도 됨.
    - ex) val name : String = "YongJun" 의 경우 타입 추론이 가능하므로 val name = "YongJun" 가능
4. val : value (상수) / var : varable (변수)
5. 인터페이스의 인스턴스를 람다식으로 표현할 수 있다.

| java | kotlin |
| --- | --- |
| View.setOnClickListener(new View.OnClickListener(){<br>@override<br>public void onClick(View view){<br>Toast.makeText(view.getContext(), "Click", Toast.LENGTH_SHORT).show();<br>}<br>}); | view.setOnClickListener{<br>Toast.makeText(it.context, "Click", Toast.LENGTH_SHORT).show()<br>} |

6. 값 및 변수 선언
```
kotlin
--------------------------
// String 타입의 상수
val a: String = "foo"

// String 타입 추론가능 -> 타입 명시하지 않음
val b = "bar"

// 선언 시 값을 할당하지 않으면 타입을 반드시 명시해야 함 -> 상수인데 초기화 안해도 됨?? 
val c: String
c = "baz"

var d: Int = 0
d += 1
```
7. Unit은 자바의 void와 유사하게 사용하며 Unit을 반환하는 함수는 반환형을 생략할 수 있음. 
```
// 반환형 명시
fun greet(name: String): Unit{
   println("Hello, $name!")
}

// 반환형 명시 X
fun greet(name: String){
   println("Hello, $name!")
}
```
8. when 문은 자바의 switch와 동일한 역할을 한다.
```
fun countItems(count: Int){
   when(count){
      1 -> println("There is $count item.")
      else -> println("there are $count items.")
   }
}
```

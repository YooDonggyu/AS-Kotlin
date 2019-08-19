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
9. for문과 for-each문 모두 지원하는 java와 달리, kotlin은 for-each문만 지원한다.
```
// for-each
val items = listOf("foo","bar","baz")
for (item in items){
   println("item: $items")
}

// while문은 java와 동일하다
var i = 0
while(i < items.size){
   println("item : ${items[i]}")
   i++
}
```
10. kotlin은 primitive type과 wrapper type을 구분하지 않는다.
* kotlin은 모든 타입을 객체로 표현하므로 primitive type과 wrapper type을 하나의 객체 타입으로 저장한다.

| java primitive | java wrapper | kotlin |
| --- | --- | --- |
| byte | java.lang.Byte | kotlin.Byte |
| short | java.lang.Short | kotlin.Short |
| int | java.lang.Integer | kotlin.Int |
| long | java.lang.Long | kotlin.Long |
| char | java.lang.Character | kotlin.Char |
| float | java.lang.Float | kotlin.Float |
| double | java.lang.Double | kotlin.Double |
| boolean | java.lang.Boolean | kotlin.Boolean |

11. 비트연산자 비교
* ex) val foo: Int = (2 or 4) shl 1
    
| java | kotlin | 의미 |
| --- | --- | --- |
| & | and | 비트 연산 AND |
| ㅣ | or | 비트 연산 OR |
| ^ | xor | 비트 연산 XOR |
| ~ | inv | 비트 연산 NOT |
| << | shl | 왼쪽으로 쉬프트 |
| >> | shr | 오른쪽으로 쉬프트 |
| >>> | ushr | 오른쪽으로 쉬프트 (부호 비트 무시) |

12. kotlin 에서는 문자형 자료형에 문자만 대입할 수 있으며 숫자를 대입할 경우 컴파일 에러가 발생한다.
* char c = 65; // 자바에서는 아스키 코드 값을 char 자료형에 넣을 수 있다.
```
// 문자 'A'의 아스키 코드 값
val code: Int = 65

// code에 해당하는 문자를 할당
// Int 자료형은 kotlin.Number 클래스를 상속 -> toChar() 메소드는 Number 클래스에서 제공하는 메소드
val ch: Char = code.toChar()
```
13. 문자열 속 특정 문자 접근

| java | kotlin |
| --- | --- |
| String foo = "Lorem ipsum"; <br><br>// ch에 인덱스가 4인 문자 'm'할당<br>char ch = foo.charAt(4); | val foo: String = "Lorem ipsum" <br><br>//ch1에 인덱스가 4인 문자 'm' 할당<br>val ch1: Char = foo.get(4)<br><br>//ch2에 인덱스가 6인 문자 'i' 할당<br>val ch2: Char = foo[6] |

14. 문자열 템플릿 기능
```
val length: Int = 3000

// 기존 규격화된 문자열 생성 방법
val lengthText: String = String.format("Length : %d meters", length)

// 문자열 템플릿 기능 사용
val lengthText2: String = "Length : $length meters"

--------------------------------------------------------------------

// 표현식 사용 방법
val text: String = "Lorem ipsum"
val lengthText: String = "TextLength : ${text.length}"

// 통화 기호 사용
val price: Int = 1000
val priceText: String = "Price : ${'$'}$price"
```

15. 배열 타입이 별도로 존재하는 java와 달리, kotlin에서의 배열은 타입 인자를 갖는 Array 클래스로 표현한다.

| java | kotlin |
| --- | --- |
| String[] words = new String[] { "Lorem", "ipsum", "dolor", "sit"}; | val words: Array<String> = arrayOf("Lorem", "ipsum", "dolor", "sit") |

* java의 primitive type은 kotlin의 Array 클래스의 타입 인자로 사용할 수 없다. 따라서 primitive type을 인자로 갖는 배열을 표현하기 위해 각 primitive type에 대응하는 특수한 클래스를 제공한다.

| java | kotlin |
| --- | --- |
| byte[] | kotlin.ByteArray |
| double[] | kotlin.DoubleArray |
| float[] | kotlin.FloatArray |
| int[] | kotlin.IntArray |
| long[] | kotlin.LongArray |
| short[] | kotlin.ShortArray |

* 일반 Array 클래스와 마찬가지로, java의 primitive type을 위한 배열을 생성하는 함수 또한 kotlin 표준 라이브러리에 포함되어 있다. 만약 primitive type이 아닌 wrapper type 배열을 사용한다면 kotlin의 일반 Array 클래스를 사용할 수 있다.

| java | kotlin |
| --- | --- |
| int[] intArr = new Int[]{1, 2, 3, 4, 5}; | val intArr: IntArray = intArrayOf(1, 2, 3, ,4 ,5) |
| Integer[] intArr = new Int[]{1, 2, 3, 4, 5}; | val intArr: Array<Int> = arrayOf(1, 2, 3, 4, 5) |

* 위의 예제를 보고 든 생각 : kotlin에서 primitive type 이라는 개념은 없다. primitive + wrapper 를 하나의 객체 타입으로 받기 때문이다. 여기서 wrapper 클래스를 하나의 객체라고 본다면 primitive type 대신 wrapper 객체(기본 타입으로써)를 사용한다고 생각할 수 있겠다. 물론 컴파일을 거쳐 primitive와 같은 기능을 갖지만 개념상 그럴수도 있겠다는 생각이 듦.

16. 자바로 작성된 코드에서 배열을 매개변수로 받거나 가변인자를 사용하는 경우, 스프레드 연산자(별표)를 함께 사용해야 코틀린의 배열을 인자로 전달할 수 있다. 코들린으로 작성된 함수는, 가변인자에 배열을 전달하는 경우에만 스프레드 연산자를 사용한다.

```
// java code
public void foo(int[] arr){ ... }
public void bar(String... args){ ... }

// kotlin에서 위의 함수를 호출
val intArr: IntArray = intArrayOf(1, 2, 3, 4, 5)
foo(*intArr) // arr는 변수 -> 가변인자

val stringArr: Array<String> = arrayOf("Lorem", "ipsum" ,"dolor")
bar(*stringArr) // args도 변수 -> 가변인자
```

```
// kotlin code
fun foo(arr: Array<Int>){ ... }
fun bar(vararg args: String){ ... }

val intArr: Array<Int> = arrayOf(1, 2, 3, 4, 5)
foo(intArr) // arr 불변인자

val stringArr: Array<String> = arrayOf("Lorem", "ipsum", "dolor")
bar(*sringArr) args 가변인자
```

17. kotlin 에서는 컬랙션 내 자료의 수정 가능 여부에 따라 컬렉션의 종류를 구분한다.

```
kotlin.collections.Iterable   <--   kotlin.collections.MutableIterable
           |                                        |
kotlin.collections.Collection <--   Kotlin.collections.MutableCollection
           |                                        |
kotlin.collections.List       <--   kotlin.collections.MutableList        
```

* immutable 컬렉션의 경우, 자료를 조회를 위한 함수만 있다. 따라서 자료가 한 번 할당되면 변경할 수 없다.

~~~
// 수정 불가능한 리스트 생성
val immutableList: List<String> = listOf("Lorem", "ipsum")

// 컴파일 에러: 자료 수정을 위한 함수를 지원하지 않음
immutableList.add("dolor")

// 수정할 수 있는 리스트 생성
val mutableList: MutableList<String> = arrayListOf("Lorem", "ipsum")
mutableList.add("dolor")

// 자료를 수정할 수 없는 자료형으로 재할당
val immutableList2: List<String> = mutableList
// 컴파일 에러: 자료 수정을 위한 함수를 지원하지 않음
immutableList2.add("sit")
~~~

* Java Collection의 get/set과 같은 메서드 kotlin에서 사용법 

~~~
val immutableList: List<String> = listOf("Lorem", "ipsum", "dolor", "sit")

// 첫번째 항목 읽기 - get(0)과 동일
val firstItem: String = immutableList[0]

// 컴파일 에러: 값 설정 - set(0)과 동일
immutableList[0] = "Lollypop"

val mutableList: MutableList<String> = arrayListOf("Lorem", "ipsum", "dolor", "sit")

// 자료 변경 가능
mutableList[0] = "Lollypop"
~~~

* Set, Map도 List와 동일한 규칙이 지정되며, 수정 가능한 인터페이스와 수정 불가능한 인터페이스 두 종류의 인터페이스가 제공됩니다.

18. 컬렉션 생성 메소드 정리

| 함수명 | 수정가능 여부 | 리턴 타입 |
| --- | --- | --- |
| listOf() | X | kotlin.collections.List |
| arrayListOf() | O | kotlin.collections.ArrayList |
| setOf() | X | kotlin.collections.Set |
| hashSetOf() | O | kotlin.collections.HashSet |
| linkedSetOf() | O | kotlin.collections.LinkedSet |
| sortedSetOf() | O | kotlin.collections.TreeSet |
| mapOf() | X | kotlin.collections.Map |
| hashMapOf() | O | kotlin.collections.HashMap |
| linkedMapOf() | O | kotlin.collections.LinkedHashMap |
| sortedMapOf() | O | kotlin.collections.SortedMap |

19. Pair 형태의 자료구조를 편리하게 생성할 수 있는 to 함수

```
val immutableMap: Map<String, Int> = mapOf(Pair("A", 65), Pair("B", 66))

// 키 A에 해당하는 값 - get("A")와 동일
val code: Int = immutableMap["A"]

// 컴파일 에러: 값 설정 - put("C", 67)과 동일
immutableMap["C"] = 67

val mutableMap: HashMap<String, Int> = hashMapOf(Pair("A", 65), Pair("B", 66))

// 자료 변경 가능
mutableMap["C"] = 67
```

* 위의 표현식을 to 함수를 사용하여 바꾸면 아래처럼 사용가능하다.

```
val map: Map<String, Int> = mapOf("A" to 65, "B" to 66)
```

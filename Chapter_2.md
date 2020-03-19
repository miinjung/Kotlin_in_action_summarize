# Chapter 2. 코틀린 기초<br>
##### 2장에서는 첫번째로 variable, function, class 개념 학습 
##### 코틀린 내의 여러 제어구조 학습
##### 스마트 캐스트에 대한 학습<br><br><br>

## 1. 기본 요소 : 함수와 변수<br>
### 함수<br>
```kotlin
fun max (a : Int): Int{
    return if(a>b) a else b
}
```
<br>
- 함수 선언시, fun 사용
- 괄호와 반환 타입 사이에 콜론(:)으로 구분<br><br>
> #### 문(statement)과 식(expression)의 구분<br>
> 식(expression) : 값을 만들어내며 다른 식의 하위요소로 계산에 참여가능<br>
> 문 (statement) : 가장 안쪽 블록의 최상위 요소로 존재하며 아무런 값을 만들어내지 않음<br>
> 코틀린 - 식(expression) / 자바 - 문 (statement)<br><br>

**식이 본문인 함수**
```kotlin
fun max (a : Int): Int = if(a>b) a else b
```
<br>
- 식 하나로 이루어진 경우 중괄호를 없애고, return을 제거한 후, 등호를 식 앞에 붙여서 함수 표현가능<br>
- 반환 타입 생략 가능 (타입추론 > 정적 타입 지정 언어)<br><br>

### 변수<br>
```kotlin
val tmp_1 = 1
val tmp_2 : Int = 2
```
<br>
- 변수 선언시, 타입 지정을 생략하는 경우가 흔함 (타입추론)
- 타입을 지정하는 경우, 변수명 뒤에 타입을 명시함<br><br>

> #### 변경 가능한 변수와 변경 불가능한 변수<br>
> val : 변경 불가능한 참조를 저장하는 변수(자바에서의 final) / 참조가 가르키는객체의 내부값은 변경가능(ex. arrayList.add) <br>
> var : 변경 가능한 참조 (자바에서의 일반변수)<br>
> **기본적으로 val로 선언**하고 이후 필요에 따라 var로 변경하라 (권장사항)<br>
<br>

### 문자열 템플릿
```kotlin
val name = "Minjung"
val fullName = "Choi $name"
```
<br>
- 문자열 리터럴의 필요한 곳에 변수를 넣되 변수 앞에 $를 추가해야 함<br>
- '$'문자를 문자열에 넣고 싶으면 \를 같이 사용해야 함 (ex. "\\$")<br>
- 변수명 바로 뒤에 한글을 붙일 경우 'unresolved reference'오류 발생 {}를 넣어줘야 함(ex. "${name}님 안녕하세요")<br><br><br>

## 2. 클래스와 프로퍼티<br>
```kotlin
class Person(val name : String){
    //TODO
}
```
<br>
- 'public'이 default라 따로 명시 안함 (자바는 private)
- 값 객체 생성시 getter/setter가 필요없음

### 프로퍼티
```kotlin
class Person(
    val name : String, 
    var isMarried : Boolean
)
```
<br>
- **자바의 필드와 접근자 메소드를 대신함**
- val : 읽기 전용 프로퍼티 / 게터만 생성
- var : 쓸 수 있는 프로퍼티 / 케터와 세터 둘다 생성<br><br>

### 커스텀 접근자
```kotlin
class Rectangle (val height : Int, val width : Int){
    val isSquare : Boolean
        get(){
            return height == width
        }
}
```
<br>
- 자체 값을 저장하는 필드 필요없음
- 게터만 정의하여 구현 가능<br><br>

### 디텍터리와 패키지
- 코틀린도 마찬가지로 패키지단위로 불러옴(import)
- 패키지별로 디렉터리를 구성하는 것을 권장
- 자바에 있는 패키지/디렉터리 사용 가능 (자바와의 호환을 위하여)<br><br>

## 3. 서택 표현과 처리 : enum / when<br>
### enum
```kotlin
enum class Color{
    RED, YELLOW, GREEN
} // 값 열거만
enum class Color(
    val r : Int, val g : Int, val b : Int
){
    RED(255,0,0), YELLOW(255,255,0), GREEN(0,255,0);
    
    fun rgb() = (r*256+ g) * 256 + b
}
```
<br>
- 'enum'은 소프트키워드라 불림 (class 앞에 있을 때만 특별한 의미를 지니고 다른 때에는 이름으로 사용가능)
- 프로퍼티나 메소드 정의 가능
- 프로퍼티값 지정과 메소드 정의 사이에 세미콜론(;)이 필수(코틀린내에서 유일하게 ;이 필수)<br><br>
### when
```kotlin
fun feePolicy(age : String)=
    when(age){
        "baby" -> 0
        "children" -> 1500
        "youth" -> 3000
        "adult" -> 4500
    }
```
<br>
- 자바에서의 switch와 동일 기능
- 자바와 달리 break를 넣지 않아도 됨
- 콤마(,)를 사용함으로써 한 분기 안에 여러값을 매치할 수 있음
- 분기 조건은 임의의 객체를 허용 (collection)
- 아미 인자 없이 분기의 조건을 boolean 결과를 계산하는 식으로 설정 가능 (이는 가독성이 떨어짐)<br><br>

### 스마트 캐스트
```kotlin
fun findType(tmp : Any){
    if(tmp is Int){
        //TODO
    }else if(tmp is String){
        //TODO
    }else{
        //TODO
    }
}
```
<br>
- 'is'를 사용해 변수 타입 검사 (자바의 instanceof)
- 변수 타입 검사 이후에 컴파일러에서 캐스팅을 해줌
- 스마트 캐스트를 사용하기 위해 해당 프로퍼티는 반드시 val이어야 한다.
- 명시적 캐스팅을 위해서는 'as'키워드를 사용함<br><br>

## 4. 대상을 이터레이션 : while / for<br>
### while/do-while
```kotlin
while(조건){
    //TODO

```
<br>
### 수에 대한 이터레이션: 범위와 수열
```kotlin
fun setArray(){
    val arr : array<Int> = arrayOf()
    for(i in 0..10){
        array[i] = i
    }
    for(i in 0 until 10){
        array[i] = i
    }
    for(i in 10 downTo 0 step 2){
        array[i] = i
    }
}
```
<br>
- 코틀린의 범위는 폐구간이다. 이는 두번째 값이 항상 범위에 포함되는 것이다.
- '..'은 범위의 끝값을 포함
- 'until'은 범위의 끝값을 포함하지 않음
- 'downTo'은 증가값을 음수로 만듦
- 'step'은 증가값의 크기를 정의함<br><br>

### in으로 컬렉션이나 범위의 원소 검사
```kotlin
fun isLstter(tmp : Char) = tmp in 'a'..'z'||'A'..'Z'
```
<br>
- 'in'을 사용하여 어떤 값이 범위에 속하는지 검사 가능 ('!in'도 가능)
- 집합 내의 요소를 확인하는 용도로도 활용 가능<br><br>

## 5. 코틀린의 예외처리<br>
```kotlin
val num = try{
    //TODO
}catch(e: NumberFormatException){
    //TODO
}finally{
    //TODO
}
```
<br>
- 코틀린의 예외처리는 자바와 유사
- 자바와 달리 throw는 식이라 다른 식에 포함가능
- 예외 인스턴스를 만들 때 'new'를 붙일 필요가 없음
- try, catch, finally를 사용하여 처리
- try를 식으로 활용 가능

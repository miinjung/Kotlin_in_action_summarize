# Chapter 2. 코틀린 기초<br>
##### 2장에서는 첫번째로 variable, function, class 개념 학습 
##### 코틀린 내의 여러 제어구조 학습
##### 스마트 캐스트에 대한 학습<br><br>

## 1. 기본 요소 : 함수와 변수<br>
### 함수<br><br>
```kotlin
fun max (a : Int): Int{
    return if(a>b) a else b
}
```
- 함수 선언시, fun 사용
- 괄호와 반환 타입 사이에 콜론(:)으로 구분<br><br>
> **문(statement)과 식(expression)의 구분**<br>
> 식(expression) : 값을 만들어내며 다른 식의 하위요소로 계산에 참여가능<br>
> 문 (statement) : 가장 안쪽 블록의 최상위 요소로 존재하며 아무런 값을 만들어내지 않음<br>
> 코틀린 - 식(expression) / 자바 - 문 (statement)<br><br>

**식이 본문인 함수**
```kotlin
fun max (a : Int): Int = if(a>b) a else b
```
- 식 하나로 이루어진 경우 중괄호를 없애고, return을 제거한 후, 등호를 식 앞에 붙여서 함수 표현가능<br>
- 반환 타입 생략 가능 (타입추론 > 정적 타입 지정 언어)<br><br>

### 변수<br><br>
```kotlin
val tmp_1 = 1
val tmp_2 : Int = 2
```
- 변수 선언시, 타입 지정을 생략하는 경우가 흔함 (타입추론)
- 타입을 지정하는 경우, 변수명 뒤에 타입을 명시함<br><br>

>**변경 가능한 변수와 변경 불가능한 변수**<br>
> val : 변경 불가능한 참조를 저장하는 변수(자바에서의 final) / 참조가 가르키는객체의 내부값은 변경가능(ex. arrayList.add) <br>
> var : 변경 가능한 참조 (자바에서의 일반변수)<br>
> **기본적으로 val로 선언**하고 이후 필요에 따라 var로 변경하라 (권장사항)<br><br>

### 문자열 템플릿
```kotlin
val name = "Minjung"
val fullName = "Choi $name"
```
- 문자열 리터럴의 필요한 곳에 변수를 넣되 변수 앞에 $를 추가해야 함<br>
- '$'문자를 문자열에 넣고 싶으면 \를 같이 사용해야 함 (ex. "\$")<br>
- 변수명 바로 뒤에 한글을 붙일 경우 'unresolved reference'오류 발생 {}를 넣어줘야 함(ex. "${name}님 안녕하세요")<br><br>

## 2. 클래스와 프로퍼티<br>

## 3. 서택 표현과 처리 : enum / when<br>
## 4. 대상을 이터레이션 : while / for<br>
## 5. 코틀린의 예외처리<br>

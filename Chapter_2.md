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
>>> #### 문(statement)과 식(expression)의 구분<br>
>>> 식(expression) : 값을 만들어내며 다른 식의 하위요소로 계산에 참여가능<br>
>>> 문 (statement) : 가장 안쪽 블록의 최상위 요소로 존재하며 아무런 값을 만들어내지 않음<br>
>>> 코틀린 - 식(expression) / 자바 - 문 (statement)<br><br>

**식이 본문인 함수**
```kotlin
fun main (a : Int): Int = if(a>b) a else b
```
- 식 하나로 이루어진 경우 중괄호를 없애고, return을 제거한 후, 등호를 식 앞에 붙여서 함수 표현가능<br><br>
- 반환 타입 생략 가능 (타입추론 > 정적 타입 지정 언어)
## 2. 클래스와 프로퍼티<br>
## 3. 서택 표현과 처리 : enum / when<br>
## 4. 대상을 이터레이션 : while / for<br>
## 5. 코틀린의 예외처리<br>

# Chapter 02

### 변수란?
  * 변하기 쉬운 값을 저장할 수 있는 메모리 공간
  * 하나의 값을 저장할 수 있는 메모리 공간
  * 변수의 선언은 `타입` `변수이름` `;`
  * 작성 규칙
    * 첫 번째 글자는 `문자`, `$`, `_`만 가능
    * 영어 대소문자 구분
    * `camelCase`가 관례
    * 길이 제한 없음
    * [예약어](../../appendix/reserved_word.md)는 사용 불가

### 리터럴(Literal)
  * 소스 코드 내에서 직접 입력된 값을 부르는 용어
  * 상수(constant)와 같은 의미
    * 프로그램에서 상수는 `값을 한 번 저장하면 변경할 수 없는 변수`로 정의
    * 따라서 이와 구별하기 위해 `Literal`이라 부름
    
  * 리터럴의 종류

| 타입      | 설명                | 예제                                              |
|---------|-------------------|-------------------------------------------------|
| 정수 리터럴  | 소수점이 없는 수         | 0, 75, -100, 02, -04, 0x5, 0xA, 0xB3, 0xAC08    |
| 실수 리터럴  | 소수점이 있는 수         | 0.25, -3.1415, 5E7(5x10^7), 0.12E-5(0.12x10^-5) |
| 문자 리터럴  | 작은 따옴표(')로 묶은 텍스트 | 'A', '안', '\t' '\u16진수'                         |
| 문자열 리터럴 | 큰 따옴표(")로 묶은 텍스트  | "ABCD", "안녕하세요."                                |
| 논리 리터럴  | true or false     | true, false                                     |

### 변수 읽기
  * 변수는 초기화 되어야 읽을 수 있음
    ```java
    public class Variable {
        public static void main(String[] args) {
            int a = 10;
            int result = a + 10;
            System.out.print("a + 10 = " + result);
        }
    }
    ```
  * 실행 결과
    ```bash
    a + 10 = 20
    ```

  * 변수는 중괄호 {} 블록 내에서 선언되고 사용됨
    ```java
    public class VariableScope {
        public static void main(String[] args) {
            int a = 10;
            if(a == 10) {
                int b = a;
            }
            else {
                b = 10; //컴파일 에러
            }
            System.out.print("a + b = " + (a + b)); //컴파일 에러
        }
    }
    ```
    
    ```java
      public class VariableScope {
          public static void main(String[] args) {
              int a = 10;
              int b; //원시 자료형(primitive type) int는 0으로 자동 초기화
              if(a == 10) {
                  b = a;
              }
              else {
                  b = 20;
              }
              System.out.print("a + b = " + (a + b));
          }
    }
      ```

  * 실행 결과
    ```bash
    a + b = 20
    ```
### 데이터 타입
  * 모든 변수에는 타입(type)이 있음
  * 타입에 따라 저장할 수 있는 값의 종류와 범위가 달라짐
  * 변수 선언 후, 변수 사용중 변경 불가

### 기본 타입(Primitive Type)
  * 정수, 실수, 문자, 논리 리터럴을 직접 저장하는 타입
  * `정수형` : byte, char, short, int, long
  * `실수형` : float, double
  * `논리형` : boolean

| 종류     | 타입         | 메모리 크기 | 범위                                          |
|--------|------------|--------|---------------------------------------------|
| 정수     | byte       | 1byte  | -128 ~ 127                                  |
| 정수     | char       | 2byte  | 0 ~ 65,535                                  |
| 정수     | short      | 2byte  | -32,768 ~ 32,767                            |
| 정수     | int        | 4byte  | -2,147,483,648 ~ 2,147,483,647              |
| 정수     | long       | 8byte  | 2^63 ~ 2^63-1                               |
| 실수     | float      | 4byte  | (+/-)1.4E-45 ~ (+/-)3.4028235E38            |
| 실수     | double     | 8byte  | (+/-)4.9E-324 ~ (+/-)1.7976931348623157E308 |
| 논리     | boolean    | 1byte  | true, false                                 |


### 타입 변환
  * 타입 변환이란 데이터 타입을 다른 데이터 타입으로 변환하는 것을 말함
  * byte -> int, int -> byte
  * 타입 변환의 종류는 `자동 타입 변환(Promotion)`, `강제 타입 변환(Casting)` 이 있음

### 자동 타입 변환(Promotion)
  * `작은 크기를 가지는 타입`이 `큰 크기를 가지는 타입`에 저장될 때 발생
  ```java
  public class Promotion {
    byte a = 10;
    int b = a; //자동 타입 변환이 발생
  }
  ```
  * 크기의 순서 
    * `byte(1) < short(2) < int(4) < long(8) < float(4) < double(8)`
    

### 강제 타입 변환(Casting)
  * 자동 타입 변환과는 반대로 `작은 크기를 가지는 타입`이 `큰 크기를 가지는 타입`에 저장될 때 사용
  ```java 
  public class Casting {
    long a = 10;
    byte b = (byte)a; //자동 타입 변환이 발생하지 않음 
    }
  ```
  * (type) 캐스팅 연산자를 사용하여 변환 시켜줘야 함

### 연산식에서의 자동 타입 변환
  * 연산은 기본적으로 같은 타입의 피연산자(operand)간에만 수행됨
  * 서로 다른 타입의 피 연산자가 있을 경우 두 피연산자 중 크기가 큰 타입으로 `Promotion`이 발생함
  ```java
  public class Operation {
    int a = 10;
    double b = 10.5;
    double result = a + b; //20.5 
}
  ```
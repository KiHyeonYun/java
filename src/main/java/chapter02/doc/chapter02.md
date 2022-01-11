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
  
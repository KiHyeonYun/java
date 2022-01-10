# Chapter 01
### 프로그래밍 언어란?
  * 컴퓨터가 이해할 수 있는 언어
  * Low Level language
    * 어셈블리어, 기계어
  * High Level language
    * c, C++, Java...

## 자바란?
  * Oak -> java
  * 인터넷 활성화 -> Web Application 구축용 언어 -> Java

## 자바의 특징
  * 높은 이식성
  * 객체 지향 언어(OOP)
  * 함수적 스타일 코딩(ver 8 ↑)
  * 메모리 자동 관리(GC)
  * 다양한 Application 개발 가능
  * 쉬운 멀티 스레드 구현
  * 동적 로딩 지원
  * 막강한 오픈소스 라이브러리

## JVM(Java Virtual Machine)
  * .java -> compiler(javac) -> .class -> JVM(java.exe) -> window or Mac or Linux...
  * OS환경에 맞게 기계어로 번역 해주는 JVM
  * Write once, Run anywhere
  * 속도가 느림 -> JIT 컴파일러로 격차 ↓

## Hello java 
```java
//클래스 이름 - Hello
public class Hello { 
    //메소드 이름 - main
    public static void main(String[] args) {
        System.out.println("Hello world!");
    } //메소드 블록
}
```
  * 클래스 : 필드 또는 메소드를 포함하는 블록 
  * 메소드 : 어떤 일을 처리하는 실행문들을 모아 놓은 블럭
  * main() : 프로그램 실행 진입점 (entry point)


## Cmd 
```bash
//컴파일
javac javaFileName.java
//JVM으로 실행
java Hello
``` 


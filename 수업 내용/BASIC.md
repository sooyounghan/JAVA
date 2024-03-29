-------
### cmd 내 자바 컴파일 및 실행
-------
  1. JAVA / JAVAC : JAVA Complier (java-version\bin\… : Java 실행 시 필요한 실행파일 제공)
  2. Complie Processing : .java → JAVAC → .class

-------
### JAVA 변수 설정
-------
 1. 시스템 변수 설정 : JAVA_HOME 변수 Java Home Directory(..\dk-version(ex)jdk-11))를 추가해 설정
 2. 환경 변수 설정 : PATH → %JAVA_HOME%\bin : JAVA의 컴파일러 디렉토리 설정
     - %변수%, \ : 하위 디렉토리
     - ; : 구분자 ( C:\Program Files\Common Files\Oracle\Java\javapath;%JAVA_HOME%\bin;…)
       
 4. Java 버전 확인 : java –version OR javac –version
------
## 자바의 특징
------
  1. 이식성이 높음 (= 타운영체제와의 호환성이 높다.)
  2. 객체 지향 언어(OOP : Object Oriented Programming) (= 부품 객체 생성 → 조합해 전체 프로그램을 완성)
  3. 캡슐화(Encapsulation), 상속(Inheritance), 다형성(Polyporhism) 기능 지원
  4. 메모리를 자동으로 관리 (사용하지 않는 객체를 자동에서 메모리에서 제거 → Garbage Collector   

------
#### JDK(Java Development Kit) = JRE(Java Runtime Enviornment = JVM + 표준 클래스 라이브러리) + 개발 도구
------
 + JDK : 자바 프로그램 개발 및 실행을 위한 Kit
 + JRE : 자바 프로그램 실행을 위한 Kit

------
### 자바 실행 과정
------
  1. JAVA 소스 파일(*.java) 작성
  2. 자바 컴파일러(javac.exe)로 바이트 코드 파일(.class → 기계어 형태) 생성
  3. JVM(바이트 코드 파일을 운영체제를 위한 기계어로 번역 및 실행 역할) 구동 명령어(java.exe)로 실행   
     : 바이트 코드 파일(*.class)은 운영체제와 직접 호환이 아닌 JVM를 통해 실행 (*.class – JVM – OS) → 이식성이 높음
     
     ![다운로드](https://github.com/sooyounghan/JAVA/assets/34672301/af1fc54f-ca81-456a-9bbc-8469871bc021)
-----
### <JVM(Java Virtual Machine)>
-----
  1. 자바를 실행하기 위한 가상 기계
  2. 자바 기반 모든 어플리케이션은 이 위에서 실행되믈 반드시 필요
  3. OS에 종속적임.

-----
### 이클립스(Eclipse)
-----
  1. Workspace : 이클립스에서 생성한 프로젝트가 기본적 저장되는 디렉토리
> .metadata 디렉토리 : 자동 생성, 이클립스 실행 시 필요 메타데이터 저장
  2. Perspective : 개발 프로젝트 종류별 유용한 view의 묶음
  3. View : Perspective 구성하는 작은 창으로 여러가지 목적에 맞게 내용 표시

#### <이클립스 팁 (참조)>
 - 버전 확인 Eclipse – Help – About Eclipse IDE – Version
 - 사용 용도에 따른 Perspective 변경 : Eclipse – Window – Persepective – 필요부분 확인
 - 환경설정
   + Eclipse – Preferences – General – Appearance - Colors and Fonts
   + Eclipse – Preferences – General – Appearance - Content Type – Text – Default encoding : UTF-8 (텍스트 인코딩)   
   + Eclipse – Preferences – General – Appearance - Java Properties File(Spring) – Default encoding : UTF-8 (Spring 인코딩)   
   + Eclipse – Preferences – General – Appearance - Editors – Text Editors – Show line numbers   
   + Eclipse – Preferences – General – Appearance - Spelling – Encoding : UTF-8 (개발 간 인코딩)   
   + Eclipse – Preferences – General – Appearance - Web Browser – Chorme (웹 서버 구현 간 기본 웹)   
   + Eclipse – Preferences – General – Appearance - Workspace – Text file encoding : UTF-8 (텍스트 파일 인코딩 설정)   
   + Eclipse – Preferences – Java – Complier – Complier compliance level (java version check) (컴파일 버전) - Installed JREs
   + Eclipse – Preferences – Web – CSS/HTTP/JSP Files – Encoding : UTF-8 (웹 인코딩 설정)
   + Eclipse – Preferences - XML – XML Files - Encoding : UTF-8 (XML 인코딩 설정)
- JAVA Project Create : File – New – Other – Java – Java Project

-----
### 의존성 모듈
-----
  - JAVA 8 이전 표준 API 제공, 11 이후 JDK가 제공하는 표준 API를 모듈별로 쪼개어 제공
  - 기본적으로 java.base 모듈 사용 가능, 다른 모듈 사용시 모듈 기술자(module-info.java)에 의존성 모듈 등록

```java
module pro1 { // 모듈 기술자
    requires java.se; 
}
```

-----
### 자바 주석
-----
  1. // : 한 줄 주석 (Ctrl + /)
  2. /* */ : 여러 줄 주석 (ctrl + Shift + /)


```java
/* 
package 패키지명;
*/
package pro1;

// class block
public class Ex01 { // 클래스는 관례상 첫글자는 대문자
	// main method block
	public static void main(String[] args) {
		System.out.println("Hello");
		System.out.println("java");
	} // main method block end
} // class block end
```
-----
### Main Method : public static void main(String[] args) {}
-----
  - Java Application의 시작 진입 지점을 의미하는 method (단 하나만 존재)
  - JVM이 자동적으로 이를 최우선으로 실행

------
### System.out.println()
------
  1. System.out :System Class의 OutputStream으로 표준 출력 화면인 모니터를 의미   
  2. System.out.println(내용) : java.io의 PrintStream Class println method → 해당 내용 출력 후 개행
     - System.out.println() : 단순 개행
     - 단축키 : syso 입력 → Ctrl + space
      
  3. System.out.print(내용) : java.io의 PrintStream Class print method → 해당 내용만 출력(미개행)
     - print()에서의 개행 : System.out.println(“\n”); → \n : Carriage Return(개행) 의미
      
  4. System.out.printf(“형식문자열”, 값1, 값2, …) : 괄호 안 첫 문자열 형식대로 내용 출력 → 여러 데이터 출력 용이   
     - %d : 정수 / %f : 실수(기본 소수점 6자리 출력) (%.숫자f : 소수점 숫자자리까지 출력, 비어있는 부분은 0으로 처리
     - %c : 문자 / %s : 문자열
       
<div align="center">
	<img width="503" alt="123" src="https://github.com/sooyounghan/JAVA/assets/34672301/0a9a66d1-5c18-4827-85dd-2e43df5468bd">
</div>

```java
// printf() method
public class PrintfEx_p90 {
	public static void main(String[] args) {
		String name = "HGD";
		long age = 25; // data type : byte, short, long ok
		double height = 180.5; // data type : float ok
		
		System.out.println(name + "\t" + age + "\t" + height); 
                                  // \t : tab escape letter or space
		System.out.printf("%10s\t%5d\t%5.1f\n", name, age, height); // same result line 10.
		System.out.printf("%10s\t%5d\t%5.1f\n", "abc", 50, 178.5); // Literal value ok.
		System.out.printf("%10s\t%5d\t%5.1f\n", "abcd", 40, 158.432); 
                                  // %.1f -> 소수점 1자리까지 출력(소수점 2번째자리에서 반올림)
		System.out.printf("%10s\t%5d\t%5.1f\n", "abcefgh", 20, 160.46); 
		System.out.println("---------------------"); // new line
		
		System.out.println("이름(println()) : " + name); // println() : new line
		System.out.print("이름(print()) : "); // print() : not new line
		System.out.print(name + "\n"); // \n : Escape 문자(개행)
		System.out.printf("이름(printf()) : %s\n", name); // printf() : not new line & format 
		                                           // name variable(String type) -> %s
		System.out.print("나이(print()) : " + age + "\n"); 
		System.out.printf("나이(printf()) : %d\n", age);	
	}
}
```

-----
Escape 문자
-----
<div align = "center">
	<img width="511" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/6025fd4c-bc69-4181-95ef-a708a39aa77b">
</div>

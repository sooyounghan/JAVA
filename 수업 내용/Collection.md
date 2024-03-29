-----
### Collection, Collection Framework
----- 
1. 사전적 의미로 요소(객체)를 수집해 저장해놓은 것
2. 컬렉션 프레임워크 (Collection Framework)

       객체들을 효율적으로 추가, 삭제, 검색할 수 있도록 제공되는 컬렉션 라이브러리
       Package : java.util 
       인터페이스를 통해 정형화된 방법으로 다양한 컬렉션 클래스 이용

3. Collection Framework 구조
<div align = "center">
<img width="321" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/a3ad62c1-9144-4824-a4c5-2122b23fea0f">
</div>

-----
### Collection 인터페이스의 메서드
-----
<div align = "center">
<img width="388" alt="다운로드 (16)" src="https://github.com/sooyounghan/JAVA/assets/34672301/fe302238-3c30-4ff6-a31e-f33352c1a9ea">
</div>

```java
/*
 * Collection Framework : Array 
 */
public class CFE {
	public static void main(String[] args) {
		/*
		 * 정수 데이터 5개를 저장하는 배열 arr
		 */
		int[] arr = new int[5];
		getArr(arr);
		
		/*
		 * 데이터 추가
		 */
		for(int i = 0; i < arr.length; i++) {
			arr[i] = (int)(Math.random() * 10) + 1;
		}
		getArr(arr);
		
		/*
		 * 데이터 변경 (가장 첫 번째 데이터의 값을 임의 데이터로 변경
		 */
		arr[0] = (int)(Math.random() * 5) + 1;
		System.out.println("arr[0] = " + arr[0]);
		System.out.println();
		
		/*
		 * 데이터 삭제
		 */
		arr[arr.length - 1] = 0; // 배열은 크기를 한 번 생성하면, 크기 조정이 불가하므로 삭제는 불가
		System.out.println("arr[arr.length - 1] = " + arr[arr.length - 1]);
		System.out.println();
		/*
		 * 배열의 갯수 출력
		 */
		System.out.println("arr length = " + arr.length);
	}
	
	public static void getArr(int[] arr) {
		/*
		 * 배열의 요소를 출력하는 메서드
		 */
		
		System.out.print("arr = [ ");
		for(int i = 0; i < arr.length; i++) {
			System.out.print(arr[i] + " ");
		}
		System.out.println("]");
		System.out.println();
	}
}
```

-----
### List Collection
-----
1. 인덱스로 관리
2. 중복해서 객체를 저장 가능

<div align = "center">
<img width="224" alt="다운로드 (17)" src="https://github.com/sooyounghan/JAVA/assets/34672301/a5c99c34-8ec0-4c61-b46b-f315d4ef59b3">
</div>

3. List Collection Method
<div align = "center">
<img width="411" alt="다운로드" src="https://github.com/sooyounghan/JAVA/assets/34672301/52b7e59a-200a-47a4-92fe-1706737a1b9c">
</div>

-----
### ArrayList
-----
1. ArrayList는 기존의 Vector를 개선 (구현원리는 기능적으로 동일)
2. Vector는 자체적으로 동기화 처리되어있으나 ArrayList는 그렇지 않음

< ArrayList Class >
<div align = "center">
<img width="253" alt="다운로드 (1)" src="https://github.com/sooyounghan/JAVA/assets/34672301/a4d88543-ce9b-471e-89f5-b849c4d3cc1c">
</div>
1. 저장 용량 (초기 용량 : 10 / 저장 용량을 초과한 객체들이 들어오면 자동적으로 늘어남 (고정도 가능))
 객체 제거 (바로 뒤 인덱스부터 마지막 인데스까지 모두 앞으로 1씩 당겨짐)
2. ArrayList Class 주요 Method
    - ArrayList의 갯수 출력 : size()
    - 데이터 추가 : boolean add(Object o)
     
      매개변수는 Object 객체이므로 모든 객체에 대해 수용 가능 (다양한 데이터 타입 가능)
      가능 예)
        arr_list.add(3.14); // arr_list.add((Double)3.14); // Auto-boxing
        arr_list.add("String"); // arr_list.add(String Instance);
        arr_list.add(true); // arr_list.add((Boolean)true or false); // Auto-boxing
        arr_list.add('A'); // arr_list.add((Character)'A'); // Auto-boxing
        arr_list.add(new Bird()); // arr_list.add(User-type Object); // 사용자가 정의한 객체도 가능[Object형 이므로]

 
   - 특정 인덱스에 저장된 데이터 가져오기 : Object get(int index)
   - 데이터 변경  데이터의 값을 변경 : Object set(int index, Object element)

         가능 예)
           arr_list.set(0, 3.14); // arr_list.set(0, (Double)3.14); // Auto-boxing
           arr_list.set(1, "String"); // arr_list.set(1, String Instance);
           arr_list.set(2, true); // arr_list.set(2, (Boolean)true or false); // Auto-boxing
           arr_list.set(3, 'A'); // arr_list.set(3, (Character)'A'); // Auto-boxing
           arr_list.set(4, new Bird()); // arr_list.set(4, User-type Object); // 사용자가 정의한 객체도 가능[Object형 이므로]

   - 데이터 삭제 (Object remove(int index)) / 데이터 삭제 (boolean remove(Object o))

         사용 예 : arr_list.remove("String");
         // 문자열 String가 존재해서 삭제되면 true, 존재하지 않아 삭제가 불가능하면 false 반환
         사용 예 : arr_list.remove("string");
         // 문자열 string가 존재해서 삭제되면 true, 존재하지 않아 삭제가 불가능하면 false 반환
         ** 문자열 객체 String과 string은 다른 객체

   - ArrayList 데이터 모두 삭제, 즉 모두 완전히 비움 (void clear())
   - ArrayList 내 비어있는지 확인 (boolean isEmpty())

```java
import java.util.*; // ArrayList Package Import

/*
 * Collection Framework
 *  - 객체(데이터)를 추가, 삭제, 삽입 등을 효율적으로 수행할 수 있도록 도와주는 컬렉션 라이브러리
 *  - java.util Package
 *  - 정형화된 인터페이스를 통해 이를 활용해 다양한 컬렉션 클래스 이용
 *  
 *  <List Collection>
 *  1. 데이터의 순서를 유지하고, 중복을 허용하는 Collection Interface
 *  2. 구현 클래스 : ArrayList, LinkedList, Vector, Stack 등
 *  
 *  <Set Collection>
 *  1. 데이터의 순서를 유지하지 않으며, 중복을 허용하지 않는 Collection Interface
 *  2. 구현 클래스 : HashSet, TreeSet 등
 *  
 *  <Map Collection>
 *  1. 데이터의 순서를 유지하지 않으며, 키와 값이라는 쌍으로 이루어져 있음
 *  2. 키는 중복을 허용하지 않으며, 값은 중복을 허용함
 *  3. 구현 클래스 : HashMap, TreeMap, HashTable, Properties 등
 */

public class ArrayList_Ex {
	public static void main(String[] args) {
		/*
		 * 정수 데이터 5개를 저장하는 ArrayList
		 */
		List arr_list = new ArrayList(); // 다형성
		// List arr_list = new Vector(); // Vector 또한 List 인터페이스의 구현 클래스이므로 다형성을 구현하여 코드의 유연성 증가
		// List arr_list = new LinkedList(); // LinkedList 또한 List 인터페이스 구현 클래스이므로 다형성을 구현하여 코드의 유연성 증가
		System.out.println("arr_list = " + arr_list); // []
		
		/*
		 * ArrayList의 갯수 출력 : size()
		 */
		System.out.println("arr_list = " + arr_list.size()); // 0
		
		/*
		 * 데이터 추가 : boolean add(Object o)
		 *   - 매개변수는 Object 객체이므로 모든 객체에 대해 수용 가능 (다양한 데이터 타입 가능)
		 *   - 가능 예)
		 *     arr_list.add(3.14); // arr_list.add((Double)3.14); // Auto-boxing
		 *     arr_list.add("String"); // arr_list.add(String Instance);
		 *     arr_list.add(true); // arr_list.add((Boolean)true or false); // Auto-boxing
		 *     arr_list.add('A'); // arr_list.add((Character)'A'); // Auto-boxing
		 *     arr_list.add(new Bird()); // arr_list.add(User-type Object); // 사용자가 정의한 객체도 가능[Object형 이므로]
		 */
		System.out.println("<ArrayList add(Object e)>");
		for(int i = 0; i < 5; i++) { // 5개의 원소 추가
			arr_list.add((int)(Math.random() * 5) + 1); // arr_list((Integer) i); // Auto-boxing
		}
		System.out.println("arr_list = " + arr_list.size()); // 5
		System.out.println("arr_list = " + arr_list); // 1 ~ 5까지 무작위 난수 5개 저장된 ArrayList 출력
		
		/*
		 * 특정 인덱스에 저장된 데이터 가져오기 : Object get(int index)
		 */
		System.out.println("<ArrayList Object get(int index))>");
		System.out.println("arr_list index 0 = " + arr_list.get(0));
		System.out.println("arr_list index 1 = " + arr_list.get(1));
		System.out.println("arr_list index 2 = " + arr_list.get(2));
		System.out.println("arr_list index 3 = " + arr_list.get(3));
		System.out.println("arr_list index 4 = " + arr_list.get(4));
		getArrayList(arr_list);
		
		/*
		 * 데이터 변경 : (가장 첫 번째 데이터의 값을 임의 데이터로 변경 : Object set(int index, Object element)
		 * 	  - 가능 예)
		 *     arr_list.set(0, 3.14); // arr_list.set(0, (Double)3.14); // Auto-boxing
		 *     arr_list.set(1, "String"); // arr_list.set(1, String Instance);
		 *     arr_list.set(2, true); // arr_list.set(2, (Boolean)true or false); // Auto-boxing
		 *     arr_list.set(3, 'A'); // arr_list.set(3, (Character)'A'); // Auto-boxing
		 *     arr_list.set(4, new Bird()); // arr_list.set(4, User-type Object); // 사용자가 정의한 객체도 가능[Object형 이므로]
		 */
		System.out.println("<ArrayList set(int index, Object element)>");
		for(int i = 0; i < arr_list.size(); i++) {
			arr_list.set(i, (int)(Math.random() * 5) + 1); // Auto-Boxing
		}
		getArrayList(arr_list);
		
		/*
		 * 데이터 삭제 (Object remove(int index))
		 * 데이터 삭제 (boolean remove(Object o))
		 *   - 사용 예 : arr_list.remove("String"); // 문자열 String가 존재해서 삭제되면 true, 존재하지 않아 삭제가 불가능하면 false 반환
		 *   - 사용 예 : arr_list.remove("string"); // 문자열 string가 존재해서 삭제되면 true, 존재하지 않아 삭제가 불가능하면 false 반환
		 *    * 문자열 객체 String과 string은 다른 객체
		 */
		System.out.println("<ArrayList remove(int index)>");
		for(int i = arr_list.size() - 1; i >= 0; i--) { // ArrayList는 삭제하면 유동적으로 그 크기가 감소하므로 맨끝부터 확인
			arr_list.remove(i);
			getArrayList(arr_list);
		}
		
		/*
		 * ArrayList 데이터 모두 삭제, 즉 모두 완전히 비움 (void clear())
		 * ArrayList 내 비어있는지 확인 (boolean isEmpty())
		 */
		arr_list.clear();
		System.out.println("ArrayList Empty = " + arr_list.isEmpty());
	}
	
	public static void getArrayList(List list) {
		/*
		 * 배열의 요소를 출력하는 메서드 (매개변수 : List Interface 타입) [다형성]
		 */
		
		System.out.print("arr = [");
		for(int i = 0; i < list.size(); i++) {
			System.out.print((i != list.size() - 1) ? list.get(i) + ", " : list.get(i));
		}
		System.out.println("]");
	}
}
```

3. ArrayList의 특징
  A. 장점 : 구조가 간단하고 데이터를 읽는데 걸리는 시간(접근 시간, Access Time)이 짧음
  B. 단점 
    - 배열의 크기를 변경할 수 없음 (변경해야 하는 경우 - 새로운 배열 생성 후 데이터 복사)
    - 크기 변경을 위해 큰 배열 생성하면, 메모리 낭비
    - 비순차적 데이터의 추가, 삭제에 시간이 많이 걸림
    
          * 순차적인 데이터 추가(끝 추가)와 삭제 (끝 부터 삭제)는 빠름

-----
### Vector
-----
<div align = "center">
<img width="302" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/e76507f3-22e2-47c3-ad6c-89a1621b5561">
</div>

< Vector Class Method 일부 >
  1. 생성자
     -  1. Vector() : 기본 크기가 10인 Vector 생성 (할당된 공간이 초과하는 순간, 2배 만큼 공간 할당)
     -  2. Vector(int initialCapacity) : 매개변수로 받은 initialCapity 공간 만큼 Vector 생성
        > (할당된 공간이 초과하는 순간, 2배 만큼 공간 할당)
     -  3. Vector(int initialCapacity, int capacityIncrement) : initialCapacity로 초기 공간 지정, 용량 증가 필요 시, capacityIncrement만큼 할당

  2. 데이터 삽입 : boolean add(Obejct o)
     > 데이터 삽입 완료 : true
     > 데이터 삽입 실패 : false

  3.  Vector 내 현재 존재하는 요소의 크기 확인 : int size() 

  4.  Vector 할당 공간 확인 : int capacity() 

     * Vector Class 내 고유 메서드로서, Vector 내 할당된 공간을 확인

  5. Vector 내 빈 공간을 없앰 (capacity() = size()) : void trimToSize()

```java
import java.util.*; // List Interface Package Import

/*
 * Vector Class (List Interface)
 *   - Vector Class의 생성자
 *     1. Vector() : 기본 크기가 10인 Vector 생성 (할당된 공간이 초과하는 순간, 2배 만큼 공간 할당)
 *     2. Vector(int initialCapacity) : 매개변수로 받은 initialCapity 공간 만큼 Vector 생성
 *        (할당된 공간이 초과하는 순간, 2배 만큼 공간 할당)
 *     3. Vector(int initialCapacity, int capacityIncrement) : initialCapacity로 초기 공간 지정, 용량 증가 필요 시, capacityIncrement만큼 할당)
 */
public class Vector_Ex {
	public static void main(String[] args) {
		Vector vector = new Vector(); // 초기 공간이 10인 기본 Vector 객체 생성
		// List vector = new Vector(); // 초기 공간이 10인 기본 Vector 객체 생성 (다형성)
		// List vector_initial = new Vector(20); // 초기 공간이 20인 기본 Vector 생성 (할당된 용량 초과시 2배로 할당)
		// List vector_initial2 = new Vector(20, 20); // 초기 공간이 20이고, 용량 초과 시 20만큼 할당
		System.out.println("Vector = " + vector); // []
		System.out.println("Vector Capacity = " + vector.capacity());
		System.out.println("Vector Size = " + vector.size());
		
		System.out.println("<Vector add(Obejct o)>");
		/*
		 * 데이터 삽입 : boolean add(Obejct o)
		 *   - ArrayList와 동일
		 */
		/*
		 * int size() : Vector내 현재 존재하는 요소의 크기 확인
		 * int capacity() : Vector 할당 공간 확인
		 *  ** Vector capacity() Method : Vector Class 내 고유 메서드로서, Vector 내 할당된 공간을 확인
		 */
		for(int i = 0; i < vector.capacity(); i++) {
			vector.add(i);
		}
		System.out.println("Vector = " + vector);
		
		System.out.println("<Vector Capacity, Size (add 10)>");
		System.out.println("Vector Capacity = " + vector.capacity()); // 기본 공간인 10을 초과하지 않았으므로, 10
		System.out.println("Vector Size = " + vector.size()); // 기본 공간인 10만큼 들어갔으므로 size는 10
		
		System.out.println("<Vector add(Obejct o)>");
		for(int i = 0; i < 5; i++) {
			vector.add(i);
		}
		System.out.println("Vector = " + vector);
		
		System.out.println("<Vector Capacity, Size (add 5)>");
		System.out.println("Vector Capacity = " + vector.capacity()); // 기본 공간 10을 초과하였고, 생성자에 추가적으로 할당하지 않았으므로 2배 증가
		System.out.println("Vector Size = " + vector.size()); // 5개를 추가했으므로 size는 15
		
		System.out.println("<Vector add(Obejct o)>");
		for(int i = 0; i < 19; i++) {
			vector.add(i);
		}
		System.out.println("Vector = " + vector);
		
		System.out.println("<Vector Capacity, Size (add 19)>");
		System.out.println("Vector Capacity = " + vector.capacity()); // 확장된 공간 20을 초과하여, 2배인 40으로 증가
		System.out.println("Vector Size = " + vector.size()); // 19개를 추가했으므로 size는 34
	}
}
```

-----
###  ArrayList와 LinkedList 성능 비교
-----
1. 순차적 데이터 추가 / 삭제 : ArrayList가 더 빠름
2. 비순차적 데이터 추가 / 삭제 : LinkedList가 더 빠름
3. 접근 시간(Access Time) : ArrayList가 더 빠름 (ArrayList는 연속적 데이터 저장 구조)
<div align = "center">
<img width="359" alt="다운로드 (2)" src="https://github.com/sooyounghan/JAVA/assets/34672301/3d8da940-65f7-4bb8-8473-521d0eb3ea92">
</div>

```java
import java.util.*;

/*
 * ArrayList vs LinkedList
 *  1. 순차적 데이터 추가 / 삭제 : ArrayList
 *  2. 비순차적 데이터 추가 / 삭제 : LinkedList
 *  3. 접근시간(Access Time) : ArrayList
 */
public class ArrayLinkList {
	public static void main(String[] args) {
		List arr_list = new ArrayList();
		List link_list = new LinkedList();
		
		System.out.println("<Linear Insert Object>"); // ArrayList < LinkedList
		System.out.println("ArrayList add1 Time = " + add1(arr_list)); // ArrayList의 순차적 데이터 추가에 대한 시간
		System.out.println("LinkedList add1 Time = " + add1(link_list)); // LinkedList의 순차적 데이터 추가에 대한 시간
		System.out.println();
		
		System.out.println("<Non - Linear Insert Object>"); // LinkedList < ArrayList
		System.out.println("ArrayList add1 Time = " + add2(arr_list)); // ArrayList의 중간에 데이터 추가에 대한 시간
		System.out.println("LinkedList add1 Time = " + add2(link_list)); // LinkedList의 중간에 데이터 추가에 대한 시간
		System.out.println();
		
		System.out.println("<Access Time>"); // ArrayList < LinkedList
		System.out.println("ArrayList add1 Time = " + access(arr_list)); // ArrayList의 임의의 데이터 접근에 대한 시간
		System.out.println("LinkedList add1 Time = " + access(link_list)); // LinkedList의 임의의 데이터 접근에 대한 시간
		System.out.println();
		
		System.out.println("<Linear Delete Object>"); // ArrayList < LinkedList
		System.out.println("ArrayList remove1 Time = " + remove1(arr_list)); // ArrayList의 순차적 데이터 삭제에 대한 시간
		System.out.println("LinkedList remove1 Time = " + remove1(link_list)); // LinkedList의 순차적 데이터 삭제에 대한 시간
		System.out.println();
		
		System.out.println("<Linear Insert Object>"); // ArrayList < LinkedList
		System.out.println("ArrayList add1 Time = " + add1(arr_list)); // ArrayList의 순차적 데이터 추가에 대한 시간
		System.out.println("LinkedList add1 Time = " + add1(link_list)); // LinkedList의 순차적 데이터 추가에 대한 시간
		System.out.println();
		
		System.out.println("<Non - Linear Delete Object>"); // LinkedList < ArrayList
		System.out.println("ArrayList remove2 Time = " + remove2(arr_list)); // ArrayList의 중간에 데이터 삭제에 대한 시간
		System.out.println("LinkedList remove2 Time = " + remove2(link_list)); // LinkedList의 중간에 데이터 삭제에 대한 시간

	}
	
	public static long add1(List list) {
		long startTime = System.currentTimeMillis(); // 시작 시간(현재 시간을 나노초 단위)
		
		for(int i = 0; i < 100000; i++) { // 총 만번의 add(데이터 삽입) 실시 (맨 앞에 데이터 삽입)
			list.add(i);// 순차적 데이터 삽입
		}
		
		long endTime = System.currentTimeMillis() - startTime; // 끝나는 시간
		
		return endTime;
	}
	
	public static long add2(List list) {
		long startTime = System.currentTimeMillis(); // 시작 시간(현재 시간을 나노초 단위)
		
		for(int i = 0; i < 100000; i++) { // 총 만번의 add(데이터 삽입) 실시
			list.add(100, i); // 100번째 원소에 데이터 삽입 (중간에 데이터 삽입)
		}
		
		long endTime = System.currentTimeMillis() - startTime; // 끝나는 시간
		
		return endTime;
	}
	
	public static long remove1(List list) {
		long startTime = System.currentTimeMillis(); // 시작 시간(현재 시간을 나노초 단위)
		
		for(int i = list.size() - 1; i >= 0; i--) { // 순차대로 delete(데이터 삭제) 실시
			list.remove(i); // 순차적으로 데이터 삭제
		}
		
		long endTime = System.currentTimeMillis() - startTime; // 끝나는 시간
		
		return endTime;
	}
	
	public static long remove2(List list) {
		long startTime = System.currentTimeMillis(); // 시작 시간(현재 시간을 나노초 단위)
		
		for(int i = 0; i <= 2000; i++) { // 비순차적 delete(데이터 삭제) 실시
			list.remove(i); // i번째 원소 삭제 (비순차적 데이터 삭제)
		}
		
		long endTime = System.currentTimeMillis() - startTime; // 끝나는 시간
		
		return endTime;
	}
	
	public static long access(List list) {
		long startTime = System.currentTimeMillis(); // 시작 시간(현재 시간을 나노초 단위)
		
		for(int i = 0; i <= 10000; i++) { // 접근 시간 확인
			list.get(i); // 100번째 원소 접근
		}
		
		long endTime = System.currentTimeMillis() - startTime; // 끝나는 시간
		
		return endTime;
	}
}
```
<div align = "center">
<img width="227" alt="다운로드 (3)" src="https://github.com/sooyounghan/JAVA/assets/34672301/dc147ac5-65ca-4e0b-85b2-f616e4d812dc">
</div>
-----
### LinkedList
-----
<div align = "center">
<img width="337" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/ad20e035-b39e-4be5-8faa-31c51cb4f4a9">
</div>

-----
### Doubly LinkedList
-----
<div align = "center">
<img width="330" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/5e487c6e-e0ca-41f1-9ea2-ca819b1bf004">
</div>

-----
### Doubly Circular LinkedList
-----
<div align = "center">
<img width="306" alt="0" src="https://github.com/sooyounghan/JAVA/assets/34672301/dedf395c-7f97-4ad9-a4af-4968186a3ff0">
</div>

-----
### Set Collection
-----
1. 저장 순서가 유지되지 않으며, 중복이 불가능
<div align = "center">
<img width="343" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/ae4585a1-8798-4566-aeb8-7d47edbccaa5">
</div>

2. Hash Set Class
	- Set 인터페이스를 구현한 대표적 컬렉션 클래스
	- 순서를 유지하려면, LinkedHashSet 사용

3. Tree Set Class
	- 범위 검색과 정렬에 유리한 컬렉션 클래스
	- HashSet보다 데이터 추가, 삭제에 대한 시간이 더 많이 걸림

-----
### Enumeration, Iterator, ListIterator
-----
1. Iterator [Collection Inteface - Set, List Interface]
	- 컬렉션에 저장된 데이터를 접근하는데 사용되는 인터페이스
```java
public interface Iterator {
  boolean hasNext();
  Object next();
  void remove();
}
```
2. Iterator Interface
	- Collection Interface 내 추상 메서드로 iterator()로 구현
```java

public interface Collection {
   ...
  public Iterator iterator();
  ...
}
```
3. Iterator Method
	- boolean hasNext() : 다음 요소가 존재하면 true, 존재하지 않으면 false;
	- Object next() : 현재 요소를 가져옴. 반환 타입 Object

<div align = "center">
<img width="345" alt="다운로드 (4)" src="https://github.com/sooyounghan/JAVA/assets/34672301/f109e67f-a4fe-491d-b901-e82f5c0e47db">
</div>

4. Set Collection (HashSet / TreeSet) 데이터 추출 - Iterator 
	- Iterator 인터페이스 존재 / Collection Interface 내 iterator() 존재 : Collection 클래스에서 사용 가능
	- iterator()를 사용 : 반환 타입으로 Iterator 객체 반환

		  (인터페이스 참조타입 Iterator 으로 이를 구현되어 생성한 객체 Iterator 객체를 가리킴)
		  이후, hasNext()를 통해 Set에 존재하는 요소 확인 후, 존재하면 받아오는 next() 또는 remove() 사용

```java
import java.util.*; // Set Package Import

/*
 * Hash Set
 */
public class Set_Ex {
	public static void main(String[] args) {
		/*
		 * 정수 데이터 5개를 저장하는 HashSet
		 */
		Set hashSet = new HashSet(); // 다형성
		// Set treeSet = new TreeSet(); // TreeSet 또한 Set 구현 클래스이므로 다형성을 구현하여 코드의 유연성 증가
		System.out.println("HashSet = " + hashSet); // []
		
		/*
		 * hashSet의 갯수 출력 : int size()
		 */
		System.out.println("HashSet size() = " + hashSet.size()); // 0
		
		/*
		 * 데이터 추가 : boolean add(Object o)
		 *   - 매개변수는 Object 객체이므로 모든 객체에 대해 수용 가능 (다양한 데이터 타입 가능)
		 *   - Object o의 삽입이 되었으면 true, 되지 않았으면 false
		 */
		System.out.println("<HashSet add(Object e)>");
		for(int i = 0; i < 5; i++) { // 5개의 원소 추가
			hashSet.add((int)(Math.random() * 45) + 1);  // 1 ~ 45 까지의 난수 중 무작위 5개 삽입 (중복 제외)
		}
		System.out.println("HashSet Size() = " + hashSet.size()); // 5
		System.out.println("HashSet = " + hashSet); // 1 ~ 5까지 무작위 난수 5개 저장(중복 제외) 
		
		/*
		 * Set Collection (HashSet) 데이터 추출 - Iterator
		 *   - Iterator 인터페이스 iterator() 메서드 존재 -> 이를 구현한 HashSet, TreeSet에 구현
		 *   - iterator()를 사용하면 반환 타입으로 Iterator 객체 반환
		 *   - 이후, hasNext()를 통해 Set에 존재하는 요소 확인 후, 존재하면 받아오는 next() 또는 remove() 사용
		 */
		
		Iterator it = hashSet.iterator();
		System.out.print("HashSet = [ ");
		while(it.hasNext()) {
			/*
			 * boolean hasNext() : 다음 요소가 존재하면 true, 존재하지 않으면 false;
			 * Object next() : 현재 요소를 가져옴. 반환 타입 Object
			 */
			Object obj = it.next();
			System.out.print(obj + " ");
		}
		
		System.out.println("]");
		
		/*
		 * 데이터 삭제 (boolean remove(Object o)) : 매개변수 Object o 객체에 대해 있으면, 삭제 후 true / 아니면 false
		 */
		System.out.println("<HashSet remove(int index)>");
		for(int i = 1; i <= 5; i++) {  // 1 ~ 45까지의 난수 중 무작위 수에 대해 삭제 (일치하는 수가 있다면)
			System.out.print(i + " = " + (hashSet.remove((int)(Math.random() * 45) + 1) + " "));
		}
		System.out.println();
		System.out.println("HashSet = " + hashSet); 
		
		/*
		 * HashSet 데이터 모두 삭제, 즉 모두 완전히 비움 (void clear())
		 * HashSet 내 비어있는지 확인 (boolean isEmpty()) : 비어있다면 true, 비어있지 않다면 false
		 */
		hashSet.clear();
		System.out.println("HashSet = " + hashSet); 
		System.out.println("HashSet Empty = " + hashSet.isEmpty());
	}
}
```

5. Enumeration : Iterator의 구버전
<div align = "center">
<img width="342" alt="다운로드 (5)" src="https://github.com/sooyounghan/JAVA/assets/34672301/c2553446-f5e2-48cf-bdd5-9f77b6798e53">
</div>

7. ListIterator : Iterator의 접근성을 향상 (단방향에서 양방향으로 변화) [List]
<div align = "center">
<img width="325" alt="다운로드 (6)" src="https://github.com/sooyounghan/JAVA/assets/34672301/17ab85fe-0caf-4ac1-8437-dd228639772c">
</div>

       * listIterator( ) : 인덱스를 부여하지 않고, listiterator 객체를 생성
       * listIterator(int index) : 지정된 인덱스부터 listiterator 객체 생성

```java
import java.util.*;

/*
 * Iterator / ListIterator / Enumeration
 *  - 컬렉션에 저장된 데이터를 접근하는데 사용되는 인터페이스
 *  
 *  1. Enumeration : boolean hasNextElement(), Object nextElement()
 *  2. Iterator : boolean hasNext(), Object next() [List, Set]
 *  3. ListIterator : boolean hasNext/Previous(), Object next/previous()... [List]
 */
public class Iterator_Ex {
	public static void main(String[] args) {
		List arr_list = new ArrayList(); 
		
		for(int i = 0; i < 5; i++) {
			arr_list.add(i + " "); // 문자열 "1" ~ "5"까지 삽입
		}
		
		/*
		 * ListIterator
		 */
		ListIterator it = arr_list.listIterator(); // ListIterator 객체 생성
		
		System.out.println("ListIterator Next()");
		System.out.print("arr_list = [ ");
		while(it.hasNext()) { 
			/*
			 * boolean hasNext() : 다음 요소가 존재하는지 확인
			 * Object next() : 현재 요소를 반환 (반환타입 Object)
			 */
			String obj = (String)it.next(); // 추출(형변환)
			System.out.print(obj + " ");
		}
		System.out.println("]");

		System.out.println("ListIterator Previous()");
		System.out.print("arr_list = [ ");
		while(it.hasPrevious()) { // 현재 요소의 인덱스를 기준으로 이전 요소가 있다면
			/*
			 * boolean hasPrevious() : 이전 요소가 존재하는지 확인
			 * Object previous() : 이전 요소를 반환 (반환타입 Object)
			 */
			String obj = (String)it.previous(); // 추출(형변환)
			System.out.print(obj + " ");
		}
		System.out.println("]");
		
		/*
		 * Iterator
		 */
		Iterator arr_it = arr_list.iterator();

		System.out.println("Iterator next()");
		System.out.print("arr_list = [ ");
		while(arr_it.hasNext()) {
			String obj = (String)arr_it.next();
			System.out.print(obj + " ");
		}
		System.out.println("]");
	}
}
```
-----
### Map Collection
-----
1. 키(Key)와 값(Value)으로 구성된 Map.Entry 객체를 저장하는 구조
2. 키와 값은 모두 객체
3. 키는 중복될 수 없지만, 값은 중복 가능

<div align = "center">
<img width="341" alt="다운로드 (7)" src="https://github.com/sooyounghan/JAVA/assets/34672301/3be923f5-6a48-40c6-a6c4-a080f851a07c">
</div>

	Value는 중복을 허용하므로, 다른 키에 대해서 동일한 value면 그 해시코드 값은 같음 (즉, 같은 객체를 가리킴)

4. 구현 클래스 : HashMap, TreeMap, HashTable, Properties  
5. 주요 메서드
<div align = "center">
<img width="459" alt="다운로드 (8)" src="https://github.com/sooyounghan/JAVA/assets/34672301/cf18f37f-8108-493d-997d-4f7ea02a0396">
</div>

-----
### HashMap
-----
<div align = "center">
<img width="414" alt="다운로드 (9)" src="https://github.com/sooyounghan/JAVA/assets/34672301/e0ee6348-24f2-459f-818e-972bbf0c25ff">
</div>

1. 키 객체는 hashCode()와 equals()를 재정의해 동등 객체가 될 조건을 정해야함
2. 해싱을 구현한 HashMap, HashSet, Properties, HashTable과 같이 해싱
   기법으로 구현한 컬렉션 클래스에서는 Object클래스에서 정의된 hashCode()를
   해시함수로 사용
3. Object클래스에 정의된 hashCode()는 객체의 주소를 이용하는 알고리즘으로
   해시코드를 만들기 때문에, 모든 객체에 대해 호출한 결과로 이용

   	   * String Class의 Object로부터 상속받은 hashCode()는 오버라이딩해서
             문자열의 내용으로 해시코드 반환

5. 따라서, 서로 다른 String인스턴스일지라도 같은 내용의 문자열을 가졌다면 같은 해시코드를 내놓음

6. 서로 다른 객체에 대해 equals()로 비교한 결과가 true인 동시에, hashCode()의 반환값이 같아야
   같은 객체로 인식

        * 그러므로 새로운 클래스를 정의할 때, equals()을 해야한다면, hashCode()도
   	   오버라이딩해야 equals()도 같이 재정의해서 equals()의 결과가 true인 동시에 두 객체의
           hashCode()의 결과가 동일하도록 해줘야함

 8. 컬렉션 클래스에서는 equals()의 호출 결과가 true이지만 해시코드가 다른 두 객체를 서로 다른
    것으로 인식하고 따로 저장
    
<div align = "center">
<img width="376" alt="다운로드 (10)" src="https://github.com/sooyounghan/JAVA/assets/34672301/9aa4b024-40ac-468d-a589-1c6a8fc2764d">
</div>

9. 키 타입은 String을 많이 사용

       (String은 문자열이 같을 경우 동등 객체가 될 수 있도록 hashCode()와 equals() 메서드가
        재정의 되어있음)

10. 동일한 키 값에 대해 다른 값을 입력하면, 기존 값은 삭제되고, 현재 값으로 갱신
11. 주요 메서드
<div align = "center">
<img width="377" alt="다운로드 (11)" src="https://github.com/sooyounghan/JAVA/assets/34672301/76b9be0c-2374-4ed7-9960-f5b882df4d21">
</div>

```java
import java.util.*; // Map Interface Import

public class Map_Ex {
	public static void main(String[] args) {
		Map<Object, Object> hashMap = new HashMap<Object, Object>(); // Generics 사용 (Key, Value : Object)
		//Map treeMap = new TreeMap();
		//Map prop = new Properties();
		System.out.println("hashMap = " + hashMap);
		
		/*
		 * 저장된 키와 값의 쌍의 수 확인
		 */
		System.out.println("hashMap size = " + hashMap.size()); // 0
		
		/*
		 * K, V 추가 : Object put(Object key, Object Value)
		 */
		hashMap.put(1, 100); // 객체이므로 Auto-boxing
		hashMap.put(2.0, 100); // Key 1과 2.0에 동일한 value 100 입력(중복) 
		hashMap.put(true, "AB");
		hashMap.put('A', 'Z');
		System.out.println("Key 'A' = " + hashMap.get('A'));
		hashMap.put('A', "C"); // 동일한 키 값에 대해 다른 값을 입력했으므로, 기존 값은 삭제되고, 현재 값으로 갱신
		System.out.println("Key 'A' = " + hashMap.get('A'));
		
		/*
		 * K를 이용해 V를 가져오기 : Object get(Object key)
		 */
		System.out.println("Key 1 = " + hashMap.get(1));
		System.out.println("Key 1's Value Hashcode = " + hashMap.get(1).hashCode()); 
		
		System.out.println("Key 2.0 = " + hashMap.get(2.0));
		System.out.println("Key 2.0's Value Hashcode = " + hashMap.get(2.0).hashCode()); // Value는 중복을 허용하므로, 다른 키에 대해서 동일한 value면 그 해시코드 값은 같음
		
		System.out.println("hashMap size = " + hashMap.size()); // 4

		/*
		 * 키를 통해 값 제거 : Object remove(Object key, [Object value]);
		 *  - 키 또는 요소를 포함하고 있는지 확인
		 *    1. boolean containsKey(Object key) : HashMap에 지정된 키(Key)를 포함하고 있는지 확인 (있으면 true, 없으면 false)
		 *    2. boolean containsValue(Object value) : HashMap에 지정된 요소(value)를 포함하고 있는지 확인 (있으면 true, 없으면 false)
		 */
		if(hashMap.containsKey(2.0)) { // 키 2.0을 가지고 있다면,
			System.out.println("HashMap Key 2.0's value remove = " + hashMap.remove(2.0)); // 키 2.0의 요소 삭제
		}
		else {
			System.out.println("Not Key 2.0");
		}
		
		System.out.println(hashMap.remove('A')); // 문자 A키를 가지고 있으면, 그 맞는 값을 제거
		System.out.println(hashMap.remove('C')); // C는 현재 키에 존재하지 않으므로, null 반환
		
		System.out.println("hashMap size = " + hashMap.size()); //  2
		
		/*
		 * Set keySet() : HashMap에 저장된 모든 키가 저장된 set 반환
		 */
		Set<Object> keySet = hashMap.keySet(); // Generics에 의해 Object
		Iterator<Object> it = keySet.iterator(); // Generics에 의해 Object
		
		System.out.print("Hash Map [ Key : Value ] = [ ");
		while(it.hasNext()) {
			Object key = it.next();
			System.out.print(key + " : ");
			System.out.print(hashMap.get(key) + " ");
		}
		System.out.println("]");
		
		hashMap.clear();
		if(hashMap.isEmpty()) {
			System.out.println("hashMap size = " + hashMap.size()); // 0
		}
	}
}
```

-----
### KeySet, EntySet
-----
1. Set keySet() : HashMap에 저장된 모든 키가 저장된 set 반환 ← Iterator 활용
```java
		Set<Object> keySet = hashMap.keySet(); // Generics에 의해 Object
		Iterator<Object> it = keySet.iterator(); // Generics에 의해 Object
		
		System.out.print("Hash Map [ Key : Value ] = [ ");
		while(it.hasNext()) {
			Object key = it.next();
			System.out.print(key + " : ");
			System.out.print(hashMap.get(key) + " ");
		}
		System.out.println("]");
```

2. Set entrySet() : HashMap에 저장된 키와 값을 Entry 형식(키와 값의 쌍)의 형태의 Set으로 가져옴

	- entrySet()의 반환타입 : Map.Entry<K, V>의 형태
	- 따라서 Set은 Set<Map.Entry<K, V>> 형태가 되어야함
	- 반복자는 단순히 그 요소를 받아올 것이므로, Iterator 또한 <Entry<K, V>>
	- 반복자에 의해 받게 된다면, 그 역시 타입은 Map.Entry<K, V>
	- Map.Entry<K, V> 에서 키에 접근 : K getKey() / 요소에 접근 : V getValue()

```java
		// enteySet() -> Map.Entry 형태이므로 Entry 형태의 Set으로 전환되므로 Set의 Generics는 <Entry<Object, Object>
        Set<Entry<Object, Object>> entrySet = hashMap.entrySet(); // Map -> Entry
        
        // Set -> Iterator를 전환 -> 반복자이므로 어차피 형태는 동일 (Entry<Object, Object>)
		Iterator<Entry<Object, Object>> entry_iter = entrySet.iterator(); // Entry -> (Key, Value)
		
		System.out.print("Entry Set = [ ");
		while(entry_iter.hasNext()) {
            // 요소의 값은 Map.Entry<Object, Object> 형태
			Map.Entry<Object, Object> entry = entry_iter.next();
            
            // Map.Entry 키에 접근 : Object getKey()
            // Map.Entry 요소에 접근 : Object getValue()
			System.out.print("Key : " + entry.getKey() + " / " + "value : " + entry.getValue() + ", ");
		}
		System.out.println(" ]");
```

-----
### HashTable
-----
```java
import java.util.*;

/*
 * HashTable - Map Collection
 */
public class HashTable_Ex {
	public static void main(String[] args) {
		Hashtable<String, String> hashtable = new Hashtable<>();
		
		/*
		 * HashTable에 값 입력
		 */
		hashtable.put("001", "abc");
		hashtable.put("002", "bcd");
		hashtable.put("003", "cde");
		hashtable.put("004", "efg");
		hashtable.put("005", "hij");;
		hashtable.put("001", "jkm");;
	
		/*
		 * Stream을 이용한 출력
		 */
		hashtable.entrySet().stream().forEach((e) -> System.out.println(e.getKey() + " : " +e.getValue())); // Stream을 이용한 Console 출력
		System.out.println();
		
		/*
		 * KeySet을 이용한 Iterator로 요소 추출
		 */
		Set<String> keySet = hashtable.keySet(); // keySet 이용
		Iterator<String> iter = keySet.iterator();
		
		while(iter.hasNext()) {
			String key = iter.next();
			System.out.println(key + " : " + hashtable.get(key)); // KeySet을 이용한 key, value 출력
		}
		System.out.println();
		
		/*
		 * Collection을 이용한 hashtable의 요소 추출
		 */
		Collection<String> c = hashtable.values(); // values() 이용
		System.out.println(c); // value 출력
		System.out.println();
		
		/*
		 * entrySet을 이용한 key, value 값 추출
		 */
		Set<Map.Entry<String, String>> entrySet = hashtable.entrySet();
		Iterator<Map.Entry<String, String>> it = entrySet.iterator();
		while(it.hasNext()) {
			Map.Entry<String, String> e = (Map.Entry<String, String>)it.next();
			System.out.println(e.getKey() + " : " + e.getValue()); // 키와 값 출력
		}
	}
}
```

-----
### Generics
-----
1. 컴파일 단계에서 잘못된 타입을 사용할 수 있는 문제를 제거할 수 있도록 도와주는 기능
2. 컬렉션, 람다식(함수적 인터페이스), 스트림 등에서 널리 사용
3. 타입을 파라미터로 가지는 클래스와 인터페이스
4. 선언 시 클래스 또는 인터페이스 이름 뒤에 <> 부호를 붙임 (<> 사이에는 타입 파라미터 위치)

	   * 타입 파라미터 : 일반적으로 대문자 알파벳 한 문자로 표현

5. 타입을 사용하지 않은 경우 : 자동적으로 Object 타입 사용 (빈번한 타입 변환 발생 → 프로그램 성능 저하)
<div align = "center">
<img width="332" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/d89d022e-0fbe-4f2f-8545-5cd1ce4d0245">
</div>

6. 제네릭 타입은 두 개 이상의 타입 파라미터 사용 가능 (각 타입 파라미터는 콤마로 구분)
	    * 자바 7 이후부터는 다음과 같이 가능
<div align = "center">
<img width="306" alt="제목 없음" src="https://github.com/sooyounghan/JAVA/assets/34672301/2494983c-9fef-41d6-aeec-ab82476938ae">
</div>
   

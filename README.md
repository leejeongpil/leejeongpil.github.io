# test

# Java

# VSCode를 이용한 자바 환경 세팅, mac ver

1.  VSCode 다운로드 및 실행
2.  ⇧⌘X 눌러 Extensions(좌측 네모 블럭 클릭해도 좋음) 에서 java extension pack(extension identifier: vscjava.vscode-java-pack) 검색 및 install(하단 6개도 자동 install 됨)
3.  jdk 다운로드
    (3.1: 2번 완료시 vscode 내부 화면 좌측에서 8 또는 11 jdk 다운 받으라고 뜸, LTS인 11 다운 권장함, 실제로 vscode 상에서 11을 최소 요구조건으로 함. 그거 다운 받고 실행하고 next 누르다 보면 /Library/Java/JavaVirtualMachines/adoptopenjdk-11.jdk 이렇게 설치됨.)
    =================
    (3.2: 만약 이 화면이 안보인다면 ⇧⌘P 를 눌러서 Java: Configure Java Runtime 입력후 3.1과정 다시 하거나
    직접 jdk를 다운 받으면 됨 [https://jdk.java.net/archive/](https://jdk.java.net/archive/), 다운 받고 압축 풀었으면 /Library/Java/JavaVirtualMachines/의 JavaVirtualMachines 폴더 내에 압축 푼걸 옮겨준다.)

        ![Java%20c4ec48144e534b329ebd3b7f8ab848ba/Untitled.png](Java%20c4ec48144e534b329ebd3b7f8ab848ba/Untitled.png)

4.  3번 완료시 terminal 키고 java —version와 javac —version을 입력하여 버전이 뜨면 올바르게 설치 된 것.
5.  이후 java 프로젝트를 vscode에서 실행해본다.
    5.1. ⇧⌘P 를 누르고 java: create java project... 클릭
    5.2. no build tools 클릭
    5.3. workspace 설정 후 프로젝트 만들면 됨
6.  5번 과정에서 오류시 또는 4번 과정에서 버전이 확인이 안될시 vscode 내에서 ⌘, 누르고 java: home 입력 후 Edit in settings.json 클릭 후 "java.home": ""에서 ""안에 jdk 깔린 위치 입력, 3.2 수행시 /Library/Java/JavaVirtualMachines/압축푼jdk폴더 를 입력하면 된다. 다시 4, 5 반복

차를 만드는 틀(type)→class Car, 차 만들기→class CarTest의 main에서 new 차로 객체(인스턴스) 생성, 차 테스트하기→class Car 내의 method를 class CarTest의 main에서 생성한 객체를 통해 접근.

- java eclipse, sts 단축키 사용 팁

  1. sts or eclipse 사용시 Window→Preferences→encoding 검색 → UTF-8 로 바꾸기
  2. sts(eclipse).ini 마지막 줄에 -Dfile.encoding=UTF-8 로 설정

  두 가지 중 하나로 설정

  ```
  ctrl + space + enter : 자동완성
  ctrl + f11 : 프로젝트 실행
  ctrl + shift + f : 자동 들여쓰기
  ctrl + shift + c , ctrl + / : 주석
  ctrl + d : 커서가 있는 라인 지우기
  ctrl + z : 뒤로가기
  ctrl + y : 앞으로가기
  alt + up, down : 라인 자리 바꾸기
  alt + shift + a : 멀티 커서
  ctrl + s : 현재 페이지 저장
  ctrl + shift + s : 전체 저장
  ctrl + f : 찾기 이걸로 찾고 한꺼번에 바꾸기(case sensitive : 대소문자 구분, selected lines : 영역 선택 가능)
  ctrl + alt + up, down : 커서가 있는 라인 방향키에 따라 복사
  ```

- 알고리즘 사용시 팁 되는 메서드 모음

  ```jsx
  int max=Integer.MIN_VALUE;
  int min=Integer.MAX_VALUE;

  for (int i : intArray) {
  	min=Math.min(min, i);
  	max=Math.max(max, i);
  }
  //=====================
  int[] scores3 = Arrays.copyOf(scores, 4);

  int[] scores2 = new int[4];
  System.arraycopy(scores, 0, scores2, 0, scores.length);
  //(복사할소스,소스의출발인덱스,복사할곳,복사할곳의출발인덱스,소스를얼만큼의길이복사?)
  //=====================

  System.out.println(Arrays.toString(names));//1차배열 내용까지 확인 가능
  System.out.println(Arrays.deepToString(names));//2차배열 내용까지 확인 가능
  //출력 값 간편 확인

  BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

  int cnt = Integer.parseInt(br.readLine());
  String input = br.readLine();

  int[] arr1=new int[cnt];
  StringTokenizer st = new StringTokenizer(input);
  for (int i = 0; i < arr1.length; i++) {
  	arr1[i]=Integer.parseInt(st.nextToken());
  }
  System.out.println(Arrays.toString(arr1));
  //버퍼이용한 글자 입력
  ```

- 변수선언

  ```java
  int[] numList;
  numList = new int[5];

  numList[0] = 1;
  .
  .
  .

  String[] strList = {"abc","def","ghi"};
  String[][] strList2 = new String[4][5];
  for(int i=0; i<strList2.length; i++){
  	for(int j=0; j<strList2[i].length; j++){
  		System.out.print("["+i+"]"+"["+j+"]"+"\t");
  	}
  	System.out.println("");
  }

  String[][] strList3 = new String[4][];
  strList3[0]=new String[1]
  strList3[1]=new String[2]
  strList3[2]=new String[3]
  strList3[3]=new String[4]
  for(int i=0; i<strList3.length; i++){
  	for(int j=0; j<strList3[i].length; j++){
  		System.out.print("["+i+"]"+"["+j+"]"+"\t");
  	}
  	System.out.println("");
  }
  ```

- 논리 연산자

  &, |는 양변을 계산해서 논리를 결정하지만

  &&, ||는 앞에만 보고 결정할 수 있는 경우 뒤에를 계산 안한다. 따라서 뒤에 있는 계산식은 입력 안된다.

- 배열

  ```jsx
  //배열 선언
  int intArray[] = {1,2,3,4,5};
  int[] intArray2 = {5,4,3,2,1};
  String[] string1 = new String[]{"a","b","c"};
  String[] string1;
  string1 = new String[]{"a","b","c"};

  String org = "LOVE";
  char[] chars = new char[org.length()];
  for (int i = 0; i < chars.length; i++) {
  	chars[i] = org.charAt(i);
  }

  //배열의 출력 방법

  String[] names = {"철수", "영희", "민수", "민희"};
  for (int i = 0; i < names.length; i++) {
  	System.out.println(i + "번 인덱스: " + names[i]);
  }

  for (String string : names) {
  	System.out.println(string);
  }

  System.out.println(Arrays.toString(names));//값 확인

  //배열의 값 변경 및 추가
  int[] scores = { 10, 20, 30 };

  int[] scores2 = new int[4];
  System.arraycopy(scores, 0, scores2, 0, scores.length);
  //(복사할소스,소스의출발인덱스,복사할곳,복사할곳의출발인덱스,소스를얼만큼의길이복사?)
  scores2[3] = 40;

  int[] scores3 = Arrays.copyOf(scores, 4);

  scores = Arrays.copyOf(scores, 4);

  //2차 배열
  int[][] intArray;
  intArray = new int[2][3];
  int[][] intArray = new int[][]{{1,2,3},{4,5,6}};
  int[][] intArray = {{1,2,3},{4,5,6}};

  int[][] intArray = new int[3][];
  intArray[0] = new int[1];
  intArray[1] = new int[5];
  intArray[2] = new int[]{1,2,3,4,5,6,7};
  intArray[3] = new int[4];
  ```

- if, for, while, do while

  ```java
  if(expression){
  	statement1;
  } else if(expression2){
  	statement2;
  } else {
  	statement3;
  }

  for(int i=0; i<array.length; i++){

  }

  for(type value:items){
  	System.out.println(value);
  }
  ```

- java 의 객체지향1

  클래스로 객체를 정의하고 다른 클래스의 메인에서 정의한 객체를 불러화 메모리에 올려 인스턴스를 생성한다.

  차를 만드는 틀(type)→class Car, 차 만들기→class CarTest의 main에서 new 차로 객체(인스턴스) 생성, 차 테스트하기→class Car 내의 method를 class CarTest의 main에서 생성한 객체를 통해 접근.

  상속(inheritance): 속성과 메서드가 다른 하지만 유사한 객체가 필요할 경우에는 이미 생성한 객체를 이용해서 새로운 객체를 생성할 수 있다. 즉 변수나 메서드가 추가 되는 경우 상속을 사용하는 것이다. 버스라는 범위 안에 관광버스, 마을버스, 시내버스 나뉠때 버스를 상속받아 필요한 메서드나 변수를 추가하는거. extends, java 는 multiple inheritance를 지원하지 않는다.(여러명한테 상속받는 경우)

  다형성(polymorphism): 하나의 interface를 이용해서 다른 구현을 해서 제공한다. 하나의 리모컨으로 여러 티비를 조작하는 경우. overloading(한 클래스 안에 이름이 같은 메서드를 여러개 정의한다. 하지만 타입(유형)이나 인자의 개수는 다르게 정의한다.), overriding(상속 관계를 가지고 있는 하위 클래스가 상위 클래스가 가지고 있는 메서드를 재정의하는 것이다. 이 때 재정의된 메서드가 선언된 형태는 상위클래스에서 선언된 것과 같다.)

  추상화(abstraction): 다양한 객체들의 공통된 특성을 모아 일반화 함으로써 클래스를 정의할 때 중요한 역할을 한다. 클래스 내부의 속성과 기능을 멤버라고 한다.

  캡슐화(encapsulation): 변수와 메서드를 하나로 묶어 독립적으로 동작하지 않도록 하고 하나의 추상화된 클래스로 묶는 과정을 의미한다. 즉 데이터와 메서드가 묶여있기에 따로 분리할 수 없으며, 데이터가 어떻게 처리되는지 알필요가 없다.

  정보은닉(information hiding): 객체지향 언어이기에 캡슐화된 변수나 메서드를 선택적으로 공개하거나 숨길 수 있게 한다. private(접근 불가), public(접근 가능)

  메시지(message): 객체 간에 서로 통신하는 방법으로 객체간에는 메시지를 주고 받기 때문에 동일한 프로세스를 가질 필요 없다. 또한 메시지를 주고 받을 때 객체가 존재하는 위치는 제약이 되지 않는다.

- java 의 객체지향2

  클래스: 객체 생성시 "객체를 구성" 또는 "객체에 포함" 되는 내용들이 작성되어있는 설계도

  객체: 특정 클래스의 설계 내용에 따라 메모리를 할당 받은 독립적인 객체(인스턴스)

  필드: 상태변수, 멤버변수, 인스턴스 변수. new로 인해 객체가 생성될 때 객체 내부에 생성되고 객체가 존재하는 동안 유지된다. new 로 객체생성할 때 heap에 올라간다.

  메소드: 클래스 내부의 함수. 예) void Name(){}

  기초자료형 변수: int, double, char, boolean ... 값 자체를 변수에 담는 애들.

  참조자료형 변수: 값은 객체에 유지되고 객체의 주소를 저장하는 변수.

  ```java
  package test;

  public class TestStudent {
      public static void main(String[] args) {
          Student st1 = new Student();//참조형 변수
          st1.age = 25;
          st1.name = "철수";
          st1.Study();
          st1.EatDduckkook();
      }
  }

  //==================================

  package test;

  public class Student {
      String name;//멤버변수(전역변수), 초기값이 선언됨
      int age;
  //==================== 필드: 클래스내에 메소드 제외한 부분
      void Study() {//메소드, ()안에 인자(매개변수)도 지역변수이다.
          System.out.println("열심히 공부한다.");
          System.out.println(age);
          System.out.println(name);
      }

      void EatDduckkook() {
          int age_DD = age;//지역변수, 초기값이 할당되지 않으므로 대입연산을 꼭 수행해야 사용 가능하다.
  				age_DD += 1;
          System.out.println(age);
      }
      void PrintInfo(){

      }
  }
  ```

  캡슐화: 객체내에 멤버변수(전역 변수)에 private을 붙여 불투명한 껍질 안에 숨겨 놓는 것. 이에 따라 이상한 값이 들어가지 않도록 한번 검사를 할 수 있고 getter, setter로 접근이 가능하다.

  public: 그냥 접근 가능, 모든 접근 가능, package, Class가 동일하지 않아도 모든 접근이 가능

  protected: 같은 패키지(폴더) 안에 클래스면 접근가능 아니면 상속받아야함, 같은 package에서만 접근을 허용하고 다른 package에서 접근하려면 해당 Class를 상속받을 시에만 접근이 가능

  default or package: 기본, 동일 package에서만 접근을 허용하는 제한자로, 접근 제한자가 생략되어 있을경우엔 기본적으로 default 접근 제한자가 적용

  private: 다른 클래스에서 getter, setter로 접근, 클래스내에서는 걍 접근 가능, 동일 package, 다른 package 모두 접근이 불가능하고 같은 Class 내에서만 접근을 허용 따라서 getter setter

  overloading: constructor의 여러버전을 만들고 싶을 때 이름은 같고 내부에 들어가는 인자(매개변수)만 다르게 작성해서 사용한다. 즉 하나의 클래스 안에서 같은 이름의 메소드를 2개 이상 만들고 싶을 때 사용한다.

  overriding: 조상 클래스에 정의된 메서드를 자식 클래스에서 적합하게 수정하는 것. 조건: 메서드 이름 같다, 매개변수의 개수, 타입, 순서가 같다, 리턴 타입 같다, 접근 제한자는 부모 보다 범위가 넓거나 같아야 한다, 조상보다 더 큰 예외를 던질 수 없다. 추가적재이다!

  this 참조변수: 모든 객체가 각각 가지고 있는 참조변수 이며 자기 자시의 주소값이 저장된 변수이다. 예를 들어 this.age이면 자기자신의 age를 뜻함, 지역변수와 멤버변수 이름 동일할 때 구분하는 용도, 생성자가 다른 생성자를 호출하는 경우에 쓰인다. 상속일때 부모 멤버랑 자기 멤버 구분할 때 쓴다.

  static: 특정 인스턴스(객체)에 소속되지 않고, 인스턴스(객체)가 없어도 존재하는 멤버이다. 여러번 생성되지 않고 하나만 존재한다. static → instance(non-static) 접근 불가, instance(non-static) → static 접근 가능.

- java 의 객체지향3

  상속 inheritance: 기존 클래스의 구성요소(멤버: 멤버 변수, 멤버 함수)을 자식 클래스에서 재사용 하는 것. 단, 부모의 생성자와 초기화 블록은 상속하지 않음. 부모의 코드를 바꾸면 상속받은 자식들에게도 적용되기에 유지보수 성이 향상한다.
  자식클래스의 생성자는 반.드.시 자기가 하고자 하는 작업 이전에 부모 생성자를 호출해야만 한다. super()로

  상속 관계를 is a 관계라고 한다. ex) fireman is person

  자바는 단일 상속만 지원한다. 이를 interface 와 포함 관계(has a) 관계로 극복한다.

  super를 통해 조상 클래스의 멤버에 접근한다. this를 통해 멤버에 접근하는 것과 유사하다. super.value, this.value

  super()는 자식 클래스 생성자의 맨 첫 줄에서만 호출 가능, 즉 생성자는 첫 줄에만 this() or super()가 올 수 있다.

  super는 자식이 부모의 성분 쓸 때랑 자식이 부모 생성자 가져올때

  Polymorphism: 하나의 객체가 다양한 타입을 가질 수 있는 것, 상속관계에 있을 때 자식인 객체는 자식의 조상들의 다양한 타입을 가질 수 있다. ex) person→hero→batman 의 상속 구조일 때 batman 객체 bruceWayne 은 hero 이기도 person 이기도 하기 때문에 batman, hero, person 의 타입을 가질 수 있고 이를 polymorphism 이라고 한다. 단 사용시 접근할 수 있는 내용의 차이가 있다. person 인 bruceWayne 은 단지 사업가 이고 hero 인 bruceWayne 은 능력자일 뿐이고 batman 인 bruceWayne 이 우리가 아는 베트맨이기에 각 타입에 따라 참조할 수 있는 접근할 수 있는 범위가 다른 것이다.
  참조형 변수 또한 형변환이 가능하며 person 인 bruceWayne 을 강제로 hero 형변환 해서 전직 시켜도 hero 의 스킬을 쓸 수 없다. 이에 따라 hero bruceWayne 인지 알기 위해 instanceof 를 통해 이프문으로 비교해 알 수 있다.

  부모의 변수를 자식의 객체로 설정할 수 있다.

- java 의 객체지향3

  abstract: 자식들이 부모를 상속받아 클래스를 만들때 부모 클래스의 메소드가 아예 안쓰이는 경우가 있다. 즉 기능적으로 자손 클래스에서 반드시 재정의해서 사용되기에 조상의 구현이 무의미한 메서드가 되는 것이다. 이때 추상화 클래스를 이용할 수 있다. abstract mehtod design pattern 이다.
  상속 전용 클래스이며 클래스에 구현부가 없는 메서드가 있기에 객체를 생성할 수 없다. abstract mehtod는 재정의해서 사용하라는 뜻이기에 실제 사용할 수 가 없다 override 하지 않는이상! 하지만, 상위 클래스 타입으로 자식을 참조할 수는 있다(뜻: 다형성에서 부모의 타입으로 자식을 new로 불러 오면서 참조는 가능하다는 뜻이다.)
  또한 클래스 내부에 abstract 가 있으므로 class 또한 abstract로 해야한다.
  그렇다면 이를 왜 사용할까? 바로 자손이 사용하고자 하는 메서드의 구현의 강제를 통해 프로그램의 안정성을 향상 시킨다는 것이다.

  interface: 최고수준의 추상화 단계, 모든 메서드가 abstract 형태이다.
  클래스와 유사하게 interface 선언을 하며 모든 멤버변수는 public static final 이고 생략 가능하다. 또한 모든 메서드는 public abstract 이고 생략 가능하다.
  특징- 클래스와 마찬가지로 extends 를 이용해 상속이 가능하며 "다중 상속"이 가능하다!!
  그렇다면 어떻게 인터페이스를 클래스에서 활용할까? 바로 implements 를 통해 interface 의 세부 내용을 구현한다.
  다형성은 조상 클래스 뿐 아니라 조상 인터페이스에도 적용된다는 것! 인터페이스로도 객체를 참조할 수 있다!!!
  모든 메서드가 abstract인 interface를 사용하게 되면 구현의 강제를 부여하여 표준화처리를 할 수 있고 이렇게 되면 손쉬운 모듈 교체를 지원하게 되는 것이다.
  클래스는 단일 상속만 가능하다 이에 따라 인터페이스의 다중 상속은 다형성을 확장 시킬 수 있다. 즉 관계를 맺어주어 다형성을 확장할 때 인터페이스는 다중 상속이 가능하기에 다형성을 확장 시킬 수 있는 것이다.
  interface default method: 인터페이스에 선언 된 구현부가 있는 일반 메서드
  메서드 선언부에 default modifier 를 추가하여 메서드 구현부를 작성하면 된다. 단 접근 제한자는 public만 가능하다. 결국 기존 interface 에 추가해야할 기능이 생겼을 때 추가한다면 interface 를 implements 하는 클래스들은 모두 override를 필수로 해야한다(abstract로 하게 되면 상속하는 애들은 무조건 재정의를 강제하므로) 따라서 이를 해결하기 위해 나온게 interface default method 이다.

  static method 또한 활용 가능하며 static 이 붙으면 클래스에 대한 구현체 없이 이름으로 바로 쓸 수 있다.

  generics: 다양한 타입의 객체를 다루는 메서드, 컬렉션 클래스에서 **컴파일 시에 타입 체크(기존은 타입을 컴파일 시에는 모르니 런타임 시에 코드 적으로 확인하게 했어야함)**. 미리 사용할 타입을 명시해서 형 변환을 하지 않아도 된다. 객체의 타입에 대한 안전성 향상 및 형 변환의 번거로움이 감소한다. 클래스가 어떤 타입인지 선언해서 그 클래스를 참조할 때 추가적인 형 변환이 필요없는거다. 클래스만 아니라 메서드에서도 사용가능.

- java 의 객체지향4

  exception: try~catch 로 처리하여 exception handling을 진행한다.
  checked exception: 예외 처리 없다면 컴파일이 안된다.
  unchecked exception: 예외 처리 없어도 컴파일은 된다.

  java library 에 다양한 예외처리를 함수로 많이 제공해준다.

  try~catch의 흐름: try에서 예외가 발생하면 jvm이 해당 exception 클래스의 객체 생성 후 던진다. 던져진 exception을 처리할 수 있는 catch 블록에서 받은 후 처리. 단 적당한 catch 블록을 만나지 못하면 예외처리는 실패한다.

  다중 exception 을 진행할시에 catch를 여러개 하면 된다. 이때 자손에서 조상 순으로 해야한다. 그렇지 않으면 조상이 먼저 exception이 실행되기에 도달할 수 없는 코드라는 오류가 뜬다.

  finally: 예외 발생 여부와 상관 없이 언제나 실행되며 중간에 return을 만나더라도 finally 블록을 먼저 수행 후 리턴을 실행한다.

  throws: 예외를 처리하는 것이 아닌 단지 던져서 떠넘기는 것 뿐이다 예외처리는 try catch 에서

  runtime exception 은 throws 를 하지 않아도 전달 되기에 좀 더 신경 쓰고 catch 해줘야 한다.

  결국 이러한 과정을 통해 예외의 종류, 예외의 원인, 디버깅의 출발점을 잘 찾아보아 오류를 해결해야한다.

  메서드를 재정의 하면 조상이 던지는 예외보다 부모예외를 던질 수 가 없다. 즉 더 큰 예외를 던질 수 없다.

  사용자 정의 예외 Exception 을 상속받아 원하는 예외 형태를 만들 수 있다.(java의 장점)

-

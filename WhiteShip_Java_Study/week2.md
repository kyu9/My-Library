# Week2\(자바 데이터 타입, 변수 그리고 배열\)

## 프리미티브 타입 종류와 값의 범위 그리고 기본 값

* Primitive type은 JavaVM에서 지원하는 비객체형 타입으로 자바 언어에 내장된 기본 유형
* 자바는 정수, 실수, 논리, 문자 방식의 Primitive type을 지원한다.
* stack 메모리에 저장된다.
* 실제 값을 전달하고 stack영역에 생성, 종료됨
* 산술 연산이 가능하고 null로 초기화할 수 없다.
* 종류
  * byte
    * 8비트 크기에 부호 있는 정수
    * 범위 : -128 ~ 127
    * 기본값 0
    * wrapper class : Byte
  * short
    * 16비트 크기에 부호 있는 정수
    * 범위 : -32768 ~ 32767
    * 기본값 0
    * wrapper class : Short
  * int
    * 32비트 크기에 부호 있는 정수
    * 범위 : -2147483648 ~ 2147483647
    * 기본값 0
    * wrapper class : Integer
  * long
    * 65비트 크기에 부호 있는 정수
    * 범위 : -9223372036854775808 ~ 9223372036854775807
    * 기본값 0L
    * wrapper class : Long
  * float
    * 32비트 크기에 실수
    * 기본값 0.0f
    * 부동소수점 방식으로 메모리에 저장
    * wrapper class : Float
  * double
    * 64비트 크기에 실수
    * 부동소수점 방식으로 메모리에 저장
    * 기본값 0.0d
    * wrapper class : Double
  * boolean
    * true, false의 두 가지 값을 가지는 논리형
    * 참/거짓 상태를 판별하기 위한 간단한 flag로 boolean이 사용됨
    * 1bit의 정보로 표현하지만 사용하는 메모리의 크기는 미정임
    * 기본값 false
    * wrapper class : Boolean
  * char
    * 16비트 유니 코드 문자
    * 범위 0 ~ 65535 or ' u0000' ~' ufff'
    * 기본값 : '\u0000'
    * wrapper class : Charater
* wrapper class : 산술 연산이 불가능하고, null값으로 초기화할 수 있다.
  * 왜? 
    * 매개변수로 객체가 요구되는 경우
    * 기본형이 아닌 객체로 저장을 해야하는 경우
    * 객체간의 비교가 필요한 경우

## Primitive type VS Reference type

자바의 자료형은 위 두 가지 타입으로 나뉠 수 있고 primitive type은 기본형이라고 불리우고, reference type은 참조형으로 불리운다.

* Primitive type
  * 비객체 타입
  * Null을 가질 수 없는 형태
  * 자료의 실제 값이 변수에 저장되는 형태임
* Reference type
  * 기본적으로 java.lang.Object을 상속받는다.
  * 선언한 자료형이 기본형이 아닌경우 참조형이다.
  * 변수에 값을 저장하는 형태가 아니라 값이 저장된 장소를 가리키는 형태

## Literal

소스 코드 내에 직접 입력된 값을 의미한다. = 변수 초기화 시 저장할 값에 해당

* 정수 : byte, char, short, int, long에 저장
* 실수 : float, double에 저장
* 문자 : ' '로 묶인 텍스트, 이스케이프문자\(\)
* 논리 : boolean에 저장

## 변수 선언 및 초기화 하는 방법

* 변수 초기화 : 변수를 선언하고 처음으로 값을 저장하는 것을 변수 초기화라고한다.
  * 멤버변수는 초기화 하지 않아도 변수의 타입에 맞는 기본값으로 초기화가 이루어지지만 지역변수는 사용하기 전에 반드시 초기화 필요함
* 멤버변수를 초기화하는 방법
  * 명시적 초기화 : 변수를 선언을 함과 동시에 초기화하는 방법
  * ```text
    class Car{
        int door = 4;//기본형 변수의 초기화
        Engine engine = new Engine();//참조형 변수의 초기화
    }
    ```
  * 초기화 블럭 : 메소드에서와 같이 조건문, 반복문, 예외 처리 구문등 자유롭게 이용이 가능하고, 초기화 작업이 복잡할때 사용한다.
    * 클래스 초기화 블럭 : 클래스 초기화시 사용, 클래스가 처음 메모리에 로딩될 떄 수행
    * 인스턴스 초기화 블럭 : 인스턴스 변수를 초기화하는데 사용, 생성자와 같이 인스턴스가 수행될 때 수행, 인스턴스 초기화 블럭이 생성자보다 먼저 수행
* 멤버변수의 초기화 시기와 순서
  * 클래스 변수
    * 초기화 시점 : 클래스가 처음 로딩될때만
    * 초기화 순수 : 기본값 -&gt; 명시적 초기화 -&gt; 클래스 초기화 블럭
  * 인스턴스 변수
    * 초기화 시점 : 인스턴스가 생성될 때마다 각 인스턴스별로 초기화
    * 초기화 순서 : 기본값 -&gt; 명시적 초기화 -&gt; 인스턴스 초기화 블럭 -&gt; 생성자
  * ```text
    class Test{
        //명시적 초기화
        static int a = 1;
        int b = 2;

        //클래스 초기화 블럭
        static{
            a = 2;
        }

        //인스턴스 초기화 블럭
        {
            b=2;
        }

        //생성자
        Test(){
            b=3;
        }
    }
    ```

## 변수의 스코프와 라이프 타임

* 변수의 Scope : 프로그램 상에서 사용되는 변수들은 그 변수가 사용 가능한 범위를 갖게된고 변수가 선언된 블럭이 그 변수의 사용범위가 된다.

  종류로써는 3가지 종류의 변수가 있다.

  * 지역변수
    * 메소드 내부에서 선언한 변수이고, 해당 메소드 밖에서는 사용할 수 없다.
    * 클래스가 메모리에 올라갈때 생성된다.
    * 함수를 호출하게되면 스택 메모리에 생성되게 되고 해당 함수가 종료하면 스택이 사라지게 되면서 그 안에 있던 변수들은 사라지게 되면서 지역 변수는 사용할 수 없게 된다.
    * 지역변수는 변수의 이름이 같아도 각각 다른 변수로 인식하게 된다.
    * ```text
      public class Scope{
          //멤버 변수
          int a = 25;

          //밖에서 a라고 선언해도 f1, f2에서도 a로 선언해서 변수 사용이 가능하다.
          public void f1(){
                  //f1의 지역변수 
                  int a = 10;
                  System.out.println(a);//10
          }
          public void f2(){
                  //f2의 지역변수 
                  int a = 15;
                  System.out.println(a);//15
          }
          public static void main(String[] args){
                  Scope s = new Scope();
                  s.f1(); //10
                  s.f2(); //15
                  int a = 20;
                  System.out.println(a); //20
                  System.out.println(s.a); //25
          }
      }
      ```
  * 멤버변수
    * new 키워드로 인스턴스를 생성해야 사용할 수 있다.
    * Heap 메모리에 생성되게 되며 멤버 변수는 해당 클래스의 메소드에서 사용 가능하다.
    * 만약 public으로 설정되어있다면, 같은 패키지의 다른 클래스들도 사용이 가능
    * 만약 private으로 설정되어있다면, 다른 클래스에서의 접근이 제한되고 만약 다른 클래스들이 사용하고 싶다면 getter / setter 함수를 통해서 접근하면 된다 = 데이터의 보안성이 보장된다.
  * static 변수
    * 프로그램 실행시, 클래스를 메모리에 로드했을 때부터 생성된다.
    * new키워드로 인스턴스를 생성하지 않아도 사용가능
    * 메모리\(stack, heap, data\)부분에서 data부분에 생성되게 된다.
    * 메모리에 로드해서 사용하기 때문에 속도도 빠르지만 프로그램이 종료되기 전까지는 살아있다\(그만큼 시스템의 메모리가 줄어든다\)
    * 순서 : 프로그램 실행 -&gt; 클래스 로드\(static 생성\) -&gt; 인스턴스 생성
    * 정적 변수라고도 불리우고 클래스에 하나밖에 없기 때문에 클래스 변수라고도 불리움

## 타입 변환, 캐스팅 그리고 타입 프로모션

* 타입 변환에는 두 가지 종류가 있음
  * 자동 타입 변환
    * 프로그램 실행 도중에 자동으로 타입 변환이 일어난다.
    * 작은 크기를 가지는 타입이 더 큰 크기의 타입으로 저장되었을때 발생함
    * 타입별 크기 순서
      * byte\(1\) &lt; short\(2\) &lt; int\(4\) &lt; long\(8\) &lt; float\(4\) &lt; double\(8\)
    * 음수가 저장될 수 있는 byte, int 등의 타입은 char 타입으로 자동 타입 변환할 수 없음
  * 강제 타입 변환
    * 큰 크기의 타입을 작은 크기의 타입으로 자동 타입 변환은 불가능
    * 하지만 강제로 잘라서는 가능하긴 하다.
    * 강제 타입 변환에서는 입력값에 대해서 변환시, 값의 손실이 일어나지 않도록 주의, 값이 보존할 수 있는지 확인할 필요가 있음
    * 연산 시 자동 타입 변환 정리
      * 정수-실수 =&gt; double
      * 정수-정수 =&gt; int
      * 실수-실수 =&gt; double
      * 큰 타입-작은 타입 =&gt; 큰 타입
* Casting : 특정 자료형을 다른 자료형과 호환되게 다른 자료형으로 변환하는 연산자
  * boolean제외한 기본형들은 서로 형변환이 가능하다.
  * primitive-reference간에는 서로 형변환이 불가능하다.
  * 값의 범위가 작은 타입에서 큰 타입으로의 변환은 생략가능
* type promotion
  * 자바에서는 표현식에 적용되는 type promotion 규칙들이 있다.
    * 모든 byte, short, char들은 int형으로 변경된다.
    * 피연산자의 타입에 따라서 변경되서 계산된다.

## 1차 및 2차 배열 선언하기

## 배열이란

* 같은 타입의 변수들로 이루어진 유한 집합
* 배열을 구성하는 각각의 값을 element라고 하며 배열에서의 위치를 가리키는 숫자를 index라고 한다.
* 인덱스는 항상 0부터 시작하며 0을 포함한 양의 정수로 구성된다.

## 1차원 배열

* 선언
  * ```text
    타입[] 배열이름;
    or
    타입 배열이름[];
    ```
  * 타입은 배열 요소\(element\)로 저장되는 변수의 타입을 명시
  * 배열 이름은 배열이 선언된 후에 배열에 접근하기 위해서 사용됨
  * 만약 배열의 길이보다 적은 수의 배열 요소를 초기화하게 되면, 나머지는 배열의 타입에 맞게 자동으로 초기화
    * char - '\u0000'
    * byte, short, int - 0
    * long - 0L
    * float - 0.0F
    * double - 0.0 or  0.0D
    * boolean - false
    * 배열, 인스턴스 - null

## 2차원 배열

* 배열의 요소\(element\)으로 1차원 배열을 가지는 배열
* 선언
  * ```text
    타입[][] 배열이름;
    or
    타입 배열이름[][];
    or
    타입[] 배열이름[];
    ```
* 예제

  ```text
  public class Array {
      public static void main(String[] args) {
          int[][] arr = new int[2][3];

          int k =10;
          for(int i=0;i<arr.length;i++){
              for(int j=0;j<arr[i].length;j++){
                  arr[i][j] = k;
                  k = k + 10;
              }
          }

          for(int i=0;i<arr.length;i++){
              for(int j=0;j<arr[i].length;j++){
                  System.out.println(arr[i][j] + " ");
              }
              System.out.println();
          }
      }
  }
  ```

* 배열의 선언과 동시에 초기화하는 방법
  * ```text
    타입 배열이름[열][행] = {
        {배열요소[0][0], 배열요소[0][1], ...},
        {배열요소[1][0], 배열요소[1][1], ...},
        {배열요소[2][0], 배열요소[2][1], ...},
        ...
    };
    ```
* 가변 배열
  * 열의 길이를 명시하지 않음으로써, 행마다 다른 길이의 배열을 요소로 저장할 수 있음
  * ```text
    int[][] arr = new int[3][];
    arr[0] = new int[2];
    arr[1] = new int[4];
    arr[2] = new int[1];
    //행을 생략했기 때문에 행마다 다른 길이의 배열을 저장할 수 있는 배열생성됨
    ```

## 타입 추론, var

* 타입 추론이란 타입이 정해지지 않은 변수의 타입을 컴파일러가 유추ㄹ하는 기능
* 자바에서의 타입 추론은 제네릭과 람다에 대한 타입 추론을 의미한다.
* 자바 10부터 타입추론을 지원하는 var 키워드가 추가됨
  * 이 키워드는 local variable임
  * 선언과 동시에 initializer가 필수로 요구됨
  * ```text
    //java 9이하
    String message = "data";
    //java 10이상
    var message = "data";
    ```
  * 다른 사람들과의 공유시 가독성에 대해서 문제가 생길수 있음
    * 위치만 보고 Message에 어떤 타입의 데이터가 할당되는지 모름


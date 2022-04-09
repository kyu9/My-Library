# 뷰 작성과 삭제
_뷰는 테이블과 같은 부류의 데이터베이스 객체_
<br><br>

## 뷰
데이터베이스 객체란 테이블이나 인덱스 등 데이터베이스 안에 정의하는 모든 것을 의미 <br>
본래 데이터베이스 객체로 등록할 수 없는 SELECT 명령을, 객체로서 이름을 붙혀서 관리할 수 있도록 한 객체이다 <br>
select는 단지 저장된 데이터 값을 반환하는 것이 끝이지만, 뷰를 참조함으로써 그에 정의된 SELECT 명령의 실행결과를 **테이블처럼** 사용 가능 <br>
<br><br>

```sql
SELECT * FROM (SELECT * FROM sample54) sq;
```
이렇게 서브쿼리를 사용하던 것을 <br>
```sql
SELECT * FROM sample_view_67;
```
이렇게 사용할 수 있다 <br>
이게 무슨 의미가 있냐라고 하면 생각보다 길어지는 쿼리문에서 GROUP BY등으로 묶다보면 정말 가독성인 부분도 그렇고 겹치는 SELECT 문이 생길수도 있음 <br>
그래서 결국은 자주 사용하거나 복잡한 SELECT 명령을 뷰로 만들어서 편리하게 사용할 수 있다는 점을 기억하자 <br>
<br>

#### 가상 테이블
뷰를 테이블처럼 사용하는 것이 가능하지만 실체가 존재하지 않기 때문에 가상테이블이라고도 불리운다 <br>
SELECT 명령으로 이루어지는 뷰는 테이블처럼 데이터를 쓰거나 지울 수 있는 저장공간을 가지지 않는다 <br>
그래서 막 INSERT, UPDATE, DELETE 와 같은 명령에서도 사용할 수는 있지만 그냥 SELECT 할때만 사용하자.... <br>
<br><br><br>

## 뷰 작성과 삭제
뷰는 데이터베이스 객체이기 때문에 DDL로 작성하거나 삭제한다 <br>
CREATE VIEW, DROP VIEW 키워드를 통해서 사용한다 <br>
<br>

#### 뷰의 작성
```sql
CREATE VIEW 뷰이름 AS SELECT 명령
```
CREATE VIEW 다음에 뷰의 이름을 지정하고 AS로 SELECT 명령을 지정해준다 <br>
뷰를 만드는데 있어서 AS 는 생략이 불가능 하다는 점 <br>
<br>

CREATE VIEW로 뷰를 작성하고 SELECT 을 거는데 있어서 필요에 따라서 열의 순서를 변경하는 것이 가능하다 <br>
```sql
CREATE VIEW 뷰이름(열1, 열2, ...) AS SELECT 명령
```
만약에 열 순서를 생략한 경우에는, **자동으로** 뷰의 열이 지정된다 <br>
그리고 SELECT 와 같은 수의 열을 일일이 지정해야 하므로 SELECT 명령의 모든 열을 사용할 경우에는 열을 지정하지 않는 것이 더 좋을지도? <br>
<br><br>

#### 뷰의 삭제
뷰를 삭제하는 경우에는 DROP VIEW 를 사용해서 삭제하고 삭제하게 되면 더이상은 뷰를 참조할 수 없다는 점 <br>
```sql
DROP VIEW 뷰명
```
<br><br><br>

## 뷰의 약점
위에서 언급했지만 뷰는 데이터베이스 객체이지만 저장공간을 필요로하지 않고 CPU 자원을 잡아먹는다 <br>
SELECT는 단순하게 조회해서 리턴해주는 명령인데, 검색, ORDER BY, GROUP BY 등으로 집계하는데 계산능력이 필요해서 CPU를 사용 <br>
<br><br>

#### 머터리얼라이즈드 뷰(Materialized View)
뷰의 근원이 되는 테이블에 보관하는 데이터양이 많거나 뷰를 중첩해서 사용하는 경우에도 처리 속도가 떨어지기 쉽다 <br>
이런 상황을 회피하기 위해서 사용하는 것이 머터리얼라이즈드 뷰이다 <br>
일반적으로 뷰는 데이터를 일시적으로 저장했다가 쿼리가 종료될 때 함께 삭제된다 <br>
하지만 머터리얼라이즈드 뷰는 테이블처럼 저장장치에 저장해두고 사용 <br>
<br>
이렇게 저장해두고 사용하게되면 이미 한번 참조했던 뷰를 다시 한 번 참조하게 되면 처음에 참조할 때의 데이터를 그대로 사용 <br>
하지만 테이블의 데이터가 변경된 경우에는 SELECT를 다시 실행해서 다시 저장한다 <br>
다른점이 있다면 일반 뷰처럼 매번 SELECT 할필요 없다는점이다 <br>
물론 이 모든건 RDBMS가 알아서 해준다 하지만 Oracle, DB2에서만 지원하고 MySQL에서는 지원하지 않는다 <br>
<br><br><br>


<br><br><br><br><br><br><br><br><br><br>
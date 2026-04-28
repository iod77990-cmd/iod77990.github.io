오후 5:42 2026-04-17

> - while문의 scope

---

### while문의 scope

- while문 밖의 변수
반복문이 끝나도 생성한 변수를 사용하고 싶을 때

- while문 안의 변수
반복이 끝날 때마다 메모리에서 지우고 매번 초기화됨

- while문 안과 밖의 변수
일명 변수 가리기 현상 발생
밖에서 생성한 변수가 안에서 생성한 변수에 의해 가려지는 현상


오후 5:27 2026-04-27

>- DB에서 테이블 정보 가져오기
>- DB에서 가져온 테이블 정보 입력한 값과 일치하는지 확인하기
SecSql 클래스, DBUtil클래스 사용

---

### DB에서 테이블 정보 가져오기

로그인 코드에서...
```sql

System.out.print("아이디 입력 : ");
      String Id = sc.nextLine().trim();

SecSql sql = new SecSql();
sql.append("SELECT * FROM tableName ");
sql.append("WHERE loginId = ?", Id);

// 1. DB에서 해당 아이디를 가진 '행(Row)' 하나를 통째로 가져옴
Map<String, Object> memberRow = DBUtil.selectRow(conn, sql);

```

### DB에서 가져온 테이블 정보 입력한 값과 일치하는지 확인하기

사용자에게 입력받은 정보 중에 비밀번호 일치하는지 확인
```sql

// 1. [논리 1단계] 이 주머니(Map)가 비었을까?
if (memberRow.isEmpty()) { 
    // 논리: 주머니가 비었다면 애초에 그런 아이디는 DB에 없다는 뜻
    return "아이디가 틀렸습니다.";
}

// 2. [논리 2단계] 주머니 안에 든 '진짜 비번'을 꺼내서 대조해볼까?
String dbPw = (String) memberRow.get("loginPw"); // DB에 저장된 값

if (dbPw.equals(loginPw)) {
    // 논리: 꺼내온 값과 입력한 값이 글자 하나 안 틀리고 똑같음
    return "로그인 성공";
} else {
    // 논리: 아이디는 맞아서 정보는 가져왔는데, 열쇠(비번)가 안 맞음
    return "비밀번호가 틀렸습니다.";
}

```

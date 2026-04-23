오전 9:55 2026-04-23

> - 인텔리제이로 mysqlDB 연결 하는 방법
> - 게시물 Write, List(조회), Modify, Delete

---

### 인텔리제이로 mysqlDB 연결 과정
1. 인텔리제이 IDE에서 Java프로젝트를 생성 

![새 프로젝트 생성 화면](./SQL/21D SQL/인텔리제이 새 프로젝트 캡쳐 2026-04-23 102336.png)

2. maven repo에서 mysql Connect/J설치

[Maven Repository](https://mvnrepository.com/artifact/com.mysql/mysql-connector-j/9.6.0)

버전은 최신버전으로

3. 만들어진 인텔리제이 프로젝트 창에 파일 -> 파일 구조 (사진 참고)

다운받은 mysql connetor.zip파일을 추가

![파일구조](./SQL/21D SQL/인텔리제이 파일 구조 캡쳐 2026-04-23 102921.png)

4. IDE의 오른쪽 DB아이콘을 누르고 
추가 버튼 -> 데이터 소스 -> mysql(maria DB) -> 접속중인 DB연결 참고해서
테스트 연결 성공 하면 연결 성공

![데이터베이스](./SQL/21D SQL/인텔리제이 파일 구조 캡쳐 2026-04-23 102921.png)

---

### 게시물 Write, List(조회), Modify, Delete

- Write(article write, 게시글 작성)

```java
// main(String[] args) 함수
if (cmd.equals("article write")) {
                System.out.println("== 글쓰기 ==");

                System.out.print("제목 : ");
                String title = sc.nextLine().trim();

                System.out.print("내용 : ");
                String body = sc.nextLine().trim();

                id = insertArticleToDb(title, body);

                System.out.printf("%d번째 게시물 작성 완료\n", id);

// insertArticleToDb(String title, String body) 함수
private static int insertArticleToDb(String title, String body) {
        Connection conn = null;
        PreparedStatement pstmt = null;
        ResultSet rs = null;
        int receivedId = -1;

        try {
            String url = "jdbc:mariadb://127.0.0.1:3307/JDBC_AM_26_04?useUnicode=true&characterEncoding=utf8&autoReconnect=true&serverTimezone=Asia/Seoul";
            conn = DriverManager.getConnection(url, "root", "");

            System.out.println();
            System.out.println("연결 성공!😎");

            String sql = "INSERT INTO article SET regDate = NOW(), updateDate = NOW(), title = ?, `body` = ?";

            pstmt = conn.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS);
            pstmt.setString(1, title);
            pstmt.setString(2, body);
            int affectedRow = pstmt.executeUpdate();
            System.out.println("affectedRow = " + affectedRow);

            rs = pstmt.getGeneratedKeys();
            if(rs.next()){
                receivedId = rs.getInt(1);
            }

            System.out.println("게시물이 DB에 저장 성공 😎");

        } catch (SQLException e) {
            System.out.println("DB연결 실패 또는 에러😳 : " + e.getMessage());
        } finally {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        return receivedId;
    }
```

- List(article list, 게시글 조회)

```java
// main(String[] args) 함수
else if (cmd.equals("article list")) {
                System.out.println("== 목록 ==");
                List<Article> articles = getArticleFromDb();

                if (articles == null) {
                    System.out.println("게시글이 없습니다.");
                    continue;
                }

                System.out.println(" 번호 | 작성일 | 수정일 | 제목 | 내용");
                for (Article article : articles) {
                    System.out.println(article.toString());
                }

// getArticleFromDb() 함수
private static List<Article> getArticleFromDb() {
        List<Article> articles = new ArrayList<>();
        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            String url = "jdbc:mariadb://127.0.0.1:3307/JDBC_AM_26_04?useUnicode=true&characterEncoding=utf8&autoReconnect=true&serverTimezone=Asia/Seoul";
            conn = DriverManager.getConnection(url, "root", "");
            System.out.println();
            System.out.println("연결 성공!😎");

            String sql = "SELECT *  FROM article ORDER BY id DESC";

            System.out.println(sql);

            pstmt = conn.prepareStatement(sql);

            ResultSet rs = pstmt.executeQuery(sql);

            while (rs.next()) {
                int id = rs.getInt("id");
                String regDate = rs.getString("regDate");
                String updateDate = rs.getString("updateDate");
                String title = rs.getString("title");
                String body = rs.getString("body");

                Article article = new Article(id, regDate, updateDate, title, body);
                articles.add(article);
            }

            System.out.println("DB에 저장된 게시물 조회 성공!😎");

        } catch (SQLException e) {
            System.out.println("DB연결 실패 또는 에러😳 : " + e.getMessage());
        } finally {

            try {
                if (pstmt != null && !pstmt.isClosed()) {
                    pstmt.close();
                }
            }catch (SQLException e){
                e.printStackTrace();
            }
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
        return articles;
    }
```

- Modify(article modify n, 게시글 수정)

```java
// main(String[] args) 함수

else if (cmd.startsWith("article modify")) {
                System.out.println("== 게시글 수정 ==");
                id = Integer.parseInt(cmd.split(" ")[2]);

                System.out.print("새로운 제목 : ");
                String newTitle = sc.nextLine().trim();

                System.out.print("새로운 내용 : ");
                String newBody = sc.nextLine().trim();

                updateArticleToDb(id, newTitle, newBody);
            }

// updateArticleToDb(int id, String newtitle, String newbody) 함수
 private static void updateArticleToDb(int id, String newtitle, String newbody) {
        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            String url = "jdbc:mariadb://127.0.0.1:3307/JDBC_AM_26_04?useUnicode=true&characterEncoding=utf8&autoReconnect=true&serverTimezone=Asia/Seoul";
            conn = DriverManager.getConnection(url, "root", "");

            System.out.println();
            System.out.println("연결 성공!");

            String sql = "Update article SET regDate = NOW(), updateDate = NOW(), title = ?, `body` = ? WHERE id = ?";

            pstmt = conn.prepareStatement(sql);
            pstmt.setString(1, newtitle);
            pstmt.setString(2, newbody);
            pstmt.setInt(3, id);

            int affectedRow = pstmt.executeUpdate();
            System.out.println("affectedRow = " + affectedRow);

            if(affectedRow > 0){
                System.out.println(id + "번 게시물 수정 완료");
            }else{
                System.out.println("수정할 게시물을 찾을 수 없거나 존재하지 않음");
            }

        } catch (SQLException e) {
            System.out.println("DB연결 실패 또는 에러 : " + e.getMessage());
        } finally {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
```

- Delete(article delete n, 게시글 삭제)

```java
// main(String[] args)함수
else if (cmd.startsWith("article delete")) {
                System.out.println("== 삭제 ==");
                id = Integer.parseInt(cmd.split(" ")[2]);

                deleteArticleToDb(id);

            }

// deleteArticleToDb(int id) 함수
private static void deleteArticleToDb(int id) {
        Connection conn = null;
        PreparedStatement pstmt = null;

        try {
            String url = "jdbc:mariadb://127.0.0.1:3307/JDBC_AM_26_04?useUnicode=true&characterEncoding=utf8&autoReconnect=true&serverTimezone=Asia/Seoul";
            conn = DriverManager.getConnection(url, "root", "");

            System.out.println();
            System.out.println("연결 성공!");

            String sql = "DELETE FROM article WHERE id = ?";

            pstmt = conn.prepareStatement(sql);

            pstmt.setInt(1, id);

            int affectedRow = pstmt.executeUpdate();
            System.out.println("affectedRow = " + affectedRow);

            if(affectedRow > 0){
                System.out.println(id + "번 게시물 삭제 완료");
            }else{
                System.out.println("삭제할 게시물을 찾을 수 없거나 존재하지 않음");
            }

        } catch (SQLException e) {
            System.out.println("DB연결 실패 또는 에러 : " + e.getMessage());
        } finally {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

```
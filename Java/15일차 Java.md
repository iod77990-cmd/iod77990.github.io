> - getter 와 setter의 위치
> - git 터미널로 파일 을 업로드하는 일련의 방식

### getter와 setter의 위치
- getter와 setter는 한쌍으로 생성한 관련있는 클래스의 범위 안에 함수로 생성
- getter는 저장된 데이터를 반환을 하는 역할
- setter는 main클래스에서 데이터를 해당 클래스에 대입을 해서 저장을 하는 역할
**클래스의 변수를 private으로 보호하는 경우 getter와 setter를 이용해서 데이터 반환 및 저장 및 수정**

❓ 궁금한 사항
- 생성자와 setter는 차이가 뭐임?
> 생성자는 변수 초기화 처럼 클래스가 생성이 되고 제일먼저 클래스 변수를 초기화를 시켜주는 역할
> setter는 이후 private으로 지정된 변수에 데이터를 저장을 하고 데이터 수정을 하는 역할

### git
1. 해당 폴더에서 git init: 초기화
2. git remote add origin "리포지터리 주소"
3. git branch -m main 브랜치를 main으로 변경
4. 계정 연동
5. git add .
6. git commit -m "메시지"
7. git push origin main
8. push 가 안되는 경우 git pull origin main으로 병합한 후 다시 push
9 또는 git pull --rebase origin main하고 다시 push



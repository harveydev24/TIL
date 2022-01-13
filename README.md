# Today I Learned

## Git
- 분산 버전 관리 시스템
- 세 단계로 구성
    1. working directory
    2. staging area
    3. repository

## Github
- 원격 저장소

## Git 명령어
- `git init`: git 초기화
- `git status`: 현재 저장소 상태 보기
- `git add .`: working directory의 변경 사항을 staging area로 옮김
- `git commit -m "commit message"`: staging area에 있는 것들을 커밋함
- 원격 저장소 연결 방법
    1. `git clone githubaddress`: 원격 저장소의 코드를 다운
    2. `git remote add origin githubaddress`: 로컬 저장소를 원격 저장소와 연결
- `git push -u origin master`: 최초로 원격 저장소에 푸쉬
- `git push`: 이후에 푸쉬
- `git push`: 원격 저장소 가져오기
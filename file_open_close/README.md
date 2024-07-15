# 실행 순서
1. fopen_close.c
2. o_excl.c
3. alloc.c
# 코드 설명
- *fopen_close.c*
  - mode에 권한 설정을 담기
    - user : R/W
    - group : R
    - others : R
  - open()을 통해 hello.txt 파일 생성
    - 실패 시, -1 반환
    - O_CREAT : 파일이 존재하지 않으면 새로 만들기
  - if문은 기본적인 오류 검사
    - perror 함수를 통해 오류 메시지 출력
- *o_excl.c*
  - 기존 mode 자리에 직접 권한 입력
  - open()을 통해 hello.txt 파일 생성
    - O_CREAT : 파일이 존재하지 않으면 새로 만들기
    - O_EXCL : 파일이 이미 존재하면 오류 반환
  - if문은 기본적인 오류 검사
    - perror 함수를 통해 오류 메시지 출력
- *alloc.c*
  - openFile()
    - open()을 통해 hello.txt 파일 생성
      - O_RDWR : 파일 읽기/쓰기 모드
    - if문은 기본적인 오류 검사
      - perror 함수를 통해 오류 메시지 출력
  - main()
    - 파일 디스크립터인 fd를 저장하고 출력
    - fd를 닫고, stdin인 0도 닫기
      - 0을 닫았기 때문에 현재 0은 비어있고, 1과 2는 존재한 상태
    - 다시 file을 open하면 자동으로 0을 할당하게 됨

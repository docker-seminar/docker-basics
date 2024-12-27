# 실습 안내

Docker 공식 문서 등을 통해 배운 내용을 실습하는 과정입니다.

# 단계

## Dockerfile reference 의 각 키워드 학습

https://docs.docker.com/reference/dockerfile/

1. FROM \<image\>
    - https://docs.docker.com/reference/dockerfile/#from
    - `FROM` 키워드가 포함된 최소한의 Dockerfile 작성
2. FROM \<image\>:\<tag\>
    - https://docs.docker.com/reference/dockerfile/#from
    - Image 의 tag 가 포함된 최소한의 Dockerfile 작성
3. FROM --platform=\<platform\> \<image\>:\<tag\>
   - https://docs.docker.com/reference/dockerfile/#from
   - `platform` 플래그가 포함된 최소한의 Dockerfile 작성
4. RUN - Shell form
   - https://docs.docker.com/reference/dockerfile/#run
   - Shell form 의 `RUN` 키워드가 포함된 최소한의 Dockerfile 작성
   - escape 를 사용하여 2 줄 이상의 명령어 사용
5. RUN - Exec form
   - https://docs.docker.com/reference/dockerfile/#run
   - Exec form 의 `RUN` 키워드가 포함된 최소한의 Dockerfile 작성
6. RUN - Shell form with Here-Documents
   - https://docs.docker.com/reference/dockerfile/#here-documents
   - Here-documents 를 사용하여 2줄 이상의 `RUN` 명령어가 포함된 Dockerfile 작성

# 방법

1. 각 단계의 링크를 링크의 내용으로 정리해서 대체
    - 예:
      ```
      1. FROM <image>
         - 새로운 빌드 스테이지를 초기화
         - 이후 명령어에 사용할 기본 이미지 설정
         - 유효한 Dockerfile 은 반드시 `FROM` 명령어로 시작해야 함
      ```
2. `/hands-on/[카테고리]/##` 디렉토리 생성
    - 예: `/hands-on/dockerfile-reference/01`
3. 해당 키워드가 포함된 최소한의 Dockerfile 작성
   - 예시 파일명: `/handson/dockerfile-reference/01/Dockerfile`
    - 예 1:
   ```Dockerfile
   # `FROM` 키워드가 포함된 최소한의 Dockerfile 작성
   FROM ubuntu
   ```
    - 예 2:
   ```Dockerfile
   # Image 의 tag 가 포함된 최소한의 Dockerfile 작성
   FROM ubuntu:latest
   ```

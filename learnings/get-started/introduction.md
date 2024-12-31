# Introduction
Docker와 컨테이너화를 이해하기 위한 포괄적인 학습 경로를 시작하며, 기본 개념과 설치 절차부터 시작합니다. 필수적인 Docker 명령, 이미지 생성 및 컨테이너 오케스트레이션을 다루는 실습 연습을 통해 진행합니다.

학습 내용
Docker Desktop 설정
첫 번째 컨테이너 실행
첫 번째 이미지 빌드
Docker Hub에 이미지 게시

# Get Docker Desktop
Docker Desktop은 이미지를 빌드하고, 컨테이너를 실행하고, 그 외 많은 작업을 할 수 있는 올인원 패키지이다.

### Docker Desktop 설정 및 첫 번째 컨테이너 실행
1. 공식 [사이트](https://docs.docker.com/get-started/introduction/get-docker-desktop/)에서 개발 환경에 맞는 설치 파일을 다운로드.
2. (Windows 기준) 사용자의 편의에 맞는 환경 (WSL2, Hyper-v)을 선택 한 후 설치
3. 설치 완료후 Powershell 또는 CMD 를 사용해 `docker run -d -p 8080:80 docker/welcome-to-docker` 커맨드를 실행 하여 첫번째 컨테이너를 실행.

> 성능상 WSL2가 뛰어나다고는 하지만 이미 Hyper-v를 사용하고 있어서 Hyper-v로 설치함.

# Develop with containers
1. 개발 프로젝트 클론 및 시작
    1. GitHub에서 프로젝트를 클론합니다.
   ```bat
   git clone https://github.com/docker/getting-started-todo-app
   cd getting-started-todo-app
   ```
    2. Docker Compose를 사용하여 개발 환경을 시작합니다.
    ```bat
   docker compose watch
   ```
    3. 브라우저에서 애플리케이션을 확인합니다 `http://localhost/`.


# Build and push your first image

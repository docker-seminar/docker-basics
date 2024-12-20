# Introduction

Docker Desktop은 개발자가 로컬 시스템에서 컨테이너화된 애플리케이션을 쉽게 구축하고 실행할 수 있도록 도와주는 도구입니다. Docker는 애플리케이션을 격리된 환경에서 실행할 수 있게 해주는 컨테이너 기술로, 시스템의 일관성 및 재현성을 보장하며, 다양한 플랫폼 간에 동일한 환경을 유지할 수 있습니다.

Docker Desktop은 Windows와 macOS에서 사용할 수 있으며, 다양한 개발 및 테스트 환경을 구축하고, 이미지를 관리하며, 컨테이너를 실행하는 데 필요한 모든 도구를 제공합니다.

# Get Docker Desktop


### 1. Docker Desktop 다운로드

- Docker Desktop은 [Docker 공식 웹사이트](https://www.docker.com/products/docker-desktop)에서 다운로드할 수 있습니다.
- 운영 체제에 맞는 설치 파일을 다운로드합니다:
  - **Windows**: Windows 10 Pro 이상, WSL 2를 지원하는 버전 필요.
  - **macOS**: macOS 10.14 이상 지원.

### 2. 설치 과정

#### Windows
1. 다운로드한 `Docker Desktop Installer.exe` 파일을 실행합니다.
2. 설치 중 WSL 2를 설치하라는 안내가 나오면, 지침에 따라 설치를 진행합니다.
3. 설치가 완료되면 Docker Desktop을 실행하고, 시스템 트레이에서 Docker 아이콘을 확인할 수 있습니다.

### macOS
1. 다운로드한 `Docker.dmg` 파일을 실행하여 애플리케이션 폴더로 드래그하여 설치합니다.
2. Docker Desktop을 실행하면 초기 설정이 자동으로 진행됩니다.
3. 메뉴 바에서 Docker 아이콘을 확인하여 설치가 완료된 것을 확인합니다.


# Develop with containers


Docker Desktop을 사용하여 로컬에서 컨테이너화된 애플리케이션을 개발하는 과정은 매우 직관적입니다. Docker는 환경을 격리하여 애플리케이션을 실행하기 때문에 개발 환경을 보다 효율적으로 관리할 수 있습니다.

### 1. Dockerfile 작성

컨테이너 이미지를 만들기 위해서는 `Dockerfile`을 작성해야 합니다. `Dockerfile`은 애플리케이션이 실행되는 환경을 정의하는 텍스트 파일입니다.

예시 `Dockerfile`:
```dockerfile
# Node.js 기반 이미지 사용
FROM node:16

# 작업 디렉토리 생성
WORKDIR /app

# 의존성 설치
COPY package.json /app
RUN npm install

# 애플리케이션 코드 복사
COPY . /app

# 애플리케이션 실행
CMD ["npm", "start"]

# Build and push your first image

docker build -t weng_weng/my_test_app .

docker login

docker push weng_weng/my_test_app

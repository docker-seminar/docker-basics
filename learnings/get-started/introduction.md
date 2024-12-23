# Introduction

# Get Docker Desktop
## Docker Desktop이란?
다양한 환경에서 애플리케이션의 설정, 구성, 및 호환성을 간소화하여 개발자가 컨테이너를 효율적으로 관리할 수 있도록 돕는 도구 
이를 통해 환경 불일치와 배포 문제를 해결하고 개발 효율성을 높일 수 있음

## 컨테이너 실행
```bash
docker run -d -p 8080:80 docker/welcome-to-docker
```
위 명령어로 컨테이너를 실행
브라우저에서 http://localhost:8080/로 접속하여 확인 가능
8080 포트를 다른 서비스(예: DB)에서 사용 중인 경우, 다른 포트 번호를 지정

## Docker Desktop을 사용하여 컨테이너 관리
### 1. Docker Desktop 실행
### 2. 왼쪽 사이드바에 컨테이너 필드 선택
### 3. Exec 탭
Shell에 엑세스 가능
### 4. Inspect 탭
컨테이너의 자세한 정보를 확인하거나, 컨테이너 일시 중지, 재개, 시작, 중지 작업 수행 가능

# Develop with containers
## 프로젝트 시작
### 1. 프로젝트를 로컬에 다운로드 및 이동동
```bash
git clone https://github.com/docker/getting-started-todo-app
cd getting-started-todo-app
```
### 2. Docker Compose를 사용하여 개발 환경을 시작
```bash
docker compose watch
```
이 명령어는 컨테이너 이미지를 다운로드하고 실행
실행된 컨테이너는 Docker Desktop의 Containers 탭에서 확인 가능
### 3. 애플리케이션이 실행 중인지 확인
**Containers**탭에서 실행 중인 컨테이너 이름 클릭
**프록시 컨테이너(getting-started-todo-app-proxy-1)** 에 url 클릭
url : localhost:80

# Build and push your first image
## 1. Docker Hub에 이미지 저장소 만들기
Docker Hub에 저장소 만들기 선택

## 2. 컨테이너 이미지 빌드
그 저장소에 이미지를 빌드하고 푸시할 수 있음
빌드하는 이미지가 Node 이미지를 확장하며 Node.js와 Yarn 등 필요한 환경이 이미 포함되어 있음

## 3. Docker Hub에 이미지 푸시
### 3-1. 프로젝트를 로컬에 다운 및 이동
```bash
git clone https://github.com/docker/getting-started-todo-app
cd getting-started-todo-app
```
### 3-2. 프로젝트를 빌드하고, DOCKER_USERNAME사용자 이름을 바꾸기
```bash
docker build -t <DOCKER_USERNAME>/getting-started-todo-app .
```
### 3-3. 이미지가 로컬에 존재하는지 확인
```bash
docker image ls
```
### 3-4. 이미지 푸시
```bash
docker push <DOCKER_USERNAME>/getting-started-todo-app
```
### 이미지/Dockerfile이란?
**Docker 이미지** : 프로세스를 실행하는 데 필요한 모든 환경과 코드를 포함하는 단일 패키지
-> 노드 환경, 백엔드 코드, 컴파일된 React 코드가 포함될 수 있음
**Dockerfile** : 이미지를 빌드하기 위한 명령어와 구성을 정의한 파일
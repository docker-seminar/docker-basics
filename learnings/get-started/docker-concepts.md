# Docker Concepts

# The Basics

## Container

**컨테이너(Container)** : 애플리케이션과 그 애플리케이션을 실행하는 데 필요한 모든 파일, 라이브러리, 설정을 함께 포함하는 독립적이고 가벼운 실행 환경

### 컨테이너의 주요 특징
#### 1. 격리 실행
각 컨테이너는 독립적으로 실행되며, 호스트 시스템 및 다른 컨테이너와 간섭 없이 동작
#### 2. 경량화
실행에 필요한 최소한의 구성만 포함
#### 3. 이식성
데이터 센터, 클라우드 등 다양한 환경에서 동일한 방식으로 작동
#### 4. 이미지 기반으로 생성성

### 컨테이너와 가상 머신의 차이
|  | Docker 컨테이너 | 가상 머신(VM) |
|:----------|:----------:|:----------:|
| 실행 속도 | 매우 빠름 | 느림 |
| 크기 | 작음 | 큼 |
| 격리 수준 | 프로세스 수준 격리 | 완전한 OS 격리 |
| 자원 사용량 | 작음 | 큼 |
| 호스트OS 필요 여부 | 필요 | 불필요 |

### VM과 Docker 컨테이너의 조합 사례
#### 1. 호스트 OS 제한 해결
Docker는 일반적으로 Linux 커널을 기반으로 작동
Windows와 macOS에서 Docker 컨테이너를 실행하기 위해 내부적으로 Linux VM을 사용

#### 2. VM은 멀티 클라우드와 온프레미스 환경에서 유연하게 배포 및 운영 가능
멀티 클라우드 : AWS, Azure, GCP 등 여러 클라우드에서 애플리케이션과 데이터를 배포 및 관리
온프레미스 : 조직의 자체 서버에서 데이터와 애플리케이션을 운영

#### 3. 보안이 중요한 환경
민감 데이터 처리 및 높은 격리가 필요한 작업

#### 4. 이기종 환경에서 애플리케이션 실행
서로 다른 OS나 커널 버전이 필요한 애플리케이션은 VM을 활용하고, 동일한 VM 내에서 여러 컨테이너를 실행

#### 5. 테스트 및 개발 환경, 운영 환경 분리
개발, 테스트 환경은 VM에서 분리하고, 운영 환경은 컨테이너로 통합

### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/
-----

## Image

**이미지(Image)** : 컨테이너를 실행하는 데 필요한 애플리케이션, 실행 환경, 라이브러리, 설정 파일 등을 포함하는 표준화된 패키지

### 이미지의 원칙
#### 1. 이미지는 수정정할 수 없음
새 이미지를 만들거나 그 위에 변경 사항을 추가할 수만 있음

#### 2. 컨테이너 이미지는 레이어로 구성

### 컨테이너와 이미지의 차이
| **항목**         | **Docker 이미지**                                     | **Docker 컨테이너**                               |
|:-------------------|:-------------------------------------------------------:|:--------------------------------------------------:|
| **정의**         | 컨테이너 실행에 필요한 파일과 설정을 담은 템플릿         | 이미지를 실행한 결과로 동작 중인 환경             |
| **상태**         | 읽기 전용, 변경 불가                                   | 실행 중이며 변경 가능 (읽기/쓰기 레이어 포함)     |
| **사용 목적**     | 컨테이너 생성의 청사진 제공                           | 애플리케이션 실행                                 |
| **생명 주기**     | 지속적 (저장소에 저장 가능)                           | 일시적 (종료 시 삭제 가능)                       |

 
### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/

-----

## Registry

**이미지 레지스터리(Image Registry)** : 컨테이너 이미지를 저장하고 공유하기 위한 중앙 집중화된 곳

### Registry와 Repository의 차이
| **항목**          | **Registry**                                                   | **Repository**                                               |
|--------------------|---------------------------------------------------------------|-------------------------------------------------------------|
| **정의**          | Docker 이미지를 저장하고 관리하는 중앙 저장소                     | Registry 안에 포함된 개별 프로젝트 단위의 이미지 컬렉션         |
| **역할**          | 여러 Repository를 관리                                          | 특정 애플리케이션 버전의 Docker 이미지 모음                   |
| **구성**          | 여러 Repository로 구성                                          | 태그(tag)로 버전 관리된 Docker 이미지들의 모음                 |
| **예시**          | Docker Hub, AWS ECR, GitHub Container Registry                 | `library/nginx` (Nginx 이미지 Repository)                   |
| **접근 방식**      | `docker pull <registry>/<repository>:<tag>`                   | `docker pull <repository>:<tag>`                            |
| **범위**          | Registry는 전체 저장소의 개념                                   | Repository는 개별 애플리케이션 이미지의 저장소                 |

### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/
#### 1. Docker Hub에 Repository 만들기
#### 2. 이미지 빌드
```shell
# 샘플 코드 가져오기기
git clone https://github.com/dockersamples/helloworld-demo-node
cd helloworld-demo-node

# Docker 이미지 빌드
docker build -t <YOUR_DOCKER_USERNAME>/docker-quickstart .
```
#### 3. 이미지를 테스트할 컨테이너에 시작
```shell
docker run -d -p 8080:8080 <YOUR_DOCKER_USERNAME>/docker-quickstart 
```
브라우저에서 http://localhost:8080을 방문하여 컨테이너가 작동하는지 확인

#### 4. Docker 이미지에 태그를 지정 및 푸시
Docker 태그를 사용하면 이미지에 레이블을 지정하고 버전을 지정할 수 있음
```shell
docker tag <YOUR_DOCKER_USERNAME>/docker-quickstart <YOUR_DOCKER_USERNAME>/docker-quickstart:1.0 
docker push <YOUR_DOCKER_USERNAME>/docker-quickstart:1.0
```

#### 5. Docker Hub 저장소 - Tags에서 확인 가능

-----

## Docker Compose
**하나의 컨테이너는 한 가지의 일을 잘 해야 한다.**
하지만 개발을 하면서 데이터 베이스, 메시지 큐 등등 다양한 다른 서비스를 실행하기 위해 **여러 컨테이너**를 실행해야 함
Docker Compose를 사용하면 모든 컨테이너와 해당 구성을 **단일 YAML 파일**에 정의할 수 있음
이 파일을 코드 리포지토리에 포함하면 리포지토리를 복제하는 모든 사람이 단일 명령으로 시작하고 실행할 수 있음

### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/

-----

# Building Images

https://docs.docker.com/get-started/docker-concepts/building-images/

## Understanding the image layers

https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/

## Writing a Dockerfile

https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/

## Build, tag, and publish an image

https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/

## Using the build cache

https://docs.docker.com/get-started/docker-concepts/building-images/using-the-build-cache/

## Multi-stage build

https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/

# Running Containers

## Publishing and exposing ports

https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/

## Overriding container defaults

https://docs.docker.com/get-started/docker-concepts/running-containers/overriding-container-defaults/

## Persisting container data

https://docs.docker.com/get-started/docker-concepts/running-containers/persisting-container-data/

## Sharing local files with containers

https://docs.docker.com/get-started/docker-concepts/running-containers/sharing-local-files/

## Multi-container applications

https://docs.docker.com/get-started/docker-concepts/running-containers/multi-container-applications/
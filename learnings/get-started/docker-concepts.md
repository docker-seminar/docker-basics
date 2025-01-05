# Docker Concepts

# The Basics

## Container

**컨테이너(Container)** : 애플리케이션과 그 실행에 필요한 모든 파일, 라이브러리, 설정을 포함하는 독립적이고 가벼운 실행 환경

### 컨테이너의 주요 특징
#### 1. 격리 실행
각 컨테이너는 독립적으로 실행되며, 호스트 시스템 및 다른 컨테이너와 간섭 없이 동작
#### 2. 경량화
실행에 필요한 최소한의 구성만 포함
#### 3. 이식성
데이터 센터, 클라우드 등 다양한 환경에서 동일한 방식으로 작동
#### 4. 이미지 기반
컨테이너는 이미지 기반으로 생성
일관된 실행 환경을 제공

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
이처럼 다양한 플랫폼에서 애플리케이션 배포 가능

#### 3. 보안이 중요한 환경
민감 데이터 처리 및 높은 격리가 필요한 작업

#### 4. 이기종 환경에서 애플리케이션 실행
서로 다른 OS나 커널 버전이 필요한 애플리케이션은 VM을 활용하고, 동일한 VM 내에서 여러 컨테이너를 실행

#### 5. 테스트 및 개발 환경, 운영 환경 분리
개발, 테스트 환경은 VM에서 분리하고, 운영은 컨테이너로 관리

### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/
-----

## Image

**이미지(Image)** : 컨테이너를 실행하는 데 필요한 애플리케이션, 실행 환경, 라이브러리, 설정 파일 등을 포함하는 표준화된 패키지

### 이미지의 원칙
#### 1. 이미지는 수정할 수 없음
새 이미지를 만들거나 그 위에 변경 사항을 추가할 수만 있음

#### 2. 컨테이너 이미지는 레이어로 구성
이미지는 여러 레이어로 이루어져 있으며, 레이어는 캐싱 및 재사용 가능

### 컨테이너와 이미지의 차이
| **항목**         | **Docker 이미지**                                     | **Docker 컨테이너**                               |
|:-------------------|:-------------------------------------------------------:|:--------------------------------------------------:|
| **정의**         | 컨테이너 실행에 필요한 파일과 설정을 담은 템플릿         | 이미지를 실행한 결과로 동작 중인 환경             |
| **상태**         | 읽기 전용, 변경 불가                                   | 실행 중이며 변경 가능 (읽기/쓰기 레이어 포함)     |
| **사용 목적**     | 컨테이너 생성의 청사진 제공                           | 애플리케이션 실행 환경 제공                             |
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
| **역할**          | 여러 Repository를 관리                                          | 특정 애플리케이션의 Docker 이미지 모음                   |
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

### 단일 서비스 관리
각 컨테이너는 특정 역할을 수행

### 멀티 컨테이너 구성
데이터베이스, 메시지 큐, 캐시 등 연관 서비스 컨테이너를 통합 관리리

### 이식성
Docker Compose를 사용하면 모든 컨테이너와 해당 구성을 **단일 YAML 파일**에 정의할 수 있음
이 파일을 코드 리포지토리에 포함하여 리포지토리를 복제하는 모든 사람에게 일관된 환경을 제공

### 실습
https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/

-----

# Building Images

https://docs.docker.com/get-started/docker-concepts/building-images/

## Understanding the image layers

### 이미지 레이어
컨테이너 이미지는 레이어로 구성되며 이미 생성된 이미지의 레이어는 변경할 수 없음
각 레이어에는 파일 시스템 변경 사항 세트로 구성

#### 1. 첫 번째 레이어
기본 명령과 apt와 같은 **패키지 관리자 설치**

#### 2. 두 번째 레이어
종속성 관리를 위한 **Python 런타임과 pip를 설치**

#### 3. 세 번째 레이어
애플리케이션의 특정 requirements.txt **파일을 복사**

#### 4. 네 번째 레이어
해당 애플리케이션의 특정 종속성을 설치

#### 5. 다섯 번째 레이어
애플리케이션의 실제 소스 코드를 복사

### 이미지 레이어의 유용성
레이어를 이미지 간에 **재사용 가능**
예를 들어, 다른 Python 애플리케이션을 만들고 싶다고 가정해 보겠습니다. 레이어링 덕분에 동일한 Python 기반을 활용할 수 있습니다. 이렇게 하면 **빌드가 더 빨라지고 이미지를 배포하는 데 필요한 저장 공간과 대역폭이 줄어듦**
레이어를 사용하면 다른 레이어의 기본 레이어를 재사용하여 이미지를 확장하고, 애플리케이션에 필요한 데이터만 추가할 수 있음

### 레이어를 쌓는 방법
레이어링은 콘텐츠 주소 지정 스토리지와 유니온 파일 시스템을 통해 가능
유니온 파일 시스템이 생성되면 이미지 레이어 외에도 실행 중인 컨테이너를 위해 특별히 디렉토리가 생성
이를 통해 컨테이너는 파일 시스템을 변경하는 동시에 원래 이미지 레이어는 그대로 유지할 수 있음
동일한 기본 이미지에서 여러 컨테이너를 실행할 수 있음음

#### 1. 각 레이어가 다운로드된 후에는 호스트 파일 시스템의 자체 디렉토리에 압축해제

#### 2. 이미지에서 컨테이너를 실행하면 각 레이어가 서로 쌓여서 새롭고 통합된 뷰가 생성되는 유니온 파일 시스템이 생성

#### 3. 컨테이너가 시작되면 루트 디렉토리는 .을 사용하여 이 통합 디렉토리의 위치로 설정

### 실습
https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/

-----

## Writing a Dockerfile

### Dockerfile의 정의
**Dockerfile**은 컨테이너 이미지를 만드는 데 사용되는 텍스트 기반 문서
실행할 명령, 복사할 파일, 시작 명령 등에 대한 이미지 빌더에 대한 지침을 제공

### Dockerfile의 일반적인 지침
**FROM <image>**: 빌드가 확장할 **기본 이미지를 지정**
**WORKDIR <path>**: 파일이 복사되고 명령이 실행되는 **이미지의 "작업 디렉토리" 또는 경로를 지정**
**COPY <host-path> <image-path>**: 빌더에게 호스트에서 **파일을 복사**하여 컨테이너 이미지에 넣으라고 지시
**RUN <command>**: 빌더에게 지정된 **명령을 실행**하라고 지시
**ENV <name> <value>**: 실행 중인 컨테이너가 사용할 환경 변수를 설정
**EXPOSE <port-number>**: 이미지가 노출하고자 하는 포트를 나타내는 구성을 이미지에 설정
**USER <user-or-uid>**: 이후의 모든 명령어에 대한 기본 사용자를 설정
**CMD ["<command>", "<arg1>"]**: 이미지를 사용하는 **컨테이너가 실행할 기본 명령을 설정**

### Dockerfile의 예시
예시 : Dockerfile은 Python 애플리케이션을 위한 Docker 이미지를 빌드
```bash
# 기본 이미지 설정
FROM python:3.8-slim

# 컨테이너 내부에서 /app이라는 디렉토리를 작업 디렉토리로 지정
# 이후 실행되는 모든 명령어는 이 디렉토리를 기준으로 동작
WORKDIR /app

# 호스트 시스템(로컬)의 requirements.txt 파일을 컨테이너 내부의 현재 작업 디렉토리로 복사
COPY requirements.txt .

# 종속성 설치 : 컨테이너 내부에서 파이썬 패키지 관리자인 pip을 사용하여 해당 파일에 명시된 모든 패키지를 설치
# -r 옵션을 통해 설치 목록을 읽는 데 사용
RUN pip install -r requirements.txt

# 현재 디렉토리에 있는 모든 파일과 폴더를 컨테이너의 현재 작업 디렉토리로 복사
# .dockerignore 파일에 명시된 항목은 복사에서 제외
COPY . .

# 컨테이너 실행 시 기본 명령어 설정 : app.py를 Python으로 실행
# CMD는 컨테이너 실행 시점에 동작
CMD ["python", "app.py"]
```

### 실습
https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/

-----

## Build, tag, and publish an image

### 이미지 흐름
#### 이미지 구축
**Dockerfile**에 정의된 명령어를 실행하여 새 Docker 이미지를 만드는 프로세스
```shell
# 현재 디렉토리에서 Dockerfile을 읽고 이미지를 생성
docker build .
```
이 경우에 다음과 같은 출력을 생성
```shell
[+] Building 3.5s (11/11) FINISHED                                              docker:desktop-linux
 => [internal] load build definition from Dockerfile                                            0.0s
 => => transferring dockerfile: 308B                                                            0.0s
 => [internal] load metadata for docker.io/library/python:3.12                                  0.0s
 => [internal] load .dockerignore                                                               0.0s
 => => transferring context: 2B                                                                 0.0s
 => [1/6] FROM docker.io/library/python:3.12                                                    0.0s
 => [internal] load build context                                                               0.0s
 => => transferring context: 123B                                                               0.0s
 => [2/6] WORKDIR /usr/local/app                                                                0.0s
 => [3/6] RUN useradd app                                                                       0.1s
 => [4/6] COPY ./requirements.txt ./requirements.txt                                            0.0s
 => [5/6] RUN pip install --no-cache-dir --upgrade -r requirements.txt                          3.2s
 => [6/6] COPY ./app ./app                                                                      0.0s
 => exporting to image                                                                          0.1s
 => => exporting layers                                                                         0.1s
 => => writing image sha256:9924dfd9350407b3df01d1a0e1033b1e543523ce7d5d5e2c83a724480ebe8f00    0.0s
```
**exporting layers** : 이미지를 구성하는 레이어를 저장
**sha256:...** : 생성된 이미지의 고유 식별자(ID)

이전 출력을 사용하면 참조된 이미지로 컨테이너를 시작할 수 있음
```bash
docker run sha256:9924dfd9350407b3df01d1a0e1033b1e543523ce7d5d5e2c83a724480ebe8f00
```
하지만 이를 매번 기억하기는 매우 힘든 일
따라서 이미지에 태그를 지정할 수 있음

#### 이미지 태그 지정
Docker 이미지에 이름과 버전을 부여
이를 통해 이미지를 어디에 배포할 수 있는지도 결정됨
##### 이미지 이름의 구조
```bash
[HOST[:PORT_NUMBER]/]PATH[:TAG]
```
###### HOST
이미지가 저장될 레지스트리 호스트 주소
기본값은 docker.io
###### PORT_NUMBER
레지스토리 포트 번호 (필요 시 지정)
###### PATH
이미지 경로
Docker Hub인 경우 [NAMESPACE/]REPOSITORY로 구성
이때 NAMESPACE가 지정되지 않으면 libraryDocker Official Images의 네임스페이스가 사용됨
###### TAG
이미지의 다른 버전들을 구분하기 위한 사용자 지정 식별자
기본값은 latest

태그를 지정하여 빌드
```bash
docker build -t my-username/my-image .
```
이미 생성된 이미지에 태그 추가
```bash
docker image tag my-username/my-image another-username/another-image:v1
```
my-username/my-image : 기존 이미지 이름
another-username/another-image:v1 : 새 태그 이름

#### 이미지 게시 
새로 생성된 이미지를 레지스토리에 푸시
```bash
docker push my-username/my-image
```

태그가 포함된 이미지 업로드
```bash
docker push my-repo/my-image:1.0
```
이미지를 업로드하면 레지스트리에서 해당 이미지와 태그를 확인할 수 있음

### 이미지 빌드 & 태그 지정 & 배포
```bash
# 이미지 빌드 및 태그 지정
docker build -t my-image:latest .

# 추가 태그 지정
docker tag my-image:latest my-repo/my-image:1.0

# 이미지 레지스토리에 업로드
docker push my-repo/my-image:1.0
```

### 추가 태그 정보
#### 1. 태그는 중요한 메타데이터
태그는 이미지의 버전을 명시적으로 구분하며, 배포 및 관리의 편리성을 제공

#### 2. 다중 태그 지원
하나의 이미지에 여러 태그를 부여하여 다른 목적에 맞게 활용할 수 있음

#### 3. 레지스토리 호환성
Docker Hub뿐 아니라 AWS ECR, Google Container Registry 등 다양한 레지스토리를 사용할 수 있음

### 실습
https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/

-----

## Using the build cache
**빌드 캐시** : Docker는 이미지를 빌드할 때 Dockerfile의 각 명령어를 실행하고 결과를 레이어 단위로 저장함 -> 다음 빌드 시, 이전에 생성한 레이어를 다시 사용할 수 있는지 확인
**이전 빌드의 결과를 재사용**하여 반복 작업을 줄이고, 빌드 시간을 단축
캐시를 효율적으로 사용하기 위해서는 **캐시 무효화의 이해**가 중요

### 캐시 사용의 기본 원리
#### Dockerfile의 명령어
동일한 명령어인지 확인

#### 명령어의 입력값
해당 명령어에 사용된 파일이나 환경 변수의 변경 여부를 확인

#### 명령어의 순서
Dockerfile의 명령어 순서가 캐시 일관성을 보장

### 캐시 무효화 되는 상황
#### RUN 명령어
Docker는 모든 변경 사항을 감지함
Dockerfile에 대한 run 명령어가 새로운 입력값이나 다른 결과를 생성하면 빌드 캐시가 무효화됨

#### COPY / ADD 명령어
Docker는 복사할 파일의 내용(해시값), 권한, 타임스탬프를 확인하여 변경 사항을 감지
콘텐츠나 권한과 같은 속성의 변경 등으로 Docker은 캐시를 무효화할 수 있음

#### 연쇄성
한 레이어가 무효화되면 그 뒤에 있는 모든 레이어가 다시 빌드됨
이는 빌드 프로세스가 동기화되고 불일치가 방지됨
##### 예시
```bash
COPY requirements.txt /app/
RUN pip install -r requirements.txt
```
requirements.txt가 변경되면 COPY 명령어가 무효화되고, 이어지는 RUN 명령어도 무효화됨

### 캐시 활용
#### 변경 사항 최소화
불필요한 파일이나 자주 변경되는 파일을 빌드 과정에서 제외
.dockerignore 파일을 활용할 수 있음

#### 명령 순서 최적화
빈번히 변경되는 명령은 마지막에 배치
##### 예시
```bash
# 변경되지 않는 패키지를 먼저 설치
COPY requirements.txt /app/
RUN pip install -r requirements.txt

# 애플리케이션 파일은 나중에 복사
COPY . /app/
```
requirements.txt가 변경되지 않으면 pip install 레이어가 캐시로 재사용됨

#### 외부 데이터의 안정성 확보
외부 네트워크 요청(RUN apt-get update)은 항상 최신 데이터를 가져오기 때문에 캐시를 활용하기 어려움
##### 해결책
특정 버전(예: apt-get install -y curl=7.68.0)을 사용하거나, 네트워크 의존성을 최소화

### 실습
https://docs.docker.com/get-started/docker-concepts/building-images/using-the-build-cache/

-----

## Multi-stage build
### Single-stage build
단일 컨테이너에서 모든 작업(의존성 다운로드, 코드 컴파일, 애플리케이션 패키징)을 하나의 Dockerfile에서 실행하며, 단일 이미지에 포함됨
빌드 도구나 불필요한 파일이 최종 이미지에 포함될 수 있음
공간 비효율 및 보안 취약성이 발생

### Multi-stage build
Docker 이미지를 빌드할 때 여러 단계를 사용하여 빌드 작업과 런타임 작업을 분리하여 최종 이미지를 효율적이고 최적화된 상태로 만드는 방법
빌드 도구는 중간 단계에서만 사용되며, 최종 이미지에는 필요한 결과물만 포함됨
이를 통해 공간 효율성과 보안, 빌드 과정의 유연성을 크게 개선할 수 있음

### 인터프리터 언어에서 다중 단계 빌드
코드와 의존성만 복사하여 런타임 이미지에서 실행할 수 있음
#### 예시
```bash
# Stage 1: Build environment
FROM node:14 AS build-stage
WORKDIR /app

COPY package.json package-lock.json ./
RUN npm install

COPY . .

# Stage 2: Runtime environment
FROM node:14-slim AS runtime-stage
WORKDIR /app

COPY --from=build-stage /app .

CMD ["npm", "start"]
```
**build-stage** : npm install 등 빌드와 관련된 작업을 처리
**runtime-stage** : build-stage에서 생성된 결과물만 복사하여 실행에 필요한 최소한의 파일만 포함

### 컴파일 언어에서 다중 단계 빌드
한 단계에서 이미 컴파일된 binary만을 최종 런타임 이미지에 복사할 수 있음
#### 예시
```bash
# Stage 1: Build environment
FROM maven:3.8.5-openjdk-17 AS build-stage
WORKDIR /app

COPY pom.xml .
RUN mvn dependency:resolve

COPY src ./src
RUN mvn package

# Stage 2: Runtime environment
FROM openjdk:17-slim AS runtime-stage
WORKDIR /app

COPY --from=build-stage /app/target/my-app.jar ./app.jar

CMD ["java", "-jar", "app.jar"]
```
**build-stage** : Maven 이미지를 사용하여 애플리케이션을 빌드하고 my-app.jar 파일을 생성
**runtime-stage** : 빌드된 JAR 파일만 런타임 이미지에 복사하여 애플리케이션을 실행

### 다중 단계 빌드 구조 예시
```bash
# Stage 1: Build Environment
FROM builder-image AS build-stage 
# Install build tools (e.g., Maven, Gradle)
# Copy source code
# Build commands (e.g., compile, package)

# Stage 2: Runtime environment
FROM runtime-image AS final-stage  
#  Copy application artifacts from the build stage (e.g., JAR file)
COPY --from=build-stage /path/in/build/stage /path/to/place/in/final/stage
# Define runtime configuration (e.g., CMD, ENTRYPOINT) 
```
**Stage 1 (build-stage)**
애플리케이션을 컴파일하는 데 필요한 빌드 도구가 있는 기본 이미지를 사용하여 소스를 컴파일하거나 패키징함

**Stage 2 (final-stage)**
애플리케이션을 실행하는 데 적합한 더 작은 기본 이미지를 사용
JAR file같은 컴파일된 작업물만 복사하여 실행에 필요한 환경만 포함됨
애플리케이션을 실행시키기 위한 환경 설정들을 정의함

### 실습
https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/

-----

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
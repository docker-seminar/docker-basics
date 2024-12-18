# Docker Concepts

# The Basics

## Container

- Docker Container 는 애플리케이션과 그 종속성을 함께 패키징하여 격리된 환경에서 실행할 수 있는 기술
    - **패키징**: 애플리케이션과 실행에 필요한 모든 요소를 하나의 독립된 단위로 묶는 과정을 의미
- 개발, 테스트, 배포 환경 간의 일관성을 유지하고, 시스템 간의 충돌을 방지

### 주요 특징

- **Self-contained**: 각 컨테이너는 실행에 필요한 모든 것을 포함하여 호스트 시스템에 사전 설치된 종속성에 의존하지 않음
- **Isolated**: 컨테이너는 독립된 환경에서 실행되어 호스트 및 다른 컨테이너에 최소한의 영향을 미치며, 애플리케이션의 보안을 강화
- **Independent**: 각 컨테이너는 독립적으로 관리되며, 하나의 컨테이너를 삭제해도 다른 컨테이너에 영향을 주지 않음
- **Portable**: 컨테이너는 개발 환경, 데이터 센터, 클라우드 등 어디서나 동일하게 실행될 수 있음

### 컨테이너와 가상 머신(Virtual Machine)의 비교:

| 특징    | 컨테이너                                         | 가상 머신(VM)                                  |
|-------|----------------------------------------------|--------------------------------------------|
| 구성 요소 | 애플리케이션과 필요한 라이브러리만 포함하며, 호스트 OS의 커널을 공유      | 전체 운영 체제, 커널, 하드웨어 드라이버, 프로그램 및 애플리케이션을 포함 |
| 오버헤드  | 경량으로, 더 적은 인프라에서 더 많은 애플리케이션을 실행 가능          | 각 VM이 전체 OS를 포함하므로, 더 많은 리소스와 오버헤드가 발생     |
| 격리 수준 | 프로세스 수준에서 격리되어 있으며, 호스트와 다른 컨테이너에 최소한의 영향을 줌 | 하드웨어 수준에서격리되어 있ㅇ며, 더 강력한 격리를 제공            |
| 부팅 시간 | 빠른 시작과 중지가 가능                                | 전체 OS를 부팅해야 하므로, 시작과 중지에 더 많은 시간 소요        |

## 이미지

### 도커 이미지 란?

도커 이미지는 컨테이너 실행에 필요한 파일, 라이브러리, 설정 등을 포함한 표준화된 패키지

### 이미지의 주요 특징

- 불변성: 한 번 생성된 이미지는 수정할 수 없으며, 변경하려면 새로운 이미지를 생성해야함
- 레이어 구조: 이미지는 여러 레이어로 구성되며, 각 레이어는 파일 시스템의 변경 사항을 나타냄

### 이미지 활용

- 기존 이미지를 기반으로 새로운 이미지를 생성하여 애플리케이션의 종속성 추가나 코드 배포에 활용 가능

### 이미지 검색 및 다운로드

- Docker Hub: 퍼블릭 이미지 저장소로, 다양한 공식 이미지와 검증된 퍼블리셔의 이미지를 제공
- AWS ECR

### Docker Hub

| 컨텐츠 종류      | 설명                                     | 예시                 |
|-------------|----------------------------------------|--------------------|
| 공식 이미지      | 도커에서 관리하는 신뢰성 높은 이미지 모음                | Redis, Memcached 등 |
| 검증된 퍼블리셔    | 도커에서 검증한 상용 퍼블리셔들이 제공하는 고품질 이미지        | MongoDB 등          |
| 도커 후원 오픈 소스 | 도커의 오픈소스 프로그램을 통해 후원받는 프로젝트에서 제공하는 이미지 | Alpine Linux 등     |

## Registry

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/

## Docker Compose

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/

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
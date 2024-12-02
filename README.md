# Docker Basics

도커 기초 익히기

# How to learn

1. 한 주제에 대해 브랜치를 생성한다
   - 브랜치 이름은 다음과 같이 설정한다: 본인 이름/종류/브랜치 이름
   - 예시 브랜치 이름: sbk/docs/what-is-docker
   - sbk 가, 문서 작업 (주로 `.md` 파일), what-is-docker 내용 수정하는 브랜치
2. 해당 주제에 포함된 링크로 들어간다. (필요한 경우 브라우저의 번역 기능을 이용)
3. 마크다운을 이용해 페이지의 내용을 정리한다.
    - [깃허브 마크다운 안내](https://docs.github.com/ko/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) (
      한국어 설정 가능)
    - 리스트나 테이블 등 적극 활용하기
4. Commit, push 그리고 pull request 를 생성한다.

# What is Docker?

Docker 는 애플리케이션을 개발, 배포, 실행할 수 있는 오픈 플랫폼으로, 컨테이너라는 독립된 환경에서 애플리케이션을 실행합니다.
이를 통해 인프라와 애플리케이션을 분리하여 소프트웨어를 신속하게 제공할 수 있습니다.

## Docker 의 주요 구성 요소

| 구성 요소           | 설명                                                                         |
|-----------------|----------------------------------------------------------------------------|
| Docker Daemon   | dockerd 로 불리며, Docker API 요청을 수신하고 이미지, 컨테이너, 네트워크, 볼륨 등의 Docker 객체를 관리    |
| Docker Client   | docker 명령어를 통해 Docker Daemon 과 상호작용할 수 있는 주요 인터페이스                         |
| Docker Desktop  | Mac, Windows, 그리고 Linux 환경에서 컨테이너화된 애플리케이션과 마이크로서비스를 구축하고 공유할 수 있는 애플리케이션  |
| Docker Registry | Docker 이미지를 저장하는 공간으로, 기본적으로 Docker Hub 를 사용하며, 필요에 따라 개인 레지스트리를 운영할 수도 있음 |

## Docker 활용 사례

- 빠르고 일관된 애플리케이션 제공: 개발자들이 로컬 컨테이너 환경에서 코드를 작성하고, 이를 테스트 및 프로덕션 환경에 신속하게 배포할 수 있음
- 유연한 배포 및 확장: Docker 컨테이너는 로컬, 데이터 센터, 클라우드 등 다양한 환경에서 실행 가능하며, 비즈니스 요구에 따라 애플리케이션과 서비스를 실시간으로 확장하거나 축소할 수 있음
- 하드웨어 자원 효율성 증대: 경량의 컨테이너를 통해 동일한 하드웨어에서 더 많은 작업을 수행할 수 있어 비용 효율적인 운영이 가능하게 함

## Docker 의 기술적 기반

Docker 는 Go 언어로 작성되었으며, 리눅스 커널의 네임스페이스와 cgroups 등의 기능을 활용하여 컨테이너의 격리와 자원 제한을 구현함
이를 통해 애플리케이션은 독립된 환경에서 실행되며, 호스트 시스템과 다른 컨테이너로부터 격리됨

Docker 를 활용하면 애플리케이션 개발부터 배포까지의 과정을 효율적으로 관리하고, 다양한 환경에서 일관되게 애플리케이션을 실행할 수 있음

# Docker Concepts

## The Basics

### Container

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/

### Image

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/

### Registry

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/

### Docker Compose

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/

## Building Images

https://docs.docker.com/get-started/docker-concepts/building-images/

### Understanding the image layers

https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/

### Writing a Dockerfile

https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/

### Build, tag, and publish an image

https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/

### Using the build cache

https://docs.docker.com/get-started/docker-concepts/building-images/using-the-build-cache/

### Multi-stage build

https://docs.docker.com/get-started/docker-concepts/building-images/multi-stage-builds/

## Running Containers

### Publishing and exposing ports

https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/

### Overriding container defaults

https://docs.docker.com/get-started/docker-concepts/running-containers/overriding-container-defaults/

### Persisting container data

https://docs.docker.com/get-started/docker-concepts/running-containers/persisting-container-data/

### Sharing local files with containers

https://docs.docker.com/get-started/docker-concepts/running-containers/sharing-local-files/

### Multi-container applications

https://docs.docker.com/get-started/docker-concepts/running-containers/multi-container-applications/

# Dockerfile Reference

Dockerfile 작성
https://docs.docker.com/reference/dockerfile/#label

# Docker in GitHub

https://github.com/docker/build-push-action
https://github.com/docker/docker-credential-helpers
대충 깃허브 워크플로우에서 도커 쓰는 법

# buildx

https://github.com/docker/buildx

# Docker in Cloud: AWS ECS

ECS 로 도커 돌리는 법
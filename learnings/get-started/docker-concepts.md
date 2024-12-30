# Docker Concepts

# The Basics

## Container

컨테이너는 애플리케이션의 각 구성 요소를 위한 `독립된 프로세스`입니다.
각 구성 요소는 자신의 독립된 환경에서 실행되며, 당신의 컴퓨터에 있는 다른 모든 것과 완전히 격리되어 있습니다.

- 자체 포함(Self-contained)
  각 컨테이너는 작동에 필요한 모든 것을 포함하고 있어, 호스트 머신에 미리 설치된 종속성에 의존하지 않습니다.

- 격리(Isolated)
  컨테이너는 격리된 상태에서 실행되므로, 호스트 시스템 및 다른 컨테이너에 영향을 거의 미치지 않으며, 애플리케이션의 보안을 강화합니다.

- 독립성(Independent)
  각 컨테이너는 독립적으로 관리됩니다. 하나의 컨테이너를 삭제해도 다른 컨테이너에 영향을 주지 않습니다.

- 이식성(Portable)
  컨테이너는 어디에서나 실행될 수 있습니다! 개발 머신에서 실행되는 컨테이너는 데이터 센터나 클라우드의 어느 곳에서도 동일하게 작동합니다.

### 컨테이너와 가상 머신(VMs)의 차이점

가상 머신(VM)은 자체 커널, 하드웨어 드라이버, 프로그램, 애플리케이션을 포함한 완전한 운영 체제입니다.
단일 애플리케이션을 격리하기 위해 VM을 실행하는 것은 상당한 오버헤드를 초래합니다.

반면, 컨테이너는 애플리케이션 실행에 필요한 모든 파일을 포함한 독립된 프로세스일 뿐입니다.
여러 컨테이너를 실행하면 모두 동일한 커널을 공유하므로, 더 적은 인프라로 더 많은 애플리케이션을 실행할 수 있습니다.

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/

## Image

컨테이너 이미지는 컨테이너를 실행하는 데 필요한 모든 파일, 바이너리, 라이브러리, 구성 파일을 포함하는 `표준화된 패키지`입니다.

- 이미지는 불변(Immutable)이다
  이미지가 한 번 생성되면 수정할 수 없습니다.
  이미지를 수정하려면 새 이미지를 만들거나 기존 이미지 위에 변경 사항을 추가해야 합니다.

- 컨테이너 이미지는 레이어(Layer)로 구성된다
  각 레이어는 파일 시스템 변경 사항(파일 추가, 삭제 또는 수정)을 나타냅니다.

이 두 가지 원칙 덕분에 기존 이미지를 확장하거나 변경 사항을 추가할 수 있습니다.

### Finding Images

Docker Hub는 이미지를 저장하고 배포하기 위한 기본 글로벌 마켓플레이스입니다.

- Docker 공식 이미지(Docker Official Images)
  Docker가 선별한 저장소 세트로, 대부분의 사용자들이 시작점으로 사용하며, Docker Hub에서 가장 안전한 이미지 중 일부입니다.

- Docker 검증 퍼블리셔(Docker Verified Publishers)
  Docker에 의해 검증된 상업 퍼블리셔가 제공하는 고품질 이미지입니다.

- Docker 지원 오픈 소스(Docker-Sponsored Open Source)
  Docker의 오픈 소스 프로그램을 통해 Docker가 지원하는 오픈 소스 프로젝트가 게시하고 유지 관리하는 이미지입니다.

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/

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

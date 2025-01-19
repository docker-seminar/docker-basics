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

### Finding Images in Docker Hub

Docker Hub는 이미지를 저장하고 배포하기 위한 기본 글로벌 마켓플레이스입니다.

- Docker 공식 이미지(Docker Official Images)
  Docker가 선별한 저장소 세트로, 대부분의 사용자들이 시작점으로 사용하며, Docker Hub에서 가장 안전한 이미지 중 일부입니다.

- Docker 검증 퍼블리셔(Docker Verified Publishers)
  Docker에 의해 검증된 상업 퍼블리셔가 제공하는 고품질 이미지입니다.

- Docker 지원 오픈 소스(Docker-Sponsored Open Source)
  Docker의 오픈 소스 프로그램을 통해 Docker가 지원하는 오픈 소스 프로젝트가 게시하고 유지 관리하는 이미지입니다.

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/

## Registry

이미지 레지스트리는 컨테이너 이미지를 저장하고 공유하기 위한 `중앙 집중화된 저장소`입니다.
레지스트리는 공개(Public) 또는 비공개(Private)로 운영될 수 있습니다.
Docker Hub는 누구나 사용할 수 있는 공개 레지스트리이며, 기본 레지스트리로 설정되어 있습니다.

Docker Hub 외에도 다양한 컨테이너 레지스트리가 제공됩니다.

- Amazon Elastic Container Registry (ECR)
- Azure Container Registry (ACR)
- Google Container Registry (GCR)

로컬 시스템이나 조직 내에서 실행할 수 있는 개인 레지스트리(Private Registry)도 운영할 수 있습니다.

- Harbor
- JFrog Artifactory
- GitLab Container Registry

### 레지스트리(Registry)와 리포지토리(Repository)의 차이점

- 레지스트리(Registry)
  컨테이너 이미지를 저장하고 관리하는 중앙 집중화된 위치입니다.

- 리포지토리(Repository)
  레지스트리 안에서 관련된 컨테이너 이미지를 모아놓은 컬렉션입니다.
  프로젝트별로 이미지를 정리하는 폴더와 같은 개념입니다. 하나의 리포지토리는 하나 이상의 컨테이너 이미지를 포함합니다.

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-registry/

## Docker Compose

Docker Compose를 사용하면 `모든 컨테이너와 그 설정`을 `단일 YAML 파일에 정의`할 수 있습니다.
이 파일을 코드 저장소에 포함하면, 저장소를 복제(clone)한 모든 사람이 단일 명령어로 실행 환경을 설정할 수 있습니다.

이는 더 복잡한 작업, 예를 들어 데이터베이스, 메시지 큐, 캐시 또는 다양한 서비스를 실행하려는 상황에 유용합니다.
각 컨테이너가 하나의 작업만 수행하고 그것을 잘 수행할 수 있도록 합니다.

Docker Compose는 실행 중인 컨테이너를 정의하는 선언형 도구입니다.
변경 사항이 있다면 docker compose up 명령어를 다시 실행하면, Compose가 파일의 변경 사항을 지능적으로 반영합니다.

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-docker-compose/

# Building Images

https://docs.docker.com/get-started/docker-concepts/building-images/

## Understanding the image layers

컨테이너 이미지는 여러 계층(layer)으로 구성되며, 계층은 한 번 생성되면 변경할 수 없습니다(불변성).

### Image Layers

이미지의 각 계층은 파일 시스템의 변경 사항을 포함합니다.
이 변경 사항은 추가, 삭제 또는 수정이 될 수 있습니다.

1. 첫 번째 계층: 기본 명령어와 패키지 관리자를 추가합니다(예: apt).
2. 두 번째 계층: Python 런타임과 pip을 설치하여 의존성 관리가 가능하게 합니다.
3. 세 번째 계층: 애플리케이션의 특정 requirements.txt 파일을 복사합니다.
4. 네 번째 계층: 애플리케이션의 특정 의존성들을 설치합니다.
5. 다섯 번째 계층: 실제 애플리케이션의 소스 코드를 복사합니다.

각 계층은 서로 다른 변경 사항을 포함하고 있으며,
이러한 계층들은 하나씩 쌓여서 최종적으로 컨테이너가 사용할 수 있는 파일 시스템을 구성하게 됩니다.

이로 인해 불필요한 중복을 줄이고, 여러 애플리케이션에서 공통된 부분을 효율적으로 재사용할 수 있어,
이미지 관리와 배포가 더 효율적이고 경제적으로 이루어집니다.

### Stacking the Layers

계층화는 콘텐츠 주소 지정 저장소(content-addressable storage)와 유니온 파일 시스템(union filesystem) 덕분에 가능해집니다.

1. 각 계층이 다운로드되면, 해당 계층은 호스트 파일 시스템의 별도의 디렉토리에 추출됩니다.
2. 이미지를 기반으로 컨테이너를 실행하면, 유니온 파일 시스템이 생성되어 계층들이 서로 위에 쌓이게 됩니다.
   이렇게 하면 새로운 통합된 뷰가 만들어집니다.
3. 컨테이너가 시작될 때, 루트 디렉토리는 이 통합된 디렉토리 위치로 설정됩니다.
   이를 위해 chroot 명령어가 사용됩니다.

유니온 파일 시스템이 생성될 때, 이미지 계층 외에도 실행 중인 컨테이너를 위한 디렉토리가 생성됩니다.
이를 통해 컨테이너는 파일 시스템 변경을 할 수 있으면서, 원본 이미지 계층은 그대로 유지됩니다.
이 덕분에 동일한 기본 이미지를 기반으로 여러 컨테이너를 실행할 수 있게 됩니다.
이 방식은 여러 컨테이너가 동일한 이미지에서 시작되면서도 각각 독립적으로 파일 시스템을 수정할 수 있도록 해 줍니다.

https://docs.docker.com/get-started/docker-concepts/building-images/understanding-image-layers/

## Writing a Dockerfile

Dockerfile은 컨테이너 이미지를 생성하는 데 사용되는 텍스트 기반의 문서입니다.

```dockerfile
FROM python:3.12
WORKDIR /usr/local/app

# 애플리케이션 의존성 설치
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# 소스 코드 복사
COPY src ./src
EXPOSE 5000

# 루트 사용자 대신 애플리케이션 사용자 설정
RUN useradd app
USER app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

이 Dockerfile은 Python 3.12 이미지를 기본 이미지로 사용하고,
애플리케이션의 의존성을 설치하고 소스 코드를 복사한 후,
컨테이너가 실행될 때 필요한 명령을 설정합니다.

### 자주 사용하는 명령어들

| 명령어                        | 설명                                                                 |
| ----------------------------- | -------------------------------------------------------------------- |
| FROM <image>                  | 빌드가 확장할 기본 이미지를 지정합니다.                              |
| WORKDIR <path>                | 파일이 복사되고 명령어가 실행될 작업 디렉토리를 지정합니다.          |
| COPY <host-path> <image-path> | 호스트에서 파일을 복사하여 컨테이너 이미지의 지정된 경로에 넣습니다. |
| RUN <command>                 | 지정된 명령어를 실행합니다.                                          |
| ENV <name> <value>            | 실행 중인 컨테이너가 사용할 환경 변수를 설정합니다.                  |
| EXPOSE <port-number>          | 이미지가 노출하고 싶은 포트를 설정합니다.                            |
| USER <user-or-uid>            | 이후의 명령어들이 실행될 기본 사용자를 설정합니다.                   |
| CMD ["<command>", "<arg1>"]   | 이 이미지를 사용하는 컨테이너가 실행할 기본 명령을 설정합니다.       |

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

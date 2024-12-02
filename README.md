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

https://docs.docker.com/get-started/docker-overview/

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
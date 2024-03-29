<a href="../README.md">
<button>⬅Back</button>
</a>


# Travis CI
# Travis + Docker + k8s (kubectl)
Imagine we have 2 microservices, one reverse proxy and a frontend to deploy. In our case we need to create docker images, push all to `Docker Hub` and after deploy all containers app in `EKS with kubectl`. We can create a Travis CI like the travis yaml fille below. We will use `docker-compose` instead of docker simple command.
```yaml
# .travis.yml file example
language: minimal

services: docker

env:
  - DOCKER_COMPOSE_VERSION=1.23.2

before_install:
  - docker -v && docker-compose -v
  - sudo rm /usr/local/bin/docker-compose
  - curl -L https://github.com/docker/compose/releases/download/${DOCKER_COMPOSE_VERSION}/docker-compose-`uname -s`-`uname -m` > docker-compose
  - chmod +x docker-compose
  - sudo mv docker-compose /usr/local/bin
  - curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
  - chmod +x ./kubectl
  - sudo mv ./kubectl /usr/local/bin/kubectl
  - mkdir ${HOME}/.kube
  - echo "$KUBE_CONFIG" | base64 --decode > ${HOME}/.kube/config # include to travis console env variable :cat ${HOME}/.kube/config | base64 | pbcopy
  - echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin # set Docker username and password in Travis console
  - echo 'dockerhub credentials configured'
install:
  - docker-compose -f udacity-deployment/docker/docker-compose-build.yaml build --parallel 
  - docker-compose -f udacity-deployment/docker/docker-compose-build.yaml push

script:
  - kubectl get pods
  - kubectl set image deployments/backend-feed backend-feed=juadel/udagram-feed-v2:latest
  - kubectl set image deployments/backend-user backend-user=juadel/udagram-user-v2:latest
  - kubectl set image deployments/frontend frontend=juadel/udagram-frontend-v2:latest
  - kubectl set image deployments/reverseproxy reverseproxy=juadel/reverseproxy-v2:latest
```
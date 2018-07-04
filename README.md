# Firebase deploy image

[![Docker build](https://img.shields.io/docker/automated/mikangali/angular.svg)](https://hub.docker.com/r/mikangali/angular)


Angular + Firebase ci-deploy image with nodejs and some npm packages :

* firebase-tools
* angular cli

## Sample usage for gitlab ci

```yml
image: mikangali/firebase

variables:
  PROJ_STAGING : "staging-project"
  PROJ_PRODUCTION : "prod-prejct"

deploy to staging:
  environment: staging
  script:
    - ng build --output-path app
    - firebase use $PROJ_STAGING --token "$FIREBASE_TOKEN"
    - firebase deploy --token "$FIREBASE_TOKEN"
  only:
  - master

deploy to production:
  environment: production
  script:
    - ng build --output-path app
    - firebase use $PROJ_PRODUCTION --token "$FIREBASE_TOKEN"
    - firebase deploy --token "$FIREBASE_TOKEN"
  only:
  - production
```

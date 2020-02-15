# log8371 : Integration continue avec Travis CI

## 1. Fork elasticsearch
commencer par Forking elasticsearch repo : https://github.com/elastic/elasticsearch.

## 2. Clone votre repo: 

```
git clone https://github.com/github username/elasticsearch.git
```

## 3. connectez-vous à travis-ci.org/ avec votre compte github.

![travis-ci.org](travis.png)

## 4 . créez votre fichier .travis.yml avec votre configuration et ajoutez-le au dossier elastichsearch sur votre environnement local. commit et push au master. 

Consulter la documentation de travis-ci pour plus d'info: https://docs.travis-ci.com/
### Exemple de .travis.yml : 

~~~
language: java
install: true


dist: trusty
jdk:
  - openjdk13
  - openjdk-ea


matrix:
  allow_failures:
    - jdk: openjdk-ea

branches:
  only:
  - master
  - v7.6.0
    

script:
  - ./gradlew --continue clean build --scan -s -p modules/

~~~

Par exemple, si vous souhaitez déployer sur heroku, vous pouvez ajouter ce qui suit à votre .travis.yml
~~~
deploy:
  provider: heroku
  api_key:
    secure: "YOUR ENCRYPTED API KEY"
~~~

see also : https://devcenter.heroku.com/articles/bonsai

## 


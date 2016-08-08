# Grails docker via sdkman

docker-compose.yml:
```
version: '2'
services:
 grails:
  image: marcelmaatkamp/docker-grails
  command: -reloading run-app
  volumes:
   - ./volumes/grails/admin:/app:rw
```

To develop:
```
docker-compose run --entrypoint '/bin/bash -s' --rm grails /bin/bash

$ rm -rf build/ (once only)
$ grails create-domain-class com.my.project.domain.SomeDomainClass
$ grails generate-all
$ grails -reloading run-app
$ .. 
$ (profit!)
```

To run:
```
docker-compose up -d grails
```

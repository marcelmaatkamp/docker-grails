# Grails docker via sdkman

The settings are in docker-compose.yml which makes a shared directory on the host:
```
version: '2'
services:
 grails:
  image: marcelmaatkamp/docker-grails
  command: -reloading run-app
  volumes:
   - ./volumes/grails/admin:/app:rw
```

To develop, start a single docker instance with bash, create and/or modify classes/views/etc, start/restart server and goto port http://localhost:8080 (rince and repeat):
```
docker-compose run --entrypoint '/bin/bash -s' --rm grails /bin/bash

$ rm -rf build/ (once only)
$ grails create-domain-class com.my.project.domain.SomeDomainClass
$ grails generate-all
$ grails -reloading run-app
$ .. 
$ (profit!)
```

If everything is ok, start the definitive container with:
```
docker-compose up -d grails
```

# local java development environment  [![Build Status](https://travis-ci.org/mrduguo/javadev.svg?branch=master)](https://travis-ci.org/mrduguo/javadev)


## Run


```bash

# ./gradlew
docker run -v /d:/d -v javadev:/root -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker --rm -it mrduguo/javadev

```

### Docker hub published tags

https://hub.docker.com/r/mrduguo/javadev/tags/



## Build


```bash

./gradlew

```

It will build the docker image with latest and versioned tags.

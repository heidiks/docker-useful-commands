# docker-useful-commands
* [Cleaning](#cleaning)
* [Push](#push)

### Cleaning
Delete all containers
```
docker rm $(docker ps -a -q)
````
 Delete all images
```
docker rmi $(docker images -q)
```

### Push
Login into a private registry
```
docker login PRIVATE_HOST
```

Tag and push
```
docker tag app:latest PRIVATE_HOST/app:latest
docker push PRIVATE_HOST/app:latest
```


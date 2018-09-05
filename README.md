# docker-useful-commands
* [Cleaning](#cleaning)
* [Push](#push)
* [Swarm](#swarm)
  * [Init](#init)
  * [Join](#join)
  * [Leave](#leave)
  * [Stack deploy](#stack-deploy)
### Cleaning
#### Delete all volumes
```
    $ docker volume rm $(docker volume ls -qf dangling=true)
    $ docker volume ls -qf dangling=true | xargs -r docker volume rm
```
#### Delete all networks
```
    $ docker network ls  
    $ docker network ls | grep "bridge"   
    $ docker network rm $(docker network ls | grep "bridge" | awk '/ / { print $1 }')
```
    
#### Remove docker images
    
```
    $ docker rmi $(docker images --filter "dangling=true" -q --no-trunc)
```
#### Remove docker containers
```
    $ docker rm $(docker ps -qa --no-trunc --filter "status=exited")
```

### Push
Login into a private registry
```
    $ docker login PRIVATE_HOST
```

Tag and push
```
    $ docker tag app:latest PRIVATE_HOST/app:latest
    $ docker push PRIVATE_HOST/app:latest
```

### Swarm
#### Init
Initialize swarm mode
```
docker swarm init
```

#### Join
Generete token for other nodes
```
docker swarm join-token [OPTIONS] (worker|manager)
```

#### Leave
```
docker swarm leave
```

#### Stack deploy
```
docker stack deploy --compose-file=docker-compose.yml STACK_NAME
```


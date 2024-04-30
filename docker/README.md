# Docker iamges

## multi arch

- Just windows amd64 for now

create builder

```shell
docker buildx create --name mybuilder --use --bootstrap
```

build and push image 

```shell
# amd64 
docker buildx build --platform linux/amd64 --load -t wanglei4687/dev-container:cuda12 dev/

# push registry 
docker buildx build --platform linux/amd64 --push -t wanglei4687/dev-container:cuda12 dev/
```

# Docker iamges

## multi arch

create builder

```shell
docker buildx create --name mybuilder --use --bootstrap
```

build and push image 

```shell
docker buildx build --platform linux/arm64,linux/amd64 --load -t wanglei4687/dev-container:cuda12 dev/ 
```

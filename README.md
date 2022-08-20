# dockerAction

+ `docker search nginx` 查找nginx相关的镜像
```
  NAME                                              DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
  nginx                                             Official build of Nginx.                        17282     [OK]  
```
+ `docker image pull golang:1.13.15` 拉取指定tag的golang镜像
```
1.13.15: Pulling from library/golang
d6ff36c9ec48: Pull complete 
c958d65b3090: Pull complete 
edaf0a6b092f: Pull complete 
80931cf68816: Pull complete 
813643441356: Pull complete 
799f41bb59c9: Pull complete 
16b5038bccc8: Pull complete 
Digest: sha256:8ebb6d5a48deef738381b56b1d4cd33d99a5d608e0d03c5fe8dfa3f68d41a1f8
Status: Downloaded newer image for golang:1.13.15
docker.io/library/golang:1.13.15
```
+ `docker image ls`  列出**当前主机上**的镜像
+ `docker image history golang:1.13.15` 镜像构建的历史信息
```
IMAGE          CREATED       CREATED BY                                      SIZE      COMMENT
d6f3656320fe   2 years ago   /bin/sh -c #(nop) WORKDIR /go                   0B        
<missing>      2 years ago   /bin/sh -c mkdir -p "$GOPATH/src" "$GOPATH/b…   0B        
<missing>      2 years ago   /bin/sh -c #(nop)  ENV PATH=/go/bin:/usr/loc…   0B        
<missing>      2 years ago   /bin/sh -c #(nop)  ENV GOPATH=/go               0B        
<missing>      2 years ago   /bin/sh -c set -eux;   dpkgArch="$(dpkg --pr…   328MB     
<missing>      2 years ago   /bin/sh -c #(nop)  ENV GOLANG_VERSION=1.13.15   0B        
<missing>      2 years ago   /bin/sh -c #(nop)  ENV PATH=/usr/local/go/bi…   0B        
<missing>      2 years ago   /bin/sh -c apt-get update && apt-get install…   182MB     
<missing>      2 years ago   /bin/sh -c apt-get update && apt-get install…   146MB     
<missing>      2 years ago   /bin/sh -c set -ex;  if ! command -v gpg > /…   17.5MB    
<missing>      2 years ago   /bin/sh -c apt-get update && apt-get install…   16.5MB    
<missing>      2 years ago   /bin/sh -c #(nop)  CMD ["bash"]                 0B        
<missing>      2 years ago   /bin/sh -c #(nop) ADD file:4b03b5f551e3fbdf4…   114MB  
```
+ `docker inspect`
+ `docker image prune`

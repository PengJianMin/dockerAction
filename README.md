# dockerAction
# `docker info` 查看dockerd的信息
```
Client:
 Context:    default
 Debug Mode: false
 Plugins:
  app: Docker App (Docker Inc., v0.9.1-beta3)
  buildx: Docker Buildx (Docker Inc., v0.8.2-docker)
  scan: Docker Scan (Docker Inc., v0.17.0)

Server:
 Containers: 1
  Running: 0
  Paused: 0
  Stopped: 1
 Images: 5
 Server Version: 19.03.15
 Storage Driver: overlay2
  Backing Filesystem: xfs
  Supports d_type: true
  Native Overlay Diff: true
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local logentries splunk syslog
 Swarm: inactive
 Runtimes: runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 894b81a4b802e4eb2a91d1ce216b8817763c29fb
 runc version: 425e105d5a03fabd737a126ad93d62a9eeede87f
 init version: fec3683
 Security Options:
  seccomp
   Profile: default
 Kernel Version: 4.18.0-240.15.1.el8_3.x86_64
 Operating System: CentOS Linux 8
 OSType: linux
 Architecture: x86_64
 CPUs: 2
 Total Memory: 1.75GiB
 Name: 192.168.81.130
 ID: RF53:NP3W:WDBT:MDZ7:VNVS:F3SR:XFFZ:HBW6:SFOT:PLFQ:ZBNO:LBHE
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Registry: https://index.docker.io/v1/
 Labels:
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
 Registry Mirrors:
  https://6kx4zyno.mirror.aliyuncs.com/
 Live Restore Enabled: false
```
# `docker search` 查找镜像
+ `docker search golang` 
```
NAME                                               DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
golang                                             Go (golang) is a general purpose, higher-lev…   4232      [OK]       
circleci/golang                                    CircleCI images for Go                          18                   [OK]
portainer/golang-builder                           Utility to build Golang binaries.               6                    [OK]
bitnami/golang                                                                                     5                    
superseriousbusiness/gotosocial                    A Golang fediverse server!                      3                    
okteto/golang                                      Development environment for golang              2                    
docker/dev-environments-go                         Image for dev-environments using Golang as m…   2                    
clearlinux/golang                                  Go (golang) imperative programming language …   1                    
webdevops/go-crond                                 Small cron daemon written in golang             1                    [OK]
openwhisk/actionloop-golang-v1.11                  Apache OpenWhisk runtime for Golang v1.11 Ac…   1                    
puppet/gogrpc                                      A container for building golang projects tha…   1                    [OK]
okteto/golang-http-template                                                                        0                    
```
# `docker pull` 拉取镜像
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
# `docker image ls` `docker images` 获取本地镜像列表
```
REPOSITORY   TAG       IMAGE ID       CREATED         SIZE
nginx        latest    605c77e624dd   7 months ago    141MB
redis        latest    7614ae9453d1   8 months ago    113MB
ubuntu       latest    ba6acccedd29   10 months ago   72.8MB
centos       latest    5d0da3dc9764   11 months ago   231MB
golang       1.13.15   d6f3656320fe   2 years ago     803MB
```
# `docker image history` 镜像构建的历史信息
+ `docker image history golang:1.13.15` 
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
# `docker image inspect`查看镜像具体信息
+ `docker image inspect redis` 
```
[
    {
        "Id": "sha256:7614ae9453d1d87e740a2056257a6de7135c84037c367e1fffa92ae922784631",
        "RepoTags": [
            "redis:latest"
        ],
        "RepoDigests": [
            "redis@sha256:db485f2e245b5b3329fdc7eff4eb00f913e09d8feb9ca720788059fdc2ed8339"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2021-12-21T12:42:49.755107412Z",
        "Container": "13d25f53410417c5220c8dfe8bd49f06abdbcd69faa62a9b877de02464bb04a3",
        "ContainerConfig": {
            "Hostname": "13d25f534104",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "6379/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "GOSU_VERSION=1.12",
                "REDIS_VERSION=6.2.6",
                "REDIS_DOWNLOAD_URL=http://download.redis.io/releases/redis-6.2.6.tar.gz",
                "REDIS_DOWNLOAD_SHA=5b2b8b7a50111ef395bf1c1d5be11e6e167ac018125055daa8b5c2317ae131ab"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"redis-server\"]"
            ],
            "Image": "sha256:e093f59d716c95cfce82c676f099b960cc700432ab531388fcedf79932fc81ec",
            "Volumes": {
                "/data": {}
            },
            "WorkingDir": "/data",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "DockerVersion": "20.10.7",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "6379/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "GOSU_VERSION=1.12",
                "REDIS_VERSION=6.2.6",
                "REDIS_DOWNLOAD_URL=http://download.redis.io/releases/redis-6.2.6.tar.gz",
                "REDIS_DOWNLOAD_SHA=5b2b8b7a50111ef395bf1c1d5be11e6e167ac018125055daa8b5c2317ae131ab"
            ],
            "Cmd": [
                "redis-server"
            ],
            "Image": "sha256:e093f59d716c95cfce82c676f099b960cc700432ab531388fcedf79932fc81ec",
            "Volumes": {
                "/data": {}
            },
            "WorkingDir": "/data",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 112691373,
        "VirtualSize": 112691373,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/9ceaf0abe063216337e51e8b8903162c5591756d40d83fce2bba5e5917cfa9d6/diff:/var/lib/docker/overlay2/dffa714dbd90cc2d81052bf7085c820fa526cf5616e22f306b5a9a373386cd9f/diff:/var/lib/docker/overlay2/c97ccd14148e48bfd06846af8b2b2bac14b23b72507643182a8ad4583b952873/diff:/var/lib/docker/overlay2/e488559edf139d93a6141d59fcd6f6bf6f7963a4897f4f8a7fe178cdb2383c62/diff:/var/lib/docker/overlay2/ad49d021b6e6ec252efa770a440fd41563e421845442fd422e69d7bcfefb9b84/diff",
                "MergedDir": "/var/lib/docker/overlay2/1b15f7d574500cbea715557a2574821917a8ce2c408b3e286466a7908add7e44/merged",
                "UpperDir": "/var/lib/docker/overlay2/1b15f7d574500cbea715557a2574821917a8ce2c408b3e286466a7908add7e44/diff",
                "WorkDir": "/var/lib/docker/overlay2/1b15f7d574500cbea715557a2574821917a8ce2c408b3e286466a7908add7e44/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:2edcec3590a4ec7f40cf0743c15d78fb39d8326bc029073b41ef9727da6c851f",
                "sha256:9b24afeb7c2f21e50a686ead025823cd2c6e9730c013ca77ad5f115c079b57cb",
                "sha256:4b8e2801e0f956a4220c32e2c8b0a590e6f9bd2420ec65453685246b82766ea1",
                "sha256:529cdb636f61e95ab91a62a51526a84fd7314d6aab0d414040796150b4522372",
                "sha256:9975392591f2777d6bf4d9919ad1b2c9afa12f9a9b4d260f45025ec3cc9b18ed",
                "sha256:8e5669d8329116b8444b9bbb1663dda568ede12d3dbcce950199b582f6e94952"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]

```
# `docker image tag`给镜像重新打tag
+ `docker image tag nginx:1.19.2 upperpeng.com/nginx:1.19.2`   
+ `docker image rm upperpeng.com/nginx:1.19.2`
```
REPOSITORY            TAG       IMAGE ID       CREATED         SIZE
nginx                 1.19.2    7e4d58f0e5f3   23 months ago   133MB
upperpeng.com/nginx   1.19.2    7e4d58f0e5f3   23 months ago   133MB
```
# `docker image prune` 清理未使用的镜像（未跑容器）
# `docker image rm` `docker rmi` 
# `docker image tag` 给镜像打标签
# `docker image push` 推送镜像到hub
# `docker image save` 将镜像导出为tar文件
# `docker image load` 将tar文件导入为镜像
# `docker image import` 导入容器tar文件为镜像
# `docker image build` 从dockerfile构建镜像


# `docker container run` 从镜像启动容器
+ `docker container run -itd --name myweb -p 9999:80 nginx:latest` 将本地9999端口映射给容器80端口
 ```
 d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8
 
 CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
d3fe3507f9cf   nginx:latest   "/docker-entrypoint.…"   49 seconds ago   Up 47 seconds   0.0.0.0:9999->80/tcp   myweb
 ```
# `docker create` 创建容器，但未启动
# `docker container ls` `docker container ls -a`
# `docker container inspect`
# `docker container exec`
# `docker container start`
# `docker container restart` 
# `docker container stop`
# `docker container kill`
# `docker container logs`
# `docker container rm`
# `docker container prune`
# `docker container top`
# `docker container cp`
# `docker container port`
+ `docker container port myweb`
```
80/tcp -> 0.0.0.0:9999 容器的80端口对应本地的9999端口
```
# `docker container rename`
+ `docker container rename web myweb` 将容器名字从web修改为myweb
# `docker container stats`
# `docker container export` 将容器直接导出为tar文件，和`docker image import`搭配使用
# `docker container commit`
# `docker container update`

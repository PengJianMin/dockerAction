# dockerAction
# `docker info` 查看dockerd系统级的信息
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
# `docker search` 在hub中查找镜像
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
# `docker image history` 展示该镜像构建的历史信息
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
# `docker image rm` `docker rmi` 删除一个或多个镜像
# `docker image push` 推送镜像到hub
# `docker image save` 将镜像导出为tar文件
# `docker image load` 将tar文件导入为镜像
# `docker image import` 导入容器tar文件为镜像
# `docker image build` 从dockerfile构建镜像


# `docker container run` 从镜像启动容器
+ `docker container run -itd --name myweb -p 9999:80 -v /data/myweb:/data nginx:latest` 将本地9999端口映射给容器80端口，使用`-d`让其运行在后台，否则一退出容器就会被挂起，`-i`让其保持输入流
  + `-i` 使用交互模式，始终保持输入流开放
  + `-t` 分配一个伪终端
  + `-it` 在容器中利用打开的伪终端进行交互操作
  + `-d` 让容器可以运行在后台（默认运行在前台，无法在后台运行）
  + `-v` 挂载数据卷volume
  + `-p` 暴露端口
  + `-e` 指定容器内的环境变量
 ```
 [root@192 ~]# docker container run -itd --name myweb -p 9999:80 -v /data/myweb:/data nginx:latest
 d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8
 
 CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                  NAMES
d3fe3507f9cf   nginx:latest   "/docker-entrypoint.…"   49 seconds ago   Up 47 seconds   0.0.0.0:9999->80/tcp   myweb
 ```
# `docker create` 创建新容器，但未启动
# `docker container ls` `docker container ls -a` `docker ps` `docker ps -a` 列出容器
+ `docker container ls` 只列出运行中的容器
+ `docker container ls -a` 列出所有容器
```
[root@192 ~]# docker container ls 
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS          PORTS                  NAMES
d3fe3507f9cf   nginx:latest   "/docker-entrypoint.…"   11 hours ago   Up 37 minutes   0.0.0.0:9999->80/tcp   myweb
[root@192 ~]# docker container ls -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                      PORTS                  NAMES
c16b3010be25   nginx          "/docker-entrypoint.…"   5 minutes ago   Exited (0) 12 seconds ago                          competent_swartz
d3fe3507f9cf   nginx:latest   "/docker-entrypoint.…"   11 hours ago    Up 37 minutes               0.0.0.0:9999->80/tcp   myweb
```
# `docker container inspect` 查看容器详细信息
+ `docker container inspect myweb`
```
[
    {
        "Id": "d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8",
        "Created": "2022-08-20T14:31:24.007567564Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 2326,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2022-08-20T14:31:26.364337185Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:605c77e624ddb75e6110f997c58876baa13f8754486b461117934b24a9dc3a85",
        "ResolvConfPath": "/var/lib/docker/containers/d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8/hostname",
        "HostsPath": "/var/lib/docker/containers/d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8/hosts",
        "LogPath": "/var/lib/docker/containers/d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8/d3fe3507f9cf23d564970adeae0d339a1ec7a6d90a5f86e0457531236b4c5fb8-json.log",
        "Name": "/myweb",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {
                "80/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "9999"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/26956a1f5ff84dae9f96c0cfe16ae456c45d4dc666af050080288925d6ba3547-init/diff:/var/lib/docker/overlay2/3a510bd5bca16d2db043881acfcc60d9ef9c98763c28f1c63ef6902813adcd11/diff:/var/lib/docker/overlay2/5951971b8498e58b2e862323102c027deaee8af14e6ea5671a15769ec0afd596/diff:/var/lib/docker/overlay2/30361b29cfc55836cee4964eb81100d833cfd7475920499f8b7647bb887c2796/diff:/var/lib/docker/overlay2/89cbc7811b4136eddac454b1d4acf76aa1f6d5957517fe6de332639644a6d7bc/diff:/var/lib/docker/overlay2/9b5168a5fe4076eb8866787ff6f2814703b6792339eb5740d8c2ba596fba50f2/diff:/var/lib/docker/overlay2/ad49d021b6e6ec252efa770a440fd41563e421845442fd422e69d7bcfefb9b84/diff",
                "MergedDir": "/var/lib/docker/overlay2/26956a1f5ff84dae9f96c0cfe16ae456c45d4dc666af050080288925d6ba3547/merged",
                "UpperDir": "/var/lib/docker/overlay2/26956a1f5ff84dae9f96c0cfe16ae456c45d4dc666af050080288925d6ba3547/diff",
                "WorkDir": "/var/lib/docker/overlay2/26956a1f5ff84dae9f96c0cfe16ae456c45d4dc666af050080288925d6ba3547/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "d3fe3507f9cf",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.21.5",
                "NJS_VERSION=0.7.1",
                "PKG_RELEASE=1~bullseye"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:latest",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {
                "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "0ac7d06324f61ec1460740500cf7ebc2a42c99419e4c23f4abe684910b87575d",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "80/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "9999"
                    }
                ]
            },
            "SandboxKey": "/var/run/docker/netns/0ac7d06324f6",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "0c987de0c3e3c2fe02328a8ab9be674c04b86d9c21a41fd46c67639a00d067f2",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "124e07c02c328f747b7d2b451456215f719a71ba5adb2ce0a3ca899651de9503",
                    "EndpointID": "0c987de0c3e3c2fe02328a8ab9be674c04b86d9c21a41fd46c67639a00d067f2",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]

```
# `docker container exec` 在一个运行容器中执行一个命令
+ `docker container exec -it myweb /bin/bash` 利用bash进入容器
```
[root@192 ~]# docker container exec -it myweb /bin/bash
root@d3fe3507f9cf:/#
```
# `docker container start` 启动一个或多个容器
# `docker container restart` 重启一个或多个正在运行的容器
# `docker container stop` 停止一个或多个正在运行的容器
# `docker container kill` 杀死一个或多个正在运行的容器
# `docker container logs` 获取容器的日志
+ `docker container logs -f myweb`
```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/08/20 14:31:27 [notice] 1#1: using the "epoll" event method
2022/08/20 14:31:27 [notice] 1#1: nginx/1.21.5
2022/08/20 14:31:27 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/08/20 14:31:27 [notice] 1#1: OS: Linux 4.18.0-240.15.1.el8_3.x86_64
2022/08/20 14:31:27 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/08/20 14:31:27 [notice] 1#1: start worker processes
2022/08/20 14:31:27 [notice] 1#1: start worker process 30
2022/08/20 14:31:27 [notice] 1#1: start worker process 31
172.17.0.1 - - [20/Aug/2022:14:38:20 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.61.1" "-"
2022/08/20 15:20:01 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2022/08/20 15:20:01 [notice] 30#30: gracefully shutting down
2022/08/20 15:20:01 [notice] 30#30: exiting
2022/08/20 15:20:01 [notice] 30#30: exit
2022/08/20 15:20:01 [notice] 31#31: gracefully shutting down
2022/08/20 15:20:01 [notice] 31#31: exiting
2022/08/20 15:20:01 [notice] 31#31: exit
2022/08/20 15:20:01 [notice] 1#1: signal 17 (SIGCHLD) received from 30
2022/08/20 15:20:01 [notice] 1#1: worker process 30 exited with code 0
2022/08/20 15:20:01 [notice] 1#1: worker process 31 exited with code 0
2022/08/20 15:20:01 [notice] 1#1: exit
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2022/08/21 01:01:24 [notice] 1#1: using the "epoll" event method
2022/08/21 01:01:24 [notice] 1#1: nginx/1.21.5
2022/08/21 01:01:24 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2022/08/21 01:01:24 [notice] 1#1: OS: Linux 4.18.0-240.15.1.el8_3.x86_64
2022/08/21 01:01:24 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2022/08/21 01:01:24 [notice] 1#1: start worker processes
2022/08/21 01:01:24 [notice] 1#1: start worker process 23
2022/08/21 01:01:24 [notice] 1#1: start worker process 24
172.17.0.1 - - [21/Aug/2022:01:01:42 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.61.1" "-"
172.17.0.1 - - [21/Aug/2022:01:04:15 +0000] "GET /50x.html HTTP/1.1" 200 497 "-" "curl/7.61.1" "-"
172.17.0.1 - - [21/Aug/2022:01:11:52 +0000] "GET / HTTP/1.1" 200 615 "-" "curl/7.61.1" "-"
172.17.0.1 - - [21/Aug/2022:01:13:47 +0000] "GET / HTTP/1.1" 200 8 "-" "curl/7.61.1" "-"
```
# `docker container rm` 删除一个或多个容器
+ `docker container rm` 只能删除非运行状态的容器
+ `docker container rm -f` 强制删除容器
```
[root@192 ~]# docker container rm c16
Error response from daemon: You cannot remove a running container c16b3010be2540d17cfc8a8f8d624a7b97a60256e4fb1ed7c43b9c48c01ebbac. Stop the container before attempting removal or force remove
[root@192 ~]# docker container rm -f c16
c16
```
# `docker container prune` 删除所有已停止的容器
# `docker container top` 展示容器中运行的进程
+ `docker container top myweb`
```
[root@192 ~]# docker top myweb
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                1811                1793                0                   09:01               pts/0               00:00:00            nginx: master process nginx -g daemon off;
101                 1868                1811                0                   09:01               pts/0               00:00:00            nginx: worker process
101                 1869                1811                0                   09:01               pts/0               00:00:00            nginx: worker process
```
# `docker container cp` 在本地文件系统和容器之间复制文件和文件夹
+ `docker container cp myweb:/usr/share/nginx/html/index.html .` 从容器复制到本地
+ `docker container cp ./index.html myweb:/usr/share/nginx/html/index.html` 从本地复制到容器
```
[root@192 ~]# curl localhost:9999
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
[root@192 ~]# docker container cp myweb:/usr/share/nginx/html/index.html .
[root@192 ~]# cat index.html 
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
[root@192 ~]# cat > index.html 
1234567
[root@192 ~]# docker container cp ./index.html myweb:/usr/share/nginx/html/index.html 
[root@192 ~]# curl localhost:9999
1234567
```
# `docker container port` 列出所有端口映射或者某一容器的端口映射情况
+ `docker container port myweb`
+ `docker container port d3fe`
```
80/tcp -> 0.0.0.0:9999 容器的80端口对应本地的9999端口
```
# `docker container rename` 重命名容器
+ `docker container rename web myweb` 将容器名字从web修改为myweb
# `docker container stats` 显示容器实时的资源使用情况
```
[root@192 ~]# docker container stats
CONTAINER ID   NAME               CPU %     MEM USAGE / LIMIT    MEM %     NET I/O          BLOCK I/O         PIDS
c16b3010be25   competent_swartz   0.00%     4.102MiB / 1.75GiB   0.23%     586B / 0B        1.09MB / 32.8kB   3
d3fe3507f9cf   myweb              0.00%     15.5MiB / 1.75GiB    0.86%     14.2kB / 9.2kB   50.3MB / 0B       3

[root@192 ~]# docker container stats myweb
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O          BLOCK I/O     PIDS
d3fe3507f9cf   myweb     0.00%     15.5MiB / 1.75GiB   0.86%     14.2kB / 9.2kB   50.3MB / 0B   3

```
# `docker container export` 将容器直接导出为tar文件，和`docker image import`搭配使用
# `docker container commit` 对容器的“变化”生成镜像
# `docker container update` 更新容器的配置信息
# `docker volume create` 创建数据卷volume，创建后可以使用volume的名字进行挂载
# dockerfile
## `FROM` 指定基础镜像
## `MAINTAINER` 指定维护者信息
## `RUN` 构建镜像时，运行额外的指令，如创建目录mkdir等等
## `ADD` 拷贝文件或目录到容器中/可指定压缩文件进行自动解压或url进行指定用下载
## `COPY` 拷贝文件或目录到容器中
## `ENV` 设置容器环境变量
## `EXPOSE` 声明容器暴露的端口（仅声明，不起实际作用）
## `VOLUME` 指定挂载卷/自动创建匿名卷并进行挂载
## `WORKDIR` 指定工作目录，类似在linux系统中使用cd命令后到达的目录
## `USER` 指定执行命令的用户
## `HEALTHCHECK` 健康检查 
+ `HEALTHECHECK --interval=5m --timeout=3s --retries=3 CMD command || exit1`
## `CMD` 运行容器时执行的命令/在运行容器时可被覆盖，该命令会被加到ENTRYPOINT后边在启动时执行，区别时它可以被覆盖
## `ENTRYPOINT` 运行容器时执行的命令/在运行容器时指定命令和参数传递给ENTRYPOINT执行命令的参数
## `ARG` 定义构建参数
```
[root@192 myweb]# cat Dockerfile 
FROM ubuntu:latest

LABEL user="upper"
LABEL email="upper@outlook.com"

#仅声明，不生效
EXPOSE 80

#在容器中执行命令
RUN mkdir -p /data/web

#将myweb添加到对应目录
ADD myweb /data/web 

#容器启动时执行的命令
ENTRYPOINT ["/data/web/myweb"]

```
# `docker image build . `
+ `-t` 给镜像打tag
+ `-f` 指定要构建的dockerfile
+ `--build-arg` 构建参数
```
[root@192 myweb]# docker build . -t upperpeng.com/myweb:0.0.1
Sending build context to Docker daemon  6.186MB
Step 1/7 : FROM ubuntu:latest
 ---> ba6acccedd29
Step 2/7 : LABEL user="upper"
 ---> Running in b2289999c164
Removing intermediate container b2289999c164
 ---> 0b1896ac78f3
Step 3/7 : LABEL email="upper@outlook.com"
 ---> Running in ecd8d8f39dc3
Removing intermediate container ecd8d8f39dc3
 ---> f0eb519b686b
Step 4/7 : EXPOSE 80
 ---> Running in c3cf6da7c6cf
Removing intermediate container c3cf6da7c6cf
 ---> 169f77dc245d
Step 5/7 : RUN mkdir -p /data/web
 ---> Running in d08bd8cdf400
Removing intermediate container d08bd8cdf400
 ---> 8854f53c44e2
Step 6/7 : ADD myweb /data/web
 ---> a5adb40db30c
Step 7/7 : ENTRYPOINT ["/data/web/myweb"]
 ---> Running in 6aac9a859e94
Removing intermediate container 6aac9a859e94
 ---> 02e2beb5fea2
Successfully built 02e2beb5fea2
Successfully tagged upperpeng.com/myweb:0.0.1
[root@192 myweb]# docker images
REPOSITORY            TAG       IMAGE ID       CREATED         SIZE
upperpeng.com/myweb   0.0.1     02e2beb5fea2   6 seconds ago   79MB

[root@192 myweb]# docker run -itd -p 1234:80 upperpeng.com/myweb:0.0.1
48c5c0ec16f8cc7554c628334e26f8857207a9b4ddd9d5d8d63a0c7b806e2afe
[root@192 myweb]# lsof -i:1234
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
docker-pr 5340 root    4u  IPv6  88211      0t0  TCP *:search-agent (LISTEN)
[root@192 myweb]# docker ps -a
CONTAINER ID   IMAGE                       COMMAND             CREATED          STATUS          PORTS                  NAMES
48c5c0ec16f8   upperpeng.com/myweb:0.0.1   "/data/web/myweb"   18 seconds ago   Up 17 seconds   0.0.0.0:1234->80/tcp   laughing_cray
[root@192 myweb]# curl localhost:1234
48c5c0ec16f8:1661066260648343423[root@192 myweb]# curl localhost:1234
```
# 通过容器编译Golang程序
+ `docker run -it -v /root/myweb:/data/ golang:1.13.15 bash -c "cd /data; go build ."`
+ `docker run -it -v $(pwd) golang:1.13.15 bash -c "cd /data; go build ."`
```
[root@192 myweb]# ll
total 12
-rw-r--r--. 1 root root 215 Aug 21 15:15 Dockerfile
-rw-r--r--. 1 root root  36 Aug 21 11:19 go.mod
-rw-r--r--. 1 root root 304 Aug 21 11:19 main.go
[root@192 myweb]# pwd
/root/myweb
[root@192 myweb]# docker run -it -v /root/myweb:/data/ golang:1.13.15 bash -c "cd /data; go build ."
[root@192 myweb]# ll
total 7292
-rw-r--r--. 1 root root     215 Aug 21 15:15 Dockerfile
-rw-r--r--. 1 root root      36 Aug 21 11:19 go.mod
-rw-r--r--. 1 root root     304 Aug 21 11:19 main.go
-rwxr-xr-x. 1 root root 7454642 Aug 21 16:23 myweb
```
+ `docker run -it -v /root/myweb:/data/ -e GOPROXY=https://goproxy.cn golang:1.13.15 bash -c "cd /data; go build ."`

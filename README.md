## Pocket Node Docker Images 
* [namenode](https://hub.docker.com/r/yawenw/pocket-namenode/)

* [datanode-dram](https://hub.docker.com/r/yawenw/pocket-datanode-dram/)

* [reflex](https://hub.docker.com/r/yawenw/pocket-reflex/)


## Build Docker Image for Pocket 
``` 
# AWS AMI for Kubernetes: k8s-1.8-debian-jessie-amd64-hvm-ebs-2018-02-08 (ami-f5d2548d)

git clone https://github.com/wyawen/pocket-container.git
cd pocket-container

# Build namenode
cp Dockerfile-namenode Dockerfile
sudo docker build -t yawenw/pocket-namenode .

# Build DRAM datanode
cp Dockerfile-datanode-dram Dockerfile
sudo docker build -t yawenw/pocket-datanode-dram .

# Build ReFlex datanode 
# pull and complie ReFlex following instructions at https://github.com/stanford-mast/reflex
cp reflex_scripts/* reflex/
cp Dockerfile-reflex Dockerfile
sudo docker build -t yawenw/pocket-reflex .
```

## Run Pocket in Container
``` 
# Run namenode
sudo docker run -it --net=host --privileged yawenw/pocket-namenode

# Run DRAM datanode
sudo docker run -it --net=host --privileged -v /dev:/dev yawenw/pocket-datanode-dram

# Run ReFlex datanode 
sudo docker run -it --net=host --privileged -v /dev:/dev -v /lib/modules/`uname -r`:/lib/modules/`uname -r` yawenw/pocket-reflex
```


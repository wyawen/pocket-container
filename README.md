# pocket-container
* [namenode](https://hub.docker.com/r/yawenw/pocket-namenode/)

* [datanode-dram](https://hub.docker.com/r/yawenw/pocket-datanode-dram/)

* [reflex](https://hub.docker.com/r/yawenw/pocket-reflex/)


## Build Docker Image for Pocket 
``` 
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
cp reflex_scripts/* reflex
cp Dockerfile-reflex Dockerfile
sudo docker build -t yawenw/pocket-reflex .
```

## Run Pocket in Container
``` 
# Run namenode
sudo docker run -it -v /dev:/dev yawenw/pocket-namenode

# Run DRAM datanode
sudo docker run -it --net=host --privileged -v /dev:/dev yawenw/pocket-datanode-dram

# Run ReFlex datanode 
sudo docker run -it --net=host --privileged -v /dev:/dev -v /lib/modules/`uname -r`:/lib/modules/`uname -r` yawenw/pocket-reflex
```


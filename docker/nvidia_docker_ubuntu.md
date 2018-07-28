## To install `nvidia-docker` on ubuntu

### 1. Install Docker-CE

ubuntu 16.04, 18.04: TODO

[ubuntu 17.10](./install_docker_ubuntu_17.10.md)

### 2. Install NVIDIA GPU device plugin

<https://github.com/nvidia/nvidia-docker>

* Ubuntu 14.04/16.04/18.04, Debian Jessie/Stretch

```bash
# If you have nvidia-docker 1.0 installed: we need to remove it and all existing GPU containers
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker

# Add the package repositories
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update

# Install nvidia-docker2 and reload the Docker daemon configuration
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd

# Test nvidia-smi with the latest official CUDA image
docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```

* Ubuntu 17.10: Similar script above, set `distribution` to `ubuntu16.04` works
# **PyTorch Dockerfiles**

I've taken the [Dockerfile](https://github.com/ROCmSoftwarePlatform/pytorch/wiki/Dockerfile) from [the build instructions](https://github.com/ROCmSoftwarePlatform/pytorch/wiki/Building-PyTorch-for-ROCm#option-3-install-using-minimal-rocm-docker-file) which ask us to use docker.


Follow the instructions to get it working and use this command to allow the docker container to display graphical content through a GUI rather than just through the command line.

```
xhost +local:root && \
docker run -it \
    --env="DISPLAY" \
    --env="QT_X11_NO_MITSHM=1" \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
    --volume=$HOME:/data \
    --privileged \
    --rm \
    --device=/dev/kfd \
    --device=/dev/dri \
    --group-add video \
    odellus/pytorch-rocm:v0 && \
xhost -local:root
```
I've also got some extra packages I'd like to include inside the dockerfile so I don't have to do a bunch of commits to the images and keep the Dockerfile lean.

## Windows

- https://docs.nvidia.com/cuda/wsl-user-guide/index.html
- https://learn.microsoft.com/zh-tw/windows/wsl/install
- https://learn.microsoft.com/en-us/windows/wsl/basic-commands

### WSL

```shell
$ wsl --install
$ wsl --update
```

WSL config

PATH: %USERPROFILE%/.wslconfig

```text 
[experimental]
autoMemoryReclaim=gradual  # gradual  | dropcache | disabled
networkingMode=mirrored
dnsTunneling=true
firewall=true
autoProxy=true
```

WSL Ubuntu config

PATH: /etc/wsl.conf

```text
[boot]
systemd=true

[network]
hostname = dooryme
generateHosts = false
generateResolvConf = true
```


### update WSL kernel

download and install

`https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi`

### Docker 

```shell
$ winget install  Docker.DockerDesktop
```

### Cuda

for windows

- https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=11&target_type=exe_local

## Check (WSL)

```shell
$ docker run --rm -it --gpus all pytorch/pytorch:2.1.2-cuda12.1-cudnn8-runtime nvidia-smi
```

Expect

```text
Fri Jan 26 06:47:51 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.40.06              Driver Version: 551.23         CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 4080        On  |   00000000:01:00.0  On |                  N/A |
|  0%   32C    P8             12W /  360W |    1909MiB /  16376MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A        34      G   /Xwayland                                   N/A      |
|    0   N/A  N/A        36      G   /Xwayland                                   N/A      |
|    0   N/A  N/A        50      G   /Xwayland                                   N/A      |
+-----------------------------------------------------------------------------------------+
```


## Rapids

```shell
docker run --gpus all --pull always --rm -it --shm-size=1g --ulimit memlock=-1 --ulimit stack=67108864 nvcr.io/nvidia/rapidsai/base:23.12-cuda12.0-py3.10
```
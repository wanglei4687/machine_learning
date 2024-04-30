FROM nvidia/cuda:12.3.2-cudnn9-devel-ubuntu22.04

ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

RUN apt update && apt upgrade -y 

RUN apt install -y software-properties-common wget curl \
        python3-dev python3-pip python3-wheel python3-setuptools \
        python3-ipykernel

RUN pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

RUN apt install git -y
FROM nvidia/cuda:12.3.2-cudnn9-devel-ubuntu22.04

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ENV TZ=Asia/Shanghai \
    DEBIAN_FRONTEND=noninteractive

RUN apt update && apt upgrade -y 

RUN groupadd --gid $USER_GID $USERNAME \
        && useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME \
        && apt-get update \
        && apt-get install -y sudo wget \
        && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
        && chmod 0440 /etc/sudoers.d/$USERNAME

RUN apt install -y software-properties-common curl \
        python3-dev python3-pip python3-wheel python3-setuptools \
        python3-ipykernel git vim  fonts-powerline zsh gnupg2\
        locales \
        # set up locale
        && locale-gen en_US.UTF-8

# Clean up
RUN apt autoremove -y \
    && apt clean -y \
    && rm -rf /var/lib/apt/lists/*

# generate locale for agnoster
RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && /usr/sbin/locale-gen

RUN pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# the user we're applying this too (otherwise it most likely install for root)
USER $USERNAME

ENV TERM xterm

# Set the default shell to bash rather than sh
ENV SHELL /bin/zsh

# set home
ENV HOME /home/$USERNAME

 # run the installation script
RUN sh -c "$(wget -O- https://install.ohmyz.sh/)"

# install powerlevel10k
# RUN git clone https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k

# RUN cd $HOME && curl -fsSLO https://raw.gitmirror.com/romkatv/dotfiles-public/master/.purepower

# zsh configuration
ADD .zshrc $HOME
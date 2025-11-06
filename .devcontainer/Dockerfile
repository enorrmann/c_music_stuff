# Imagen base de Ubuntu
FROM ubuntu:22.04

# Evita las preguntas interactivas durante la instalación
ENV DEBIAN_FRONTEND=noninteractive

# Actualiza el sistema e instala herramientas necesarias
RUN apt-get update && apt-get install -y \
    build-essential \        
    gdb \                    
    valgrind \               
    cmake \                  
    git \                    
    curl \                   
    vim \                    
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Crea un usuario no root (recomendado para Codespaces)
ARG USERNAME=coder
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update && apt-get install -y sudo \
    && echo "$USERNAME ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER $USERNAME
WORKDIR /workspaces

# Configura compilador por defecto
ENV CC=gcc
ENV CXX=g++

# Mensaje de bienvenida
RUN echo 'echo "Bienvenido al entorno C de GitHub Codespaces!"' >> /home/$USERNAME/.bashrc

FROM rocker/r-ver:4.4.2

ENV DEBIAN_FRONTEND=noninteractive

# 1. Dependencias del sistema (Añadidas librerías para mapas y gráficos)
RUN apt-get update && apt-get install -y \
    build-essential \
    pkg-config \
    libzmq3-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libpng-dev \
    zlib1g-dev \
    # Dependencias críticas para paquetes espaciales (sustitutos de rgdal)
    libgdal-dev \
    libgeos-dev \
    libproj-dev \
    libudunits2-dev \
    python3 python3-venv python3-pip \
    locales \
    && echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
    && locale-gen en_US.UTF-8 \
    && rm -rf /var/lib/apt/lists/*

ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8

# 2. Jupyter en venv
RUN python3 -m venv /opt/venv \
    && /opt/venv/bin/pip install --upgrade pip \
    && /opt/venv/bin/pip install notebook jupyter jupyterlab ipykernel
ENV PATH="/opt/venv/bin:$PATH"

# 3. Instalación de paquetes R (Sin rgdal, con sf y ggplot2)
RUN install2.r --error \
    IRkernel \
    corrplot \
    NbClust \
    MASS \
    factoextra \
    colorspace \
    sp \
    sf \
    ggplot2 \
    clv \
    tidyverse \
    caret \
    psych \
    GGally \
    && R -e "IRkernel::installspec(user = FALSE)"

# Verificación
RUN R

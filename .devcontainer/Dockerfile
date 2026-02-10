FROM rocker/r-ver:4.4.2

ENV DEBIAN_FRONTEND=noninteractive
ENV LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8

# --- CORRECCIÓN CRÍTICA AQUÍ ---
# Cambiamos 'jammy' (Ubuntu 22.04) por 'noble' (Ubuntu 24.04)
# Esto alinea los binarios de R con las librerías del sistema de rocker/r-ver:4.4.2
RUN echo "options(repos = c(CRAN = 'https://packagemanager.posit.co/cran/__linux__/noble/latest'))" >> /usr/local/lib/R/etc/Rprofile.site

# 2. Dependencias del sistema
# Mantenemos las librerías necesarias.
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    libzmq3-dev \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libpng-dev \
    zlib1g-dev \
    # Dependencias espaciales
    libgdal-dev \
    libgeos-dev \
    libproj-dev \
    libudunits2-dev \
    # Dependencias gráficas/texto (fix para caret/tidyverse)
    libfontconfig1-dev \
    libcairo2-dev \
    libicu-dev \
    # Python
    python3 python3-venv python3-pip \
    locales \
    && echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
    && locale-gen en_US.UTF-8 \
    && rm -rf /var/lib/apt/lists/*

# 3. Jupyter
RUN python3 -m venv /opt/venv \
    && /opt/venv/bin/pip install --upgrade pip --no-cache-dir \
    && /opt/venv/bin/pip install --no-cache-dir jupyterlab ipykernel
ENV PATH="/opt/venv/bin:$PATH"

# 4. Instalación de paquetes R
# Eliminamos clv y httppgd que daban problemas.
# Al usar el repo 'noble', sf y caret encontrarán las librerías correctas (.so files).
RUN install2.r --error --skipinstalled --ncpus -1 \
    IRkernel \
    corrplot \
    NbClust \
    MASS \
    factoextra \
    colorspace \
    sp \
    sf \
    ggplot2 \
    tidyverse \
    caret \
    psych \
    GGally \
    && R -e "IRkernel::installspec(user = FALSE)" \
    && rm -rf /tmp/downloaded_packages

CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
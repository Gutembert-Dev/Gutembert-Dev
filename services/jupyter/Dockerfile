FROM jupyter/scipy-notebook:latest

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8

USER root

RUN apt-get update --fix-missing && apt-get install -y \
    byobu \
    ca-certificates \
    curl \
    git-core \
    htop \
    unzip \
    wget \
    gcc \
    libpq-dev \
    python-dev \
    python3-dev \
    python3-llvmlite \
    build-essential \
    libtesseract-dev \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*



RUN pip install --upgrade pip
# seems 2 versions of numpy are installed. This is a fix
RUN pip uninstall -y numpy; pip uninstall -y numpy;pip uninstall -y numpy
RUN pip --no-cache-dir install -U \
    jupyter_server==1.3.0 \
    jupyter \
    jupyterlab \
    numpy \
    pandas \
    sqlalchemy \
    pyarrow \
    inflection \
    tqdm


USER jovyan
WORKDIR /home/jovyan/
## if rebulding notebook need to delete old config
RUN rm -rf /home/jovyan/.jupyter
RUN jupyter notebook --generate-config
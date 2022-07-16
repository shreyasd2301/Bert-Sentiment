FROM nvidia/cuda:10.2-cudnn7-runtime-ubuntu18.04
RUN apt update && apt install -y htop python3-dev wget
ENV PATH="/root/miniconda3/bin:${PATH}"
ARG PATH="/root/miniconda3/bin:${PATH}"
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh \
    && mkdir /root/.conda \
    && bash Miniconda3-latest-Linux-x86_64.sh -b \
    && rm -f Miniconda3-latest-Linux-x86_64.sh \
    && echo "Running $(conda --version)" && \
    conda init bash && \
    . /root/.bashrc && \
    conda update conda && \
    conda create -n bert-app && \
    conda activate bert-app && \
    conda install python=3.8 pip
COPY . src/
RUN cd src \
    && pip install -r requirements.txt
    
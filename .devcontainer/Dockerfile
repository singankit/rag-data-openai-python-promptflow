FROM mcr.microsoft.com/devcontainers/python:3.10
ENV PYTHONUNBUFFERED 1

WORKDIR /
COPY src/requirements.txt .

ENV CONDA_PREFIX=/azureml-envs/ai-development-env
ENV CONDA_DEFAULT_ENV=$CONDA_PREFIX
ENV PATH=$CONDA_PREFIX/bin:$PATH
ENV LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$LD_LIBRARY_PATH

# needed for build_mlindex
RUN apt update && apt install -y fuse

RUN pip3 install virtualenv
RUN python3 -m venv venv
ENV PATH="/venv/bin:$PATH"
RUN pip3 install --upgrade pip
RUN pip3 cache purge

# Install Python SDK
RUN pip3 install -r requirements.txt 

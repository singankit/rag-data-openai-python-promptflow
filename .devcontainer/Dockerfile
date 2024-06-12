FROM mcr.microsoft.com/devcontainers/python:3.10
ENV PYTHONUNBUFFERED 1

WORKDIR /

ENV CONDA_PREFIX=/azureml-envs/ai-development-env
ENV CONDA_DEFAULT_ENV=$CONDA_PREFIX
ENV PATH=$CONDA_PREFIX/bin:$PATH
ENV LD_LIBRARY_PATH=$CONDA_PREFIX/lib:$LD_LIBRARY_PATH

# needed for build_mlindex
RUN apt update && apt install -y fuse

RUN pip3 install virtualenv
RUN python3 -m venv venv
ENV PATH="/venv/bin:$PATH"

# Install Python SDK
COPY src/requirements.txt .
RUN python3 -m venv .venv
RUN source .venv/bin/activate
RUN pip3 install --upgrade pip
RUN pip3 cache purge
RUN pip3 install -r requirements.txt 

FROM mcr.microsoft.com/devcontainers/python:3.9-bullseye

COPY ./requirements.txt /tmp/
RUN \
    # dev setup
    apt update && \
    apt-get install bash-completion graphviz default-mysql-client s3fs procps -y && \
    pip install --no-cache-dir --upgrade pip && \
    # workflow dependencies
    apt-get install gcc ffmpeg libsm6 libxext6 -y && \
    # Commented out CaImAn installation due to Docker image size limits on Codespace
    # pip install --no-cache-dir Pygments==2.14.0  && \
    # git clone https://github.com/datajoint/CaImAn.git  && \
    # pip install --no-cache-dir -r ./CaImAn/requirements.txt  && \
    # pip install --no-cache-dir ./CaImAn && \
    pip install --no-cache-dir -r /tmp/requirements.txt && \
    # clean up
    # rm -rf /tmp/CaImAn && \
    rm /tmp/requirements.txt && \
    apt-get clean

ENV DJ_HOST fakeservices.datajoint.io
ENV DJ_USER root
ENV DJ_PASS simple

ENV DJ_PUBLIC_S3_MOUNT_PATH /workspaces/workflow-calcium-imaging/example_data
ENV IMAGING_ROOT_DATA_DIR /workspaces/workflow-calcium-imaging/example_data
ENV DATABASE_PREFIX neuro_
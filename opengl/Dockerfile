FROM ubuntu:22.04

ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=all

RUN apt-get update && apt-get install -y \
    libgl1 mesa-utils \
    && rm -rf /var/lib/apt/lists/*

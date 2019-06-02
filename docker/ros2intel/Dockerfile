ARG FROM_IMAGE=ros2base
FROM $FROM_IMAGE

ENV DEBIAN_FRONTEND=noninteractive

#######################################################
### Run intel configuration
RUN \
  apt-get update && \
  apt-get -y install libgl1-mesa-glx libgl1-mesa-dri && \
  rm -rf /var/lib/apt/lists/*

EXPOSE 11345

ENTRYPOINT [""]
CMD ["bash"]

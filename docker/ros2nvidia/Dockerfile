ARG FROM_IMAGE=nvidia/opengl:1.0-glvnd-devel-ubuntu18.04
FROM $FROM_IMAGE

ENV DEBIAN_FRONTEND=noninteractive

#######################################################
### nvidia docker settings
LABEL com.nvidia.volumes.needed="nvidia_driver"
ENV PATH /usr/local/nvidia/bin:/usr/local/cuda/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/local/nvidia/lib:/usr/local/nvidia/lib64:${LD_LIBRARY_PATH}

EXPOSE 11345

ENTRYPOINT [""]
CMD ["bash"]

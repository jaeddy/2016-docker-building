############################################################
# Dockerfile to build rapmap container images
# Based on Ubuntu images made by C. Titus Brown, e.g.
# https://github.com/ctb/2015-docker-building/blob/master/transrate/Dockerfile
# and CentOS-related modifications in image made by Laurent Jourden:
# https://hub.docker.com/r/genomicpariscentre/bcl2fastq/~/dockerfile/
############################################################

# Image: jaeddy/rapmap

# Set the base image to CentOS 5
FROM centos:5

# File author / maintainer
MAINTAINER James Eddy <james.a.eddy@gmail.com>

# Specify dependencies & version
ENV PACKAGES curl libgomp

ENV RAPMAP_VERSION 0.1.0-pre

# rapmap binary will be installed in /home/RapMap-${RAPMAP_VERSION}_CentOS5/bin/rapmap

### don't modify things below here for version updates etc.

WORKDIR /home

# Install packages
RUN yum -y install ${PACKAGES} && \
    yum clean packages

RUN curl -L https://github.com/COMBINE-lab/RapMap/releases/download/v${RAPMAP_VERSION}/RapMap-${RAPMAP_VERSION}_CentOS5.tar.gz | tar xzvf -

ENV PATH ${PATH}:/home/RapMap-${RAPMAP_VERSION}_CentOS5/bin

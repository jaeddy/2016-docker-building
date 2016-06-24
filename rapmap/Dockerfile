############################################################
# Dockerfile to build rapmap container images (with samtools baked in)
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
ENV PACKAGES curl libgomp bzip2 gcc make cmake zlib-devel ncurses-devel ncurses

ENV RAPMAP_VERSION 0.2.1
ENV SAMTOOLS_VERSION 1.3.1

# rapmap binary will be installed in /home/RapMap-${RAPMAP_VERSION}_CentOS5/bin/rapmap

### don't modify things below here for version updates etc.

WORKDIR /home

# Install packages
RUN yum -y install ${PACKAGES} && \
    yum clean packages

RUN curl -SL https://github.com/COMBINE-lab/RapMap/releases/download/v${RAPMAP_VERSION}/RapMap-${RAPMAP_VERSION}_CentOS5.tar.gz | tar xzvf -
RUN curl -SL https://github.com/samtools/samtools/releases/download/${SAMTOOLS_VERSION}/samtools-${SAMTOOLS_VERSION}.tar.bz2 | tar xjvf -
RUN cd samtools-${SAMTOOLS_VERSION} && \
    make && \
    make prefix=. install

ENV PATH ${PATH}:/home/RapMap-${RAPMAP_VERSION}_CentOS5/bin
ENV PATH ${PATH}:/home/samtools-${SAMTOOLS_VERSION}/bin

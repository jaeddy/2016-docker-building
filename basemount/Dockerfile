
############################################################
# Dockerfile to build rapmap container images (with samtools baked in)
# Based on Ubuntu images made by C. Titus Brown, e.g.
# https://github.com/ctb/2015-docker-building/blob/master/transrate/Dockerfile
# and CentOS-related modifications in image made by Laurent Jourden:
# https://hub.docker.com/r/genomicpariscentre/bcl2fastq/~/dockerfile/
############################################################

# Image: jaeddy/basemount

# Set the base image
FROM phusion/baseimage

# File author / maintainer
MAINTAINER James Eddy <james.a.eddy@gmail.com>

# Install basemount
RUN bash -c "$(curl -L https://basemount.basespace.illumina.com/install/)"

# Set up data directory
VOLUME /data
WORKDIR /data

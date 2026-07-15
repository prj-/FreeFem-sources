FROM ubuntu:24.04

ARG FF_VERSION

LABEL maintainer="FreeFEM, Frédéric Hecht <frederic.hecht@sorbonne-universite.fr>"
LABEL org.opencontainers.image.title="FreeFEM"
LABEL org.opencontainers.image.description="FreeFEM finite element language"
LABEL org.opencontainers.image.url="https://freefem.org"
LABEL org.opencontainers.image.source="https://github.com/FreeFem/FreeFem-sources"
LABEL org.opencontainers.image.licenses="LGPL-2.1"
LABEL org.opencontainers.image.version="${FF_VERSION}"

ENV DEBIAN_FRONTEND=noninteractive

# Install runtime dependencies declared by the FreeFEM .deb package
RUN apt-get update && apt-get install -y --no-install-recommends \
        libc6 \
        g++ \
        gcc \
        gfortran \
        libgsl-dev \
        libhdf5-dev \
        liblapack-dev \
        freeglut3-dev \
        mpich \
    && rm -rf /var/lib/apt/lists/*

# Copy and install the FreeFEM .deb built for Ubuntu 24.04
# Expected filename pattern: FreeFEM-<version>-amd64-ubuntu24.04.deb
COPY FreeFEM-*.deb /tmp/freefem.deb
RUN apt-get update && apt-get install -y --no-install-recommends /tmp/freefem.deb \
    && rm -f /tmp/freefem.deb \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /home/user
ENTRYPOINT ["/usr/local/bin/FreeFem++-nw"]
CMD ["--help"]

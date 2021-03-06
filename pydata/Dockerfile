FROM ubuntu:trusty

MAINTAINER "The Galactic Empire"

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -qq update && apt-get install -y language-pack-en
RUN locale-gen en_GB.UTF-8

ENV LANGUAGE en_GB.UTF-8
ENV LANG en_GB.UTF-8
ENV LC_ALL en_GB.UTF-8

RUN dpkg-reconfigure locales

RUN apt-get -qq update && \
    apt-get install -y python3-pip \
                       libblas3 \
                       libblas-dev \
                       libgfortran3 \
                       liblapack3 \
                       liblapack-dev \
                       gfortran \
                       libhdf5-dev

RUN pip3 install numpy
RUN pip3 install scipy
RUN pip3 install cython
RUN pip3 install numexpr
RUN pip3 install pandas
RUN pip3 install tables
RUN pip3 install scikit-learn
RUN pip3 install blaze
RUN pip3 install bokeh

# install matplotlib ------------------------------------
RUN apt-get -qq update && \
    apt-get install -y pkg-config \
                       libpng12-dev \
                       libfreetype6-dev
RUN pip3 install matplotlib


# install ipython ---------------------------------------
RUN apt-get -qq update && \
    apt-get install -y libzmq3 \
                       libzmq3-dev
RUN pip3 install pyzmq \
                 tornado \
                 jinja2 \
                 ipython

# might make the image smaller
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ADD run.sh /
RUN chmod +x /run.sh

VOLUME /srv
WORKDIR /srv

EXPOSE 8888

# You can mount your own SSL certs as necessary here
ENV PEM_FILE /key.pem
# $PASSWORD will get `unset` within notebook.sh, turned into an IPython style hash
ENV PASSWORD Dont make this your default
ENV USE_HTTP 0

# Default command to run
CMD ["/run.sh"]

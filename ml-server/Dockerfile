FROM amazonlinux:2

RUN yum install -y wget tar gzip gcc gcc-c++ make zlib-devel openssl-devel libffi-devel xz-devel bzip2-devel sqlite-devel
RUN mkdir /root/work /root/local /root/venv

WORKDIR /root/work
RUN wget https://www.python.org/ftp/python/3.7.7/Python-3.7.7.tgz
RUN tar zxvf Python-3.7.7.tgz

WORKDIR /root/work/Python-3.7.7
RUN ./configure --prefix=/root/local/python --with-ensurepip
RUN make
RUN make install
RUN /root/local/python/bin/python3 -m venv ~/venv/local


ADD ./requirements.txt /root/work/
RUN source ~/venv/local/bin/activate \
  && pip3 install -U pip \
  && pip3 install -r /root/work/requirements.txt
RUN mkdir ~/notebook
WORKDIR ~/notebook

CMD ~/venv/local/bin/jupyter lab --port 8888 --ip=0.0.0.0 --allow-root

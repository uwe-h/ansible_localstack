FROM ubuntu:20.04
ENV AWS_ACCESS_KEY_ID=test \
    AWS_SECRET_ACCESS_KEY=test \
    AWS_DEFAULT_REGION=us-west-2
RUN apt-get update && TZ="Europe/Berlin" apt-get install -y curl less unzip cron python3.9 python3-distutils xxd

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && unzip awscliv2.zip && ./aws/install
RUN  curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python3.9 get-pip.py && python3.9 -m pip install ansible boto3
RUN rm /usr/bin/python3 && ln -s /usr/bin/python3.9 /usr/bin/python3
RUN mkdir /downloads
VOLUME /ansible
WORKDIR /ansible
ENTRYPOINT /bin/bash
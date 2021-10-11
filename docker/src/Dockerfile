FROM ubuntu:21.10

ENV AWS_CDK_PROJECT="/aws-cdk-work"
ENV TZ=Europe/Warsaw
COPY files/requirements.txt /

RUN ln -snf /usr/share/zoneinfo/${TZ} /etc/localtime && \
    echo ${TZ} > /etc/timezone && \
    apt update && apt install -y vim python3-pip npm && \
    pip3 install --upgrade pip && \
    pip3 install --upgrade virtualenv && \
    npm install -g aws-cdk && \
    cdk --version

# Create and initialize AWS_CDK_PROJECT
RUN mkdir ${AWS_CDK_PROJECT} && \
    cd ${AWS_CDK_PROJECT} && \
    cdk init app --language python && \
    pip3 install -r ${AWS_CDK_PROJECT}/requirements.txt && \
    pip3 install -r /requirements.txt

WORKDIR ${AWS_CDK_PROJECT}
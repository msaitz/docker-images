FROM ubuntu:bionic-20210702

ENV TF_VERSION='1.0.2'
ENV AWSCLI_VERSION='2.0.30'

# Install dependencies & utilities
RUN apt-get update --no-install-recommends \
    && apt-get install -y --upgrade curl jq unzip less groff

# Install Terraform
RUN curl https://releases.hashicorp.com/terraform/${TF_VERSION}/terraform_${TF_VERSION}_linux_amd64.zip -o tf.zip \
    && unzip tf.zip && mv terraform /usr/local/bin

# Install awscli v2
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-${AWSCLI_VERSION}.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip && ./aws/install

# Do some cleanup
RUN apt remove -y unzip curl \
    && apt-get clean \
    && apt autoremove -y \
    && rm -rfv /var/lib/apt/lists/* *.zip aws*

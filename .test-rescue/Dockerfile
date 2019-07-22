FROM ubuntu:16.04
ARG GITHUB_TOKEN
ARG FULL_REPOSITORY_NAME
SHELL ["/bin/bash", "-c"]

# Install dependencies
RUN apt-get update
RUN apt-get install -y wget gnupg curl git libpq-dev
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RUN curl -sSL https://get.rvm.io | bash -s stable
RUN source /etc/profile.d/rvm.sh
RUN /usr/local/rvm/bin/rvm install 2.6.2
RUN git clone https://x-access-token:${GITHUB_TOKEN}@github.com/${FULL_REPOSITORY_NAME}.git
RUN PATH="/usr/local/rvm/rubies/ruby-2.6.2/bin:$PATH" gem install rubygems-bundler
RUN cd rspec-core && PATH="/usr/local/rvm/rubies/ruby-2.6.2/bin:$PATH" bundle
RUN rm -r rspec-core

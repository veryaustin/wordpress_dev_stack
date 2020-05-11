# Use Latest Wordpress
FROM wordpress:latest

RUN apt-get update
RUN apt-get install -y ca-certificates curl git &&\
  rm -rf /var/lib/apt/lists/*
RUN curl -Lsf 'https://storage.googleapis.com/golang/go1.8.3.linux-amd64.tar.gz' | tar -C '/usr/local' -xvzf -
ENV PATH /usr/local/go/bin:$PATH
RUN go get github.com/mailhog/mhsendmail
RUN cp /root/go/bin/mhsendmail /usr/local/bin/mhsendmail

COPY ./configs/uploads.ini /usr/local/etc/php/conf.d/uploads.ini
COPY ./configs/mailhog.ini /usr/local/etc/php/conf.d/mailhog.ini


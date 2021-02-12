FROM alpine:3.4
LABEL MAINTAINER Naba Das <nabad600@gmail.com>

WORKDIR /app
VOLUME /app

RUN apk add --update mysql mysql-client && rm -f /var/cache/apk/*

# These lines moved to the end allow us to rebuild image quickly after only these files were modified.
COPY startup.sh /startup.sh
RUN chmod +x /startup.sh
COPY my.cnf /etc/mysql/my.cnf

EXPOSE 3306
CMD ["/startup.sh"]
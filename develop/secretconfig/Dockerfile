FROM busybox

COPY ssmtp.conf /etc/ssmtp/ssmtp.conf
COPY ssl /etc/nginx/ssl
COPY ssh /var/www/.ssh
COPY ssh /root/.ssh
COPY secretconfig.sh /usr/local/bin/secretconfig

# Workaround for boot2docker issue #581, see
# https://github.com/boot2docker/boot2docker/issues/581
# Assume www-data user+group to use 1000 as id:
RUN chown -R 1000:1000 /var/www
RUN chmod 600 /var/www/.ssh/*
RUN chmod 600 /root/.ssh/*
RUN chmod +x /usr/local/bin/secretconfig

VOLUME /etc/ssmtp
VOLUME /etc/nginx/ssl
VOLUME /var/www/.ssh
VOLUME /root/.ssh

ENTRYPOINT ["secretconfig"]

ARG MARIADB_VERSION=latest
FROM mariadb:10.4

# Set Timezone
ARG TZ=CEST
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && chown -R mysql:root /var/lib/mysql/

CMD ["mysqld"]

EXPOSE 3306
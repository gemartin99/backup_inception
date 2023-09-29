FROM debian:10.11

ENTRYPOINT ["tail" ,"-f", "/dev/null"]

RUN apt-get update && \
	apt-get install -y \
	mariadb-server

#CMD ["tail" ,"-f", "/dev/null"]

COPY conf/mariadb.conf /etc/mysql/mariadb.conf.d/50-server.cnf

RUN mkdir -p /var/run/mysqld \
	&& chown -R mysql:mysql /var/run/mysqld \
	&& chmod 777 /var/run/mysqld

#CMD ["tail" ,"-f", "/dev/null"]

EXPOSE 3306

COPY ./tools/mariadb.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/mariadb.sh

RUN mysql_install_db

#CMD ["tail" ,"-f", "/dev/null"]

ENTRYPOINT [ "/usr/local/bin/mariadb.sh" ]

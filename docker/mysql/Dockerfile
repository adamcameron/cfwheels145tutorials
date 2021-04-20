FROM mysql:8

COPY ./docker-entrypoint-initdb.d/ /docker-entrypoint-initdb.d/
COPY ./conf/logging.cnf /etc/mysql/conf.d/
RUN chmod -R 644 /etc/mysql/conf.d/logging.cnf

EXPOSE 3306

CMD ["mysqld"]

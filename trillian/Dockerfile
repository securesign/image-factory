FROM registry.redhat.io/rhel8/mariadb-103

USER root

COPY examples/deployment/docker/db_server/mysql.cnf /etc/mysql/conf.d/trillian.cnf
COPY storage/mysql/schema/storage.sql /docker-entrypoint-initdb.d/storage.sql
COPY examples/deployment/docker/db_server/60-load-db.sh /usr/share/container-scripts/mysql/init/60-load-db.sh
RUN chmod -R 775 /docker-entrypoint-initdb.d && \
    chmod 644 /etc/mysql/conf.d/trillian.cnf && \
    chmod 775 /usr/share/container-scripts/mysql/init/60-load-db.sh
USER 1001
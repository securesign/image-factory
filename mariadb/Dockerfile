# Use the RHEL 8 UBI as the base image
FROM registry.access.redhat.com/ubi8/ubi

# Set the environment variables
ENV MYSQL_USER=mysql \
    MYSQL_DATA_DIR=/var/lib/mysql \
    MYSQL_RUN_DIR=/run/mysqld \
    MYSQL_LOG_DIR=/var/log/mysql \
    MYSQL_ROOT_PASSWORD=your_password

# Install MariaDB 10.2 server and client from the MariaDB repository
RUN yum install -y https://downloads.mariadb.com/MariaDB/mariadb_repo_setup && \
    rpm --import https://yum.mariadb.org/RPM-GPG-KEY-MariaDB && \
    yum-config-manager --add-repo https://mariadb.org/mariadb/repo/10.2/rhel8-amd64 && \
    yum install -y MariaDB-server MariaDB-client

# Copy the configuration file to the container
COPY my.cnf /etc/my.cnf

# Create the necessary directories
RUN mkdir -p ${MYSQL_RUN_DIR} ${MYSQL_LOG_DIR} && \
    chown -R ${MYSQL_USER}:${MYSQL_USER} ${MYSQL_DATA_DIR} ${MYSQL_RUN_DIR} ${MYSQL_LOG_DIR}

# Change the working directory
WORKDIR /var/lib/mysql

# Expose the MySQL/MariaDB port
EXPOSE 3306

# Start the MariaDB server
CMD ["mysqld"]


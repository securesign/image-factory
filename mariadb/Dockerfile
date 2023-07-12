# Use the RHEL 8 UBI as the base image
FROM registry.access.redhat.com/ubi8/ubi

# Set the environment variables
ENV MYSQL_USER=mysql \
    MYSQL_DATA_DIR=/var/lib/mysql \
    MYSQL_RUN_DIR=/run/mysqld \
    MYSQL_LOG_DIR=/var/log/mysql \
    MYSQL_ROOT_PASSWORD=your_password

# Install MariaDB server and client
RUN yum install -y mariadb-server mariadb-client

# Create the necessary directories
RUN mkdir -p ${MYSQL_RUN_DIR} ${MYSQL_LOG_DIR} && \
    chown -R ${MYSQL_USER}:${MYSQL_USER} ${MYSQL_DATA_DIR} ${MYSQL_RUN_DIR} ${MYSQL_LOG_DIR}

# Change the working directory
WORKDIR /var/lib/mysql

# Expose the MySQL/MariaDB port
EXPOSE 3306

# Start the MariaDB server
CMD ["mysqld"]


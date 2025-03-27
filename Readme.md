# Docker Compose Setup

This repository contains several `docker-compose.yml` configurations for setting up different services like MongoDB, MySQL, PostgreSQL, Redis, and Kafka. These configurations are useful for quickly spinning up instances of these services for development or testing purposes.

## Services

### MongoDB
- **Version**: 3.1
- **Image**: `mongo:latest`
- **Ports**: 27017:27017
- **Environment Variables**:
  - `MONGO_INITDB_ROOT_USERNAME`
  - `MONGO_INITDB_ROOT_PASSWORD`
  - `MONGO_INITDB_DATABASE`
- **Volumes**: `./db_data/:/data/db/`

### MySQL
- **Version**: 3.3
- **Image**: `mysql/mysql-server:8.0`
- **Ports**: 3306:3306
- **Environment Variables**:
  - `MYSQL_DATABASE`
  - `MYSQL_ROOT_PASSWORD`
  - `MYSQL_ROOT_HOST`

### PostgreSQL
- **Version**: 3.9
- **Image**: `postgres:15-alpine`
- **Ports**: 5432:5432
- **Environment Variables**:
  - `POSTGRES_PASSWORD`
  - `POSTGRES_USER`
  - `POSTGRES_DB`
- **Volumes**: `/Users/amittiwari/Infra/dock-containers/postgres:/var/lib/postgresql/data`

### Redis
- **Version**: 3.6
- **Image**: `redis/redis-stack-server:latest`
- **Ports**: 6379:6379
- **Environment Variables**:
  - `REDIS_ARGS`
- **Volumes**: `/Users/amittiwari/Infra/dock-containers/redis/redis_data:/data`
- **Healthcheck**: `redis-cli --raw incr ping`

### Kafka
- **Version**: 2
- **Images**: 
  - Zookeeper: `confluentinc/cp-zookeeper:latest`
  - Kafka: `confluentinc/cp-kafka:latest`
- **Ports**:
  - Zookeeper: 22181:2181
  - Kafka: 29092:29092
- **Environment Variables**:
  - `ZOOKEEPER_CLIENT_PORT`
  - `ZOOKEEPER_TICK_TIME`
  - `KAFKA_BROKER_ID`
  - `KAFKA_ZOOKEEPER_CONNECT`
  - `KAFKA_ADVERTISED_LISTENERS`
  - `KAFKA_LISTENER_SECURITY_PROTOCOL_MAP`
  - `KAFKA_INTER_BROKER_LISTENER_NAME`
  - `KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR`

## Usage

To start any of the services, navigate to the respective directory and run:

```bash
docker-compose up
```

Ensure that Docker is installed and running on your machine before executing the command.

## Notes

- Change the default passwords in the environment variables for security purposes.
- Adjust volume paths according to your system configuration.

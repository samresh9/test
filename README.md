# test
# Project Title

A brief description of what this project does and who it's for


## Description

<!-- This project is the backend for the Environmental & Social Resource Hub, built with NestJS and TypeORM. It includes features such as database migration and seeding, job queues using Bull, document indexing with Elasticsearch and FSCrawler, file storage with MinIO, and more. -->

### Key Technologies:

- **NestJS**: A progressive Node.js framework for building efficient, reliable, and scalable server-side applications.
- **TypeORM with Postgres**: An ORM for TypeScript and JavaScript that supports various databases and allows for database migrations.
- **Redis & Bull**: Redis is used as the data store for Bull, which is a Node.js queue library for handling background jobs.
- **Elasticsearch & FSCrawler**: Elasticsearch is used for document indexing and search, with FSCrawler providing a bridge to index file systems into Elasticsearch.
- **MinIO**: A high-performance, S3-compatible object storage service for storing files and other data.
- **Swagger**: Provides interactive API documentation.
- **Husky**: Used for managing pre-commit hooks to maintain code quality.

This backend service manages and indexes Environmental and Social resources, making it easier to access and interact with the data through a well-documented API.

## Documentation
### API Documentation

The API documentation is provided using **Swagger**. It offers an interactive interface to explore and test the API endpoints, making it easier to understand the available functionalities.

To access the API documentation, navigate to the following route in your browser:

[Documentation](https://linktodocumentation)


## Installation
Follow these steps to install and set up the Application:

1. **Clone the Repository**  
   First, clone the repository to your local machine or server using the following command:

```bash
$ git clone <repository-url>
```
2. **Navigate to the Project Directory**
Change your directory to the root of the project where the codebase is located:
  ```bash
$ cd <project-directory>
```
Replace <project-directory> with the actual path of the project folder.

3. **Install Dependencies**
Install all the required dependencies using Yarn:

```bash
$ yarn install
```
This will install all necessary Node.js packages specified in the package.json file.

4. **Environment Configuration**
Rename the .env.example file to .env in the root project directory. Update the .env file with your specific configuration values for the environment variables.

```bash
$ mv .env.example .env
```
Fill in all the required environment variables as specified in the 
[Configuration](#configuration) section.
## Running the App
Follow these steps to run the application:

1. **Start the Application** 
Use one of the following commands based on your environment:

```bash
# development
$ yarn run start

# development with watch mode
$ yarn run start:dev

# production mode
$ yarn run start:prod
```
- start: Runs the application in development mode.
- start:dev: Runs the application in development mode with file watching for automatic restarts.
- start:prod: Runs the application in production mode.

2. **Run Database Migrations**
After starting the application, run the following command to apply any pending database migrations:
```bash
$ yarn migration
```
This ensures your database schema is up-to-date with the current application structure.

3. **Seed Initial Data**
To populate the database with initial data (super admin accounts and other essential records such as role-permission data and more), run the seeder command:
```bash
$ yarn seed
```
This will execute the seeder scripts to insert predefined data into your database.
## Database Migration Configuration and Seeding

### Migration
1. **Generate a New Migration**
- On Linux/macOS:
```bash
$ npm run migration:generate --name="migration_name"
```
- On Windows:
```bash
$ npm run migration:generate:win --name="migration_name"

```
Replace "migration_name" with a descriptive name for the migration, which will generate a new migration file.

2. **Run Migrations**   
Apply the migrations to update your database schema:
```bash
$ npm run migration
```
This command will execute all pending migrations, ensuring your database schema matches the current application code.

3. **Generate a Skeleton Migration File**     
 If you need to create a migration manually, you can generate a skeleton migration file:
```bash
$ npm run migration --name="skeleton_migration_name"
```
Replace "skeleton_migration_name" with the desired name for the migration.

4. **Revert the Latest Migration**     
If you need to undo the most recent migration, use the following command:
```bash
$ npm run migration:revert
```
Note: This command only reverts the latest migration. Use with caution.

### Seeding

1. **Update Seeder Files**    
Make any necessary changes to your seeder scripts located in the seeder directory.

2. **Run the Seeder**     
Execute the following command to seed your database:
```bash
$ yarn run seed
```
This will insert the data defined in your seeder files into the database, ensuring that your application has the necessary data to function correctly.
<a id="configuration"></a>
## Configuration
To run the application, you need to set up several services and provide configuration through environment variables. Below are the required environment variables and suggestions for installing the necessary services.

### Required Environment Variables

#### General Configuration
- `APP_PORT`: Port on which the application will run (e.g., `3000`).
- `NODE_ENV`: Environment mode (`development`, `production`, etc.).
- `ADMIN_PASSWORD`: Default password for the super admin account.

#### API and Documentation
- `API_URL`: Base URL of the API (e.g., `http://localhost:3000`).
- `API_DOCUMENTATION`: URL for accessing API documentation with Swagger (e.g., `/api/v1/docs`).

#### Database Configuration
- `DATABASE_URL`: Connection string for PostgreSQL. It should include the protocol, username, password, host, port, and database name (e.g., `postgres://user:password@localhost:5432/mydatabase`).

#### JWT Configuration
- `JWT_SECRET`: Secret key for signing JWT tokens.
- `JWT_EXPIRE_IN`: Expiration time for JWT tokens (e.g., `1h`).
- `JWT_SECRET_PASSWORD_RESET`: Secret key for signing password reset tokens.
- `JWT_PASSWORD_RESET_EXPIRE_IN`: Expiration time for password reset tokens (e.g., `15m`).
- `JWT_REFRESH_SECRET`: Secret key for signing JWT refresh tokens.
- `JWT_REFRESH_EXPIRE_IN`: Expiration time for refresh tokens (e.g., `7d`).

#### Mail Configuration
- `MAIL_PORT`: Port for the mail server (e.g., `587`).
- `MAIL_HOST`: Mail server host (e.g., `smtp.mailtrap.io`).
- `MAIL_USERNAME`: Username for the mail server.
- `MAIL_PASSWORD`: Password for the mail server.
- `FROM_EMAIL`: Default sender email address.

#### Redis Configuration
- `REDIS_HOST`: Host of the Redis server (e.g., `localhost`).
- `REDIS_PORT`: Port of the Redis server (e.g., `6379`).
- `REDIS_PASSWORD`: Password for Redis (if any).

#### MinIO Configuration
- `MINIO_ENDPOINT`: Endpoint for the MinIO server (e.g., `localhost`).
- `MINIO_PORT`: Port for the MinIO server (e.g., `9000`).
- `MINIO_ACCESS_KEY`: Access key for MinIO.
- `MINIO_SECRET_KEY`: Secret key for MinIO.
- `MINIO_USE_SSL`: Whether to use SSL with MinIO (true/false).
- `MINIO_BUCKET`: Default bucket name for MinIO.
- `MINIO_REGION`: Region for the MinIO bucket (e.g., `us-east-1`).

#### Elasticsearch and FSCrawler Configuration
- `FSCRAWLER_API`: URL for the FSCrawler API (e.g., `http://localhost:8080`).
- `ELASTICSEARCH_URL`: URL for the Elasticsearch instance (e.g., `http://localhost:9200`).
- `ELASTICSEARCH_USERNAME`: Username for Elasticsearch authentication.
- `ELASTICSEARCH_PASSWORD`: Password for Elasticsearch authentication.
- `ELASTIC_INDEX_NAME`: Name of the Elasticsearch index (e.g., `idx`).

#### Other Configurations
- `PASSWORD_RESET_URL`: URL to redirect users for password reset.
- `CAPTCHA_SECRET`: Secret key for CAPTCHA verification.
- `CAPTCHA_VERIFICATION_URL`: URL for verifying CAPTCHA.
- `CONTACT_US_TO_MAIL`: Email address for the contact us form.
- `EMAIL_VERIFY_URL`: URL to redirect users for email verification.

### Service Installation
You can install and run the necessary services either locally or using [Docker](https://www.docker.com/).

#### Required Services

    Redis: For caching and background processing.
    MinIO: For file storage.
    Elasticsearch: For full-text search and indexing.
    FSCrawler: For indexing documents into Elasticsearch.
    PostgreSQL: For the application's relational database.

#### Local Installation
Install the services on your local machine and provide the required configuration through environment variables.
#### Using Docker
Alternatively, use Docker to simplify the setup and management of these services. Docker allows you to run each service in an isolated container. Configure the environment variables accordingly to match your Docker setup.

#### Elasticsearch and FSCrawler with Docker Compose:
You can use Docker Compose to set up Elasticsearch, FSCrawler, and Kibana together. Below is an example Docker Compose setup for these services:

```
services:
  setup:
    image: docker.elastic.co/elasticsearch/elasticsearch:${STACK_VERSION}
    volumes:
      - certs:/usr/share/elasticsearch/config/certs
    user: "0"
    command: >
      bash -c '
        if [ x${ELASTIC_PASSWORD} == x ]; then
          echo "Set the ELASTIC_PASSWORD environment variable in the .env file";
          exit 1;
        elif [ x${KIBANA_PASSWORD} == x ]; then
          echo "Set the KIBANA_PASSWORD environment variable in the .env file";
          exit 1;
        fi;
        if [ ! -f certs/ca.zip ]; then
          echo "Creating CA";
          bin/elasticsearch-certutil ca --silent --pem -out config/certs/ca.zip;
          unzip config/certs/ca.zip -d config/certs;
        fi;
        if [ ! -f certs/certs.zip ]; then
          echo "Creating certs";
          echo -ne \
          "instances:\n"\
          "  - name: elasticsearch\n"\
          "    dns:\n"\
          "      - elasticsearch\n"\
          "      - localhost\n"\
          "    ip:\n"\
          "      - 127.0.0.1\n"\
          > config/certs/instances.yml;
          bin/elasticsearch-certutil cert --silent --pem -out config/certs/certs.zip --in config/certs/instances.yml --ca-cert config/certs/ca/ca.crt --ca-key config/certs/ca/ca.key;
          unzip config/certs/certs.zip -d config/certs;
        fi;
        echo "Setting file permissions"
        chown -R root:root config/certs;
        find . -type d -exec chmod 750 \{\} \;;
        find . -type f -exec chmod 640 \{\} \;;
        echo "Waiting for Elasticsearch availability";
        until curl -s --cacert config/certs/ca/ca.crt https://elasticsearch:9200 | grep -q "missing authentication credentials"; do sleep 30; done;
        echo "Setting kibana_system password";
        until curl -s -X POST --cacert config/certs/ca/ca.crt -u elastic:${ELASTIC_PASSWORD} -H "Content-Type: application/json" https://elasticsearch:9200/_security/user/kibana_system/_password -d "{\"password\":\"${KIBANA_PASSWORD}\"}" | grep -q "^{}"; do sleep 10; done;
        echo "All done!";
      '
    healthcheck:
      test: ["CMD-SHELL", "[ -f config/certs/elasticsearch/elasticsearch.crt ]"]
      interval: 1s
      timeout: 5s
      retries: 120

  elasticsearch:
    depends_on:
      setup:
        condition: service_healthy
    image: docker.elastic.co/elasticsearch/elasticsearch:${STACK_VERSION}
    volumes:
      - certs:/usr/share/elasticsearch/config/certs
      - esdata:/usr/share/elasticsearch/data
    ports:
      - ${ES_PORT}:9200
    environment:
      - node.name=elasticsearch
      - cluster.name=${CLUSTER_NAME}
      - cluster.initial_master_nodes=elasticsearch
      - ELASTIC_PASSWORD=${ELASTIC_PASSWORD}
      - bootstrap.memory_lock=true
      - xpack.security.enabled=true
      - xpack.security.http.ssl.enabled=true
      - xpack.security.http.ssl.key=certs/elasticsearch/elasticsearch.key
      - xpack.security.http.ssl.certificate=certs/elasticsearch/elasticsearch.crt
      - xpack.security.http.ssl.certificate_authorities=certs/ca/ca.crt
      - xpack.security.http.ssl.verification_mode=certificate
      - xpack.security.transport.ssl.enabled=true
      - xpack.security.transport.ssl.key=certs/elasticsearch/elasticsearch.key
      - xpack.security.transport.ssl.certificate=certs/elasticsearch/elasticsearch.crt
      - xpack.security.transport.ssl.certificate_authorities=certs/ca/ca.crt
      - xpack.security.transport.ssl.verification_mode=certificate
      - xpack.license.self_generated.type=${LICENSE}
    mem_limit: ${MEM_LIMIT}
    ulimits:
      memlock:
        soft: -1
        hard: -1
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "curl -s --cacert config/certs/ca/ca.crt https://localhost:9200 | grep -q 'missing authentication credentials'",
        ]
      interval: 10s
      timeout: 10s
      retries: 120

  kibana:
    depends_on:
      elasticsearch:
        condition: service_healthy
    image: docker.elastic.co/kibana/kibana:${STACK_VERSION}
    volumes:
      - certs:/usr/share/kibana/config/certs
      - kibanadata:/usr/share/kibana/data
    ports:
      - ${KIBANA_PORT}:5601
    environment:
      - SERVERNAME=kibana
      - ELASTICSEARCH_HOSTS=https://elasticsearch:9200
      - ELASTICSEARCH_USERNAME=kibana_system
      - ELASTICSEARCH_PASSWORD=${KIBANA_PASSWORD}
      - ELASTICSEARCH_SSL_CERTIFICATEAUTHORITIES=config/certs/ca/ca.crt
      - ENTERPRISESEARCH_HOST=http://enterprisesearch:${ENTERPRISE_SEARCH_PORT}
    mem_limit: ${MEM_LIMIT}
    healthcheck:
      test:
        [
          "CMD-SHELL",
          "curl -s -I http://localhost:5601 | grep -q 'HTTP/1.1 302 Found'",
        ]
      interval: 10s
      timeout: 10s
      retries: 120

  # FSCrawler
  fscrawler:
    image: dadoonet/fscrawler:$FSCRAWLER_VERSION
    container_name: fscrawler
    restart: always
    volumes:
      - ../../test-documents/src/main/resources/documents/:/tmp/es:ro
      - ${PWD}/config:/root/.fscrawler
      - ${PWD}/logs:/usr/share/fscrawler/logs
      - ${PWD}/external:/usr/share/fscrawler/external
    depends_on:
      elasticsearch:
        condition: service_healthy
    ports:
      - ${FSCRAWLER_PORT}:8080
    command: fscrawler idx --restart --rest

volumes:
  certs:
    driver: local
  esdata:
    driver: local
  kibanadata:
    driver: local

```
You can either set up these services locally and provide the necessary environment variables or use Docker containers to handle these services and configure the environment variables accordingly.



#### Docker Compose environment variables
Before running your services, configure the following environment variables in your .env file or directly in your environment:

- `ELASTIC_PASSWORD`: Set the password for the 'elastic' user. The password must be at least 6 characters long.

- `KIBANA_PASSWORD`: Set the password for the 'kibana_system' user. This password should also be at least 6 characters long.

- `STACK_VERSION`: Define the version of Elastic products you want to use, such as Elasticsearch and Kibana.

- `CLUSTER_NAME`: Set the name of your Elasticsearch cluster.

- `LICENSE`: Choose the type of license to use. Set to basic for the free license or trial to automatically start a 30-day trial.

- `ES_PORT`: Specify the port to expose the Elasticsearch HTTP API to the host. The format should be host_port:container_port.

- `KIBANA_PORT`: Specify the port to expose Kibana to the host.

- `MEM_LIMIT`: Set the memory limit for the Elasticsearch container. This value is in bytes and should be adjusted based on the available memory on the host machine.

- `FSCRAWLER_PORT`: Define the port to expose FSCrawler to the host.

- `FSCRAWLER_VERSION`: Specify the version of FSCrawler you want to use.

- `ENTERPRISE_SEARCH_PORT`: Set the port for exposing Enterprise Search to the host.

- `ENCRYPTION_KEYS`: Provide encryption keys for securing Enterprise Search.

- `PWD`: Set the working directory for FSCrawler, where it will look for configuration files and other related data.

These variables should be defined in your environment or within a .env file to ensure that the services run correctly when using Docker Compose.

NOTE:For more detail about Elasticsearch and FSCrawler setup, you can refer to the official FS Crawler Docker Compose guide to set up these services in containers:
[Elasticsearch and FSCrawler with Docker Compose](https://fscrawler.readthedocs.io/en/latest/installation.html#using-docker-compose) 
## Git Hooks and Husky


We utilize Husky, a Git hook tool, to enforce certain actions and maintain a consistent workflow within our project. Git hooks are scripts that run before or after specific Git events.



- **Pre-commit Hook**: We have setup the pre-commit hook that runs code formatting scripts and linters to ensure code consistency before committing changes.

Please ensure that your code meets the required standards and passes the necessary checks before committing or pushing changes.

---

## Running Tests

1. **Running Unit Tests**
```bash
$ yarn run test
```

2. **Running End-to-End (E2E) Testss**
```bash
$ yarn run test:e2e
```

3. **Running Test Coverage**
```bash
$ yarn run test:cov
```

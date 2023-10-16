# Spring Flyway
Example using Flyway in spring

### Dependencies
* Docker
* Docker Compose
* Java 17

### Services to run
* Flyway Service
* Postgres

### To Run with Docker

Execute in root directory:

```bash
sudo docker-compose up -d 
```

##### Scripts to see Flyway operation in Docker

1. Access postgres container

```bash
sudo docker exec -it postgres bash
```

2. Connect in postgres bash

```bash
psql -U postgres -h localhost -d flyway
```

3. To see Flyway registry versions

```bash
select * from public.flyway_schema_history;
```

4. To see Flyway script run

```bash
select * from public.person;
```

##### Docker configurations

* In root directory have a file with name init.sql, it will be executed when init postgres service. Your goal is create database with name "flyway".
* To change properties access file "docker-compose.yml" in root directory.

### To run manually

Supports to run Flyway manually

* Info: Prints current status/version of a database schema. It prints which migrations are pending, which migrations have been applied, the status of applied migrations, and when they were applied.
* Migrate: Migrates a database schema to the current version. It scans the classpath for available migrations and applies pending migrations.
* Baseline: Baselines an existing database, excluding all migrations, including baselineVersion. Baseline helps to start with Flyway in an existing database. Newer migrations can then be applied normally.
* Validate: Validates current database schema against available migrations.
* Repair: Repairs metadata table.
* Clean: Drops all objects in a configured schema. Of course, we should never use clean on any production database.

To run access project directory "flyway" and run 

```bash
./mvnw flyway:{flyway_support_command}
```
### To create new Flyway SQL

1. Access directory "db/migration" in project
2. Create new file with next version using specific name:

For versioned scripts

```bash
 V{version}__{description}.sql 
```

For undo scripts

```bash
  U{version}__{description}.sql 
```

For repeatable scripts

```bash
  R__{description}.sql 
```



## License

This application is available under the
[MIT license](https://opensource.org/licenses/MIT).

 












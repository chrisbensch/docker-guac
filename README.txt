creating the database initialization script:
  docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --mysql > guac_db.sql

Bringing the db container up:
  docker-compose -f docker-compose.yml mariadb up -d

Copying db initialization script into the container:
  docker cp guac_db.sql guacdb:/guac_db.sql

Opening a shell and initializing the db:
  docker exec -it guacdb bash
  cat /guac_db.sql | mysql -u root -p guacamole_db
  exit

Shutting down db container:
  docker-compose down
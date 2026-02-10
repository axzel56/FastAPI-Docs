Docker Compose is a tool for defining and running multi-container Docker applications. It simplifies the management of complex applications that require multiple services, such as web server, a database and a caching system all working together.

Instead of running multiple `docker run` commands with various flags and parameters for each service, Docker compose allows to define entire application in a single YAML File.
Typically Named: `compose.yml`  or `docker-compose.yml`
`docker compose down` can stop and remove all the containers, networks and volumes related to the application.


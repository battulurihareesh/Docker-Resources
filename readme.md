This project responsible to make availability of resources used by nuvizz projects, using docker images.

Prerequisite:
=================
Install "Docker Desktop".
Available at : https://docs.docker.com/docker-for-windows/install/

How to use:
=================
- open cmd, and point to location where we have docker-compose.yml file.
- make sure data and its sub folders (empty) availabile in same location.

- Start Command: 
	docker-compose up -d
	* downloads all the images first time, if not availabile, and runs the services as a container.

- Verify Command :
	docker ps
	* shows all active containers running 

- Stop Command (Recommend to use):
	docker-compose stop
	* Stops all the services, but containers won't be removed. 

- Delete Command (Not Recommend to use):
	docker-compose down
	* Stops all the services, and removes the containers. We can observe in docker-compose that, Active-MQ, RabbitMQ data
	is not mounted.... so using this command removes queue names and data


URL, Port, Credentials :
=========================
Below info is based on docker-compose.yml, it can be customized.

Mysql : 
	port 					: 3306
	Root passowrd 			: root
	Root username 			: root
	command to connect  	: docker-compose exec mysql bash -c "mysql -u root -proot"
	How to upload dump  	: unzip dump and add extension .sql, and place file in "data\mysql\db" path where we have docker-compose file. place command path till where we have "docker-compose.yml" file. Connect to DB using command: <docker-compose exec mysql bash -c "mysql -u root -proot">, and run "SOURCE /var/lib/mysql/SQLFileName.sql"

Mongo :
	port 					: 27017
	Root passowrd 			: root
	Root username 			: root
	command to connect  	: place command path till where we have "docker-compose.yml" file. Run command : <docker-compose exec mongo bash -c "mongo mongodb://root:root@localhost:27017">

RabbitMQ :
	URL 					: http://localhost:15672
	userName 				: guest
	password				: guest
	
ActiveMQ :
	URL 					: http://localhost:8161/admin
	userName 				: admin
	password				: admin
	
Couchbase :
	URL 					: http://localhost:8091
	Username, password 		: On first aceess, we need to do setup username, password, bucket creation ..etc

Elastic-search :
	Port 					: 9200
	userName				: elastic
	passowrd				: changeme

Kibana :
	URL 					: http://localhost:5601
	Username, password 		: no Cred Req by default
	
Redis :
	port 					: 6379
	command to connect  	: place command path till where we have "docker-compose.yml" file. Run command : <docker-compose exec redis bash -c "redis-cli">
	

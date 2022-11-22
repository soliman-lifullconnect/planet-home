.PHONY: build stop start restart logs logs-app app-login db-login server-login migrate keygenerate


build: stop 
	COMPOSER_DOCKER_CLI_BUILD=1 DOCKER_BUILDKIT=1 
	docker-compose build --build-arg USER_ID=$$(id -u) --build-arg GROUP_ID=$$(id -g) --build-arg USERNAME=$$(id -u -n) --build-arg GROUPNAME=$$(id -g -n) myapp
	docker-compose -f docker-compose.yml up --remove-orphans -d

stop:
	docker-compose -f docker-compose.yml down


start:
	docker-compose -f docker-compose.yml up --remove-orphans -d

restart: stop start

logs: 
	docker-compose -f docker-compose.yml planet-home_myapp_1 storage/logs --tail=10 -f $(c)

logs-app:
	docker-compose -f docker-compose.yml planet-home_myapp_1 storage/logs --tail=10 -f app

app-login:
	docker exec -it planet-home_myapp_1 /bin/bash

db-login:
	docker exec -it planet-home_mariadb_1 mysql -ularavel -p"laravel"

server-login:
	docker exec -it twoeyewear-nginx /bin/bash

migrate:
	docker-compose run app php artisan migrate


keygenerate:
	docker-compose exec app php artisan key:generate


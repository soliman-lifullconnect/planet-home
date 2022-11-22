.PHONY: build stop start restart logs logs-app app-login db-login migrate keygenerate serve npm_dev

# 1. Build your system before anything make
build: stop 
	COMPOSER_DOCKER_CLI_BUILD=1 DOCKER_BUILDKIT=1 
	docker-compose build --build-arg USER_ID=$$(id -u) --build-arg GROUP_ID=$$(id -g) --build-arg USERNAME=$$(id -u -n) --build-arg GROUPNAME=$$(id -g -n) app
	docker-compose -f docker-compose.yml up --remove-orphans -d

stop:
	docker-compose -f docker-compose.yml down

# 2. start paroject
start:
	docker-compose -f docker-compose.yml up --remove-orphans -d

restart: stop start

logs: 
	docker-compose -f docker-compose.yml app storage/logs --tail=10 -f $(c)

logs-app:
	docker-compose -f docker-compose.yml app storage/logs --tail=10 -f app

app-login:
	docker exec -it planet-home_app_1 /bin/bash

db-login:
	docker exec -it planet-home_mariadb_1 mysql -hmariadb -ularavel -plaravel


# 3. First do the migrate before anything
migrate:
	docker-compose run app php artisan migrate

# 3. After migrate do this make before anything else
keygenerate:
	docker-compose exec app php artisan key:generate

# 4. serve project
serve:
	docker-compose run app php artisan serve	

# 
npm_dev:
	docker-compose run app npm run dev


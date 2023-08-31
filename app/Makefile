test:
	docker-compose -f ../docker-compose.yml run --rm app sh -c "python manage.py test"

user:
	docker-compose -f ../docker-compose.yml run --rm app sh -c "python manage.py createsuperuser"

migrations:
	docker-compose -f ../docker-compose.yml run --rm app sh -c "python manage.py makemigrations"

migrate:
	docker-compose -f ../docker-compose.yml run --rm app sh -c "python manage.py migrate"

up:
	docker-compose -f ../docker-compose.yml up

build:
	docker-compose -f ../docker-compose.yml build

format:
	brunette ../app --config=setup.cfg

dev:
	git checkout dev
	git pull origin dev
	pip install -r ../etc/requirements.txt
	make migrate

check:
	python manage.py makemigrations --dry-run --check
	python manage.py test --noinput
	brunette ../app --check --diff --config=setup.cfg

ilocal:
	pip install -r ../etc/requirements.txt

init:
	make ilocal
	cp ../.env.sample ./app/core/.env
	cp ../.env.sample ./.env

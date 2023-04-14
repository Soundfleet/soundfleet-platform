# Soundfleet platform

## About

Start here if you want to explore Soundfleet project.

_Keep in mind  this repository is not meant to be deployed in any production environment._

## Requirements
1. [Docker](https://docs.docker.com/install/)

## How to run it?
1. Clone this repository:
```shell
git clone https://github.com/Soundfleet/soundfleet-platform.git
```
2. Go to cloned directory:
```shell
cd soundfleet-platform
```
2. Update submodules
* If it's the first time you check-out this repository run:
```shell
git submodule update --init --recursive
```
* then run:
```shell
git submodule update --recursive --remote
```
3. Run application:
```shell
docker-compose up --build
```
4. Run migrations inside soundfleet container:
```shell
python manage.py migrate
```
5. Create superuser inside soundfleet container:
```shell
python manage.py createsuperuser
```
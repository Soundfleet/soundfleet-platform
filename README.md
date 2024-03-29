# Soundfleet platform

## About

Start here if you want to explore Soundfleet project.

_Keep in mind  this repository is not meant to be deployed in any production environment._

## Requirements
1. [Docker](https://docs.docker.com/install/)

2. [docker-compose](https://docs.docker.com/compose/install/other/)

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

3. Create `.env` file inside root directory of this repo with following content:
```yaml
DOMAIN=a.b.c.d:8000
SOUNDFLEET_URL=http://a.b.c.d:8000
CORS_ORIGIN_WHITELIST=http://a.b.c.d:3000

# where a.b.c.d is IP address of your host
```

4. Run application:
```shell
docker-compose up --build
```
5. Run migrations inside soundfleet container:
```shell
python manage.py migrate
```
6. Create superuser inside soundfleet container:
```shell
python manage.py createsuperuser
```

## How to connect your RPi?
1. Flash your SD card with preferred distro (minimal raspbian is sufficient).

2. Install [salt minion](https://docs.saltproject.io/salt/install-guide/en/latest/)

3. Configure salt minion:
```yaml
# /etc/salt/minion
master: salt  # <- replace this to hostname of your salt master instance
```

```yaml
# /etc/salt/minion_id
<UUID of your device created via soundfleet dashboard>
```

4. Restart salt minion service:
```shell
sudo systemctl restart salt-minion
```

5. Connect device by accepting salt key from RPi, you can do this from soundfleet dashboard
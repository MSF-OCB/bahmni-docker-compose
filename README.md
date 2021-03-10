# bahmni-docker-compose

This repo contains several compose files.
The main `docker-compose.yml` file defines the base set-up, you can then add one of the following files:
1. `docker-compose.active.yml`: start an EMR behind Traefik, and request certificates from Let's Encrypt. Used when `mode = active`.
1. `docker-compose.passive.yml`: start an EMR without any web interface. Used when `mode = passive`.
2. `docker-compose.local_port.yml`: start an EMR with a local port exposed on localhost.

A typical command to start an active server, looks therefore like this:
```
docker-compose -f docker-compose.yml -f docker-compose.active.yml up -d
```

There are also two files to start a UAT version, these are independent of the main `docker-compose.yml` file.
You can start a UAT server like this:
```
docker-compose -f docker-compose.uat.yml up -d
```

## On the Bahmni server

Create the target directory in `/opt`:
```
sudo mkdir -p /opt/bahmni
```

Clone this repo:
```
git clone https://github.com/MSF-OCB/bahmni-docker-compose/ /opt/bahmni
```

And copy over the config file and edit it:
```
cp .env.template .env
vim .env
```

Pull the image, bring up the container and watch the logs:
```
docker-compose up -d
docker-compose logs -f
```


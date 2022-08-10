## Create Image

```bash
$ git clone ssh://git@github.com/AtsuhikoYamada/iwtsys_create_image.git
$ cd iwtsys_create_image
$ ./build.sh
```

## Share Image

```bash
$ docker login
$ docker push a2ymd/iwt-web
$ docker push a2ymd/iwt-db
$ docker save a2ymd/iwt-web >iwt-web.tar
$ docker save a2ymd/iwt-db >iwt-db.tar
```

## Delete Image

```bash
$ docker image prune -a
```

## Container structure

```bash
├── web
└── db
```

### web container

- Base image
  - [php](https://hub.docker.com/_/php):7.4-apache-buster
  - [composer](https://hub.docker.com/_/composer):2.0
  - [node](https://hub.docker.com/_/node):node:14-buster

### db container

- Base image
  - [mariadb](https://hub.docker.com/_/mariadb):10.8

#### Persistent MariaDB Storage

By default, the [named volume](https://docs.docker.com/compose/compose-file/#volumes) is mounted, so MariaDB data remains even if the container is destroyed.
If you want to delete MariaDB data intentionally, execute the following command.

```bash
$ docker-compose down -v && docker-compose up
```



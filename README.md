
# Laravel Development Container

## TL;DR

### Local workspace

```console
$ mkdir ~/myapp && cd ~/myapp
$ curl -LO https://raw.githubusercontent.com/runthis/docker-laravel/master/docker-compose.yml
$ docker-compose up
```

**Warning**: This quick setup is only intended for development environments. You are encouraged to change the insecure default credentials and check out the available configuration options for the [MariaDB container](https://github.com/bitnami/bitnami-docker-mariadb#readme) for a more secure deployment.


> This [CVE scan report](https://quay.io/repository/bitnami/laravel?tab=tags) contains a security report with all open CVEs. To get the list of actionable security issues, find the "latest" tag, click the vulnerability report link under the corresponding "Security scan" field and then select the "Only show fixable" filter on the next page.


## Purpose

The purpose of this fork is to use PHP 8 with this vendor. Vendor upstreams are merged every few weeks.



## Getting started

The quickest way to get started with the Laravel Development Container is using [docker-compose](https://docs.docker.com/compose/).

Begin by creating a directory for your Laravel application:

```console
mkdir ~/myapp
cd ~/myapp
```

Download the [docker-compose.yml](https://raw.githubusercontent.com/runthis/docker-laravel/master/docker-compose.yml) file in the application directory:

```console
$ curl -LO https://raw.githubusercontent.com/runthis/docker-laravel/master/docker-compose.yml
```

Finally launch the Laravel application development environment using:

```console
$ docker-compose up
```

Among other things, the above command creates a container service, named `myapp`, for Laravel development and bootstraps a new Laravel application in the application directory. You can use your favorite IDE for developing the application.

> **Note**
>
> If no application available at http://localhost:3005 and you're running Docker on Windows, you might need to uncomment `privileged` setting for `myapp` container. Later, re-launch the Laravel application development environment as stated before.

In addition to the Laravel Development Container, the [docker-compose.yml](https://raw.githubusercontent.com/runthis/docker-laravel/master/docker-compose.yml) file also configures a MariaDB service to serve as the database backend of your Laravel application, as well as a PHPMyAdmin service available at http://localhost:3010.

## Executing commands

Commands can be launched inside the `myapp` Laravel Development Container with `docker-compose` using the [exec](https://docs.docker.com/compose/reference/exec/) command.

> **Note**:
>
> The `exec` command was added to `docker-compose` in release [1.7.0](https://github.com/docker/compose/blob/master/CHANGELOG.md#170-2016-04-13). Please ensure that you're using `docker-compose` version `1.7.0` or higher.

The general structure of the `exec` command is:

```console
$ docker-compose exec <service> <command>
```

, where `<service>` is the name of the container service as described in the `docker-compose.yml` file and `<command>` is the command you want to launch inside the service.

Following are a few examples of launching some commonly used Laravel development commands inside the `myapp` service container.

- List all `artisan` commands:

  ```console
  $ docker-compose exec myapp php artisan list
  ```

- List all registered routes:

  ```console
  $ docker-compose exec myapp php artisan route:list
  ```

- Create a new application controller named `UserController`:

  ```console
  $ docker-compose exec myapp php artisan make:controller UserController
  ```

- Installing a new composer package called `phpmailer/phpmailer` with version `5.2.*`:

  ```console
  $ docker-compose exec myapp composer require phpmailer/phpmailer:5.2.*
  ```

## Special Thanks


We want to thank the following individuals for reporting vulnerabilities responsibly and helping improve the security of this container.

- Bitnami: [bitnami-docker-laravel](https://github.com/bitnami/bitnami-docker-laravel/)


## License

Copyright (c) 2015-2021 Bitnami

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

# Debian 13 — LAMP Server (WordPress-ready)

A lightweight, reproducible **Debian 13 virtual machine** provisioned with **Vagrant and libvirt**, running Apache2, MariaDB and PHP.

The environment is designed as a simple LAMP-stack deployment ready to host WordPress, with a basic `index.html` page and a dedicated `/info.php` endpoint that exposes the virtual machine's PHP configuration and system details.

## Virtual Machine Specifications

| Resource                | Configuration                  |
| ----------------------- | ------------------------------ |
| Operating System        | Debian 13 (`cloud-image/debian-13`) |
| Virtualization Provider | libvirt                        |
| Hostname                | `WordPress`                    |
| CPU                     | 4 vCPUs                        |
| Memory                  | 2 GB RAM                       |
| Private Network IP      | `192.168.33.12`                |
| Port Forwarding         | Guest `80` → Host `8080`       |
| Web Server              | Apache2                        |
| Database                | MariaDB                        |
| PHP                     | PHP with `libapache2-mod-php`  |
| Default Page            | `index.html`                   |
| System Information      | `/info.php`                    |

## Services

### Apache2

Apache2 is installed and configured to listen on ports `80` and `8080`.

The default website provides a simple `index.html` page that can be customized for the environment.

### MariaDB

MariaDB is installed as the database server, ready to be used by applications such as WordPress.

### PHP

PHP is installed together with the extensions commonly required by WordPress and other web applications:

`php-mysql`, `php-mbstring`, `php-xml`, `php-curl`, `php-zip`, `php-bcmath`, `php-intl`

### System Information Endpoint

The `/info.php` endpoint runs `phpinfo()` and provides information about the virtual machine's PHP and server environment.

For example:

```text
http://192.168.33.12/info.php
```

or, through the forwarded port from the host machine:

```text
http://localhost:8080/info.php
```

## Requirements

The following software is required on the host machine:

* Vagrant
* libvirt
* Vagrant Libvirt provider

## Usage

Clone the repository and enter the machine's directory:

```bash
git clone https://github.com/marmole3003/VagrantFiles.git
cd VagrantFiles/debian-13-lamp
```

Start the virtual machine:

```bash
vagrant up --provider=libvirt
```

Check the VM status:

```bash
vagrant status
```

Connect through SSH:

```bash
vagrant ssh
```

When the VM is running, access the web server at `http://192.168.33.12` or `http://localhost:8080`.

## VM Lifecycle

Stop the machine:

```bash
vagrant halt
```

Restart the machine:

```bash
vagrant reload
```

Re-run provisioning:

```bash
vagrant provision
```

Destroy the machine:

```bash
vagrant destroy
```

## Purpose

This environment provides a simple, reproducible LAMP deployment that can be used for **development, testing, infrastructure labs, and virtualization experiments**.

The configuration is intentionally lightweight while demonstrating how Vagrant can be used to provision a consistent Linux web-server environment.

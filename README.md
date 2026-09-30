# Debian 13 — Apache2 Web Server

A lightweight, reproducible **Debian 13 virtual machine** provisioned with **Vagrant and libvirt**, running an Apache2 web server.

The environment is designed as a simple and reproducible web-server deployment, with a clean `index.html` page and a dedicated `/info.php` endpoint that exposes the virtual machine's system specifications.

## Virtual Machine Specifications

| Resource                | Configuration |
| ----------------------- | ------------- |
| Operating System        | Debian 13     |
| Virtualization Provider | libvirt       |
| CPU                     | 2 vCPUs       |
| Memory                  | 4 GB RAM      |
| Web Server              | Apache2       |
| PHP                     | PHP           |
| Default Page            | `index.html`  |
| System Information      | `/info.php`   |

## Services

### Apache2

Apache2 is installed and configured as the web server.

The default website provides a clean `index.html` page that can be customized for the environment.

### System Information Endpoint

The `/info.php` endpoint provides information about the virtual machine's current environment and specifications.

For example:

```text
http://<vm-ip>/info.php
```

This endpoint can be useful for quickly verifying the resources and software environment assigned to the VM.

## Requirements

The following software is required on the host machine:

* Vagrant
* libvirt
* Vagrant Libvirt provider

## Usage

Clone the repository and enter the machine's directory:

```bash
git clone https://github.com/<marmole3003>/<VagrantFiles>.git
cd <VagrantFiles>/debian-13-apache
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

When the VM is running, access the Apache web server using the VM's configured IP address.

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

This environment provides a simple, reproducible Apache2 deployment that can be used for **development, testing, infrastructure labs, and virtualization experiments**.

The configuration is intentionally lightweight while demonstrating how Vagrant can be used to provision a consistent Linux web-server environment.


# Ansible Infrastructure Automation Lab

## Overview

This repository contains Ansible playbooks and supporting configuration
used to automate multi-node Linux infrastructure in a simulated
production environment.

The project demonstrates:

-   Multi-group inventory management
-   Rocky Linux and Ubuntu conditional logic
-   Idempotent service configuration
-   Tagged playbook execution
-   Automated package management and patching
-   Service configuration using handlers
-   Basic infrastructure segmentation (web, database, file servers)

The environment is hosted on a Proxmox-based virtualization platform and
includes multiple Linux virtual machines grouped by function.

------------------------------------------------------------------------

## Environment Structure

Inventory groups:

-   `web_servers`
-   `db_servers`
-   `file_servers`

Operating systems supported:

-   Rocky Linux
-   Ubuntu

------------------------------------------------------------------------

## Repository Structure

    ansible_repo/
    ├── ansible.cfg
    ├── inventory/
    │   └── hosts.ini
    ├── playbooks/
    │   ├── site.yml
    │   ├── common.yml
    │   ├── web.yml
    │   ├── db.yml
    │   └── file.yml
    ├── files/
    │   └── default_site.html
    └── README.md

------------------------------------------------------------------------

## What This Project Automates

### Common Tasks

-   System updates for Rocky and Ubuntu
-   Package cache updates

### Web Servers

-   Apache/httpd installation (Rocky/Ubuntu)
-   PHP installation
-   Service enablement and startup
-   Configuration modification using `lineinfile`
-   Conditional service restarts via handlers
-   Deployment of a default web page

### Database Servers

-   MariaDB installation for Rocky and Ubuntu

### File Servers

-   Samba installation

------------------------------------------------------------------------

## How to Run

Run full site deployment:

``` bash
ansible-playbook -i inventory/hosts.ini playbooks/site.yml
```

Run only web configuration:

``` bash
ansible-playbook -i inventory/hosts.ini playbooks/site.yml --tags apache
```

Limit execution to a specific host group:

``` bash
ansible-playbook -i inventory/hosts.ini playbooks/site.yml --limit web_servers
```

------------------------------------------------------------------------

## Automation Principles Demonstrated

-   Idempotent configuration management
-   Use of tags for selective execution
-   OS-based conditional task execution
-   Structured inventory grouping
-   Separation of concerns across playbooks
-   Version-controlled infrastructure as code

------------------------------------------------------------------------


## Author

Jeffrey Way Jr.  
RHCSA \| Security+ \| CCNA

VPS Basic Config
================

* Our VPS (Virtual Private Server) is registered with Contabo (a multinational cloud hosting provider).

* Our VPS is based in a Portsmouth Datacenter, this doesn't actually mean anything technical-wise - it's just a nice thing to know!

Requirements
----------------
- *This has been written assuming the VPS is running Ubuntu 22.04 (LTS) and is accessible via SSH.*
- *This guide assumes you are logged in as root. If not, prepend sudo to all commands.*

* Step 1: Uncomplicated Firewall
- *As this VPS is exposed to the internet, we have to setup a Firewall. Fortunately - Ubuntu comes with a suitable piece of software which we can just configure for our requirements. Further Documentation is available on the UFW Webpages.*

    * Check that UFW exists and is inactive ufw status
    * Set default to deny all incoming connections ufw default deny incoming
    * Allow SSH connections ufw allow 22
    * Allow HTTPS connections ufw allow https
    * Allow HTTP connections ufw allow http
    * Enable UFW ufw enable
    * Confirm that it's status is correct using ufw status, you should get something like below;
    
    .. list-table::
        :header-rows: 1

    * - To
        - Action
        - From
    * - 22
        - ALLOW
        - Anywhere
    * - 80/tcp
        - ALLOW
        - Anywhere
    * - 443
        - ALLOW
        - Anywhere
    * - 22 (v6)
        - ALLOW
        - Anywhere (v6)
    * - 80/tcp (v6)
        - ALLOW
        - Anywhere (v6)
    * - 443 (v6)
        - ALLOW
        - Anywhere (v6)


* Step 2: Install Nginx
- *As Ubuntu 22.04 is a LTS version of Ubuntu, it ships with packages which are now out of date. We want to be using up-do-date Nginx so that we can protect all our services behind it and worry slightly less about their security.*

- This guide has been derived from Step 5 of How To Forge's guide on installing a LEMP stack.

    * Import Nginx's Singing Key:
        - curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor \
        - | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null
    * Add the Repository for Nginx's stable version to Apt
        - echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg arch=amd64] \
        - http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
        - | sudo tee /etc/apt/sources.list.d/nginx.list
    * Update System Repositories: apt update
    * Install Nginx: apt install nginx
    * Verify that Nginx's version is greater than 1.18 (we are aiming for it to be around 1.24): nginx -v

* Step 3: Install PostgreSQL
- *PostgreSQL will be our Database Management System.*

* Again, as Ubuntu 22.04 ships with an older package, we have to add the new package's repository manually as described in the official documentation on installing PostgreSQL.

    * Create the fie repository configuration
        - sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
    * Import the repository signing key
        - wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    * Update the package lists
        - sudo apt-get update
    * Install the latest version of PostgreSQL
        - sudo apt-get -y install postgresql

    * As part of the installation process, a user postgres is created for the Operating System.

* Step 4: Creating the Additional User
- *An additional user is created for both the VPS and PostgreSQL so that root access does not have to be given out to the full team.*

    * Do this in two parts, fist create the user:

    * useradd -s /usr/bin/bash -m setap
    * Then set it's password.
    * Then create the user in Postgres and give it superuser access.
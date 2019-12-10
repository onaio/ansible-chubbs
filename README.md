Ansible: Chubbs [![Build Status](https://travis-ci.org/onaio/ansible-chubbs.svg?branch=master)](https://travis-ci.org/onaio/ansible-chubbs)
=========

This role installs and configures [Chubbs (PGRestAPI)](https://github.com/onaio/PGRestAPI). A Node.js REST API for PostgreSQL spatial entities.

Role Variables
--------------

Below is a list of some variables and the default values set. Get the full list of settable variables from the [defaults](./defaults/main.yml) file:

```yml
# The method to use to install the node dependencies
# Can be:
#  - archive (make sure you set chubbs_node_packages_archive_url)
#  - npm
chubbs_node_deps_install_method: "archive"

# The URL from where to get the archive with node dependencies
chubbs_node_packages_archive_url: "https://node-modules-backups.s3.eu-central-1.amazonaws.com/pgrestapi.zip"

# The version of Node.js to install (using NVM). Currently, Chubbs works with Node.js 0.10
chubbs_nvm_node_version: "v0.10.42"

# The version of PM2 to run Chubbs in. Chubbs currently supports PM2 2.4
chubbs_nvm_pm2_version: "2.4.6"
```

Dependencies
------------

Chubbs depends on the following roles:
 - [onaio.nvm](https://github.com/onaio/ansible-nvm)

Example Playbook
----------------

Here's an example Chubbs playbook:

```yml
- hosts: all
  roles:
    - role: ansible-chubbs
      chubbs_pgsql_db: "chubbs"
      chubbs_pgsql_user: "chubbs"
      chubbs_pgsql_password: "random strong password"
      chubbs_pgsql_host: "localhost"
      chubbs_cors_whitelist: ["https://ona.io", "http://localhost:3000"]
```

License
-------

Apache 2

[![Build Status](https://travis-ci.org/wtanaka/ansible-role-certbot.svg?branch=master)](https://travis-ci.org/wtanaka/ansible-role-certbot)
[![CircleCI](https://circleci.com/gh/wtanaka/ansible-role-certbot.svg?style=svg)](https://circleci.com/gh/wtanaka/ansible-role-certbot)

wtanaka.certbot
===============

Installs certbot command line tools for the letsencrypt certificate
authority

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: wtanaka.certbot
           # Read the TOS then uncomment this
           # letsencrypt_agree_tos: --agree-tos
           letsencrypt_email: example@example.com
           letsencrypt_webroot: /var/www/html
           # Uncomment to renew on every run (by default waits till 30
           # days till expiration)
           # letsencrypt_renew_by_default: --renew-by-default
           letsencrypt_domains:
           - wtanaka.com
           - www.wtanaka.com


Or you can include just the role, and configure it in

    PLAYBOOK
    - hosts: servers
      roles:
         - wtanaka.certbot

    HOST_VARS file:

    # Read the TOS then uncomment this
    # letsencrypt_agree_tos: --agree-tos
    letsencrypt_email: example@example.com
    letsencrypt_webroot: /var/www/html
    # Uncomment to renew on every run (by default waits till 30
    # days till expiration)
    # letsencrypt_renew_by_default: --renew-by-default
    letsencrypt_domains:
    - wtanaka.com
    - www.wtanaka.com

### `letsencrypt_fake_key`

Set to `True` in order to disable executing certbot and install a
self-signed key in each of the `letsencrypt_domains` directories.
Nothing will be installed if `letsencrypt_domains` is empty

For example, this could be used in an integration test environment or
in a testing or staging environment.

### `letsencrypt_domains`

This is a list of domain names to pass to certbot.

Example:

```
letsencrypt_domains:
- wtanaka.com
- www.wtanaka.com
```

Setting this to an empty list will disable executing certbot:

```
letsencrypt_domains: []
```

License
-------

GPLv2

Author Information
------------------

http://wtanaka.com/

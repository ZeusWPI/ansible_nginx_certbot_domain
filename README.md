NGINX certbot domain
=========

Ansible role to request letsencrypt certificates. Will check if the certificate is already present. If that's not the case it will request one for you.

Requirements
------------

A public IP address and the `ZeusWPI.nginx_cerbot_base` role.

Role Variables
--------------

Check out `defaults/main.yml`, I try to document each variable there.

This role will do a dry run if `certbot_dry_run` is set to `true`.

Dependencies
------------

- `ZeusWPI.nginx_certbot_base`

Example Playbook
----------------

This example will request one certificate for both `example.com`, `www.example.com` and `extra.example.com` with a rsa key-size of 4096 bits. This certificate will be available in `/etc/letsencrypt/live/example.com/`. Because this role depends on `ZeusWPI.nginx_certbot_base`, automatic renewal will be enabled.
```
    - hosts: servers
      roles:
         - role: ZeusWPI.nginx_certbot_domain
           letsencrypt_email: example@example.com
           letsencrypt_domain: example.com
           letsencrypt_key_size: 4096
           letsencrypt_extra_domains:
               - www.example.com
               - extra.example.com
           tags: certbot
```

License
-------

GNU General Public License v3.0

Author Information
------------------

For questions, clarifications or other chitchat, contact me at [maertensrien@gmail.com](mailto:maertensrien@gmail.com).


# Ansible playbooks

Automated server setup and configuration.

## Setup

Put the SSH public key into `/root/.ssh/authorized_keys`.

Install Python 2 since Python 3 is not yet supported for ansible:

```
sudo aptitude install ansible python2.7 python-simplejson
```

Best to be at the most up to date stable release, so work from a PPA:

```
sudo add-apt-repository ppa:ansible/ansible
```


## SSL with Let's Encrypt

Install or create the keys and certs for domains in:

```
/etc/letsencrypt
/etc/ssl
```

Creating a new cert for a domain is as easy as making sure the `public/.well-known` is symlinked and then running:
```
sudo letsencrypt certonly -a webroot --webroot-path=/var/apps/example.com/shared/public -d example.com -d www.example.com
```

Further reading:

* https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04
* https://certbot.eff.org/#ubuntuxenial-nginx
* https://community.letsencrypt.org/t/nginx-configuration-sample/2173
* https://mozilla.github.io/server-side-tls/ssl-config-generator/


## Run the playbooks

For app servers and mail servers:

```
ansible-playbook site.yml
```

Or just for a given server type:

```
ansible-playbook app-servers.yml
ansible-playbook mail-servers.yml
```

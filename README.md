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
sudo certbot certonly -a webroot --webroot-path=/var/apps/example.com/shared/public -d example.com -d www.example.com
```


Further reading:
* https://certbot.eff.org/lets-encrypt/ubuntubionic-nginx
* https://github.com/certbot/certbot/issues/6221#issuecomment-455641244


## Run the playbooks

For app servers:

```
ansible-playbook site.yml
```

Or just for a given server type:

```
ansible-playbook app-servers.yml
```


## TODO

```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update
sudo apt-get install nodejs yarn
```

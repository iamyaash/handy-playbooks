# Ansible Playbooks for Home Raspberry Devices

## Hugo Page Setup

1. **Create a user** named `hugo-pages` and add them to sudo group as well.
```sh
sudo adduser hugo-pages
```

- Add `hugo-pages` in `sudo` group:
```sh
sudo visudo
```

- Add this at the end of the file:
```sh
hugo-pages ALL=(ALL) NOPASSWD:ALL
```

2. **Setup** the account & `nginx` server
```sh
ansible-playbook -i hosts.ini playbook/setup/setup_hugo_account.yaml --ask-become-pass
```
```sh
ansible-playbook -i hosts.ini playbook/setup/nginx_configuration.yaml
```

3. **Clone** the Repositories
```sh
ansible-playbook -i hosts.ini playbook/clone/*
```

4. **Post-Build modification** for running them in `nginx` server
```sh
ansible-playbook -i hosts.ini playbook/hugo/*
```

5. **Setup `nginx`** configuration
```sh
ansible-playbook -i hosts.ini playbook/nginx-serve/deploy-nginx.yaml
```
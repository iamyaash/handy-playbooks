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

- Add ssh key into this machine
```sh
ssh-copy-id hugo-pages@192.168.x.x
```

2. **Setup** the account & `nginx` server
```sh
ansible-playbook playbooks/setup-account.yaml
```
```sh
ansible-playbook playbooks/configure-nginx.yaml
```

3. **Clone** the Repositories
```sh
ansible-playbook playbooks/clone-stashed.yaml
```

5. **Setup `nginx`** configuration
```sh
ansible-playbook -i hosts.ini playbook/nginx-serve/deploy-nginx.yaml
```
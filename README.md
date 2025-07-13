# Ansible Playbooks for Home Raspberry Devices

## 1. Hugo Page Setup; Local
```sh
ansible-playbook hugo/master-playbook.yaml
```
Executes each playbook in certain order and deploys the site in an instant! 🙌🏼

## 2. Docker Installation & Configuration; ARM Architecture
```sh
ansible-playbook docker/master-playbook.yaml
```


# Informations

- Variables under `/inventory/group_vars/all.yaml` are accessible all over the project. Therefore, try maintaining repetitive variables inside `all.yaml`.
- Added a vault under `/inventory/groups_vars/vault.yaml`, and I haven't stored any sensitive information yet. 
    - Change password of the `vault` by using `ansible-vault rekey`.
    - Edit the `env` inside `vault.yaml` by using `ansible-vault edit`
- `ansible.cfg` stores information about the location of `hosts.ini`, so there's no need to mention the location of `hosts.ini` everytime you execute the command.
- Separated the `build` & `clone` tasks and moved it inside `/tasks/` for easier maintenance.
    - Used loops to clone & build multiple repositories.

# ansible-provision
Installs Code Enigma's infrastructure management stack on a server.
<!--TOC-->
<!--ENDTOC-->

<!--ROLEVARS-->
## Default variables
```yaml
---

_ansible_provision:
username: "{% if is_local is defined and is_local %}ce-dev{% else %}provision{% endif %}"

ansible_provision:
username: "{{ _ansible_provision.username }}"
# Main repo.
own_repository: "https://github.com/codeenigma/ansible-provision.git"
own_repository_branch: "master"
# Destination.
local_dir: "/home/{{ _ansible_provision.username }}/ansible-provision"
# Private config repo.
config_repository: ""
config_repository_branch: "master"
# Extra config repo.
extra_repository: ""
extra_repository_branch: "master"
extra_repository_vars_file: "custom.yml"
extra_repository_allowed_vars: []
# List of additional groups to add the user to.
groups: ''
```

<!--ENDROLEVARS-->
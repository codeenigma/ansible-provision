# Init role

This is meant to ALWAYS be included as the first task of a play.

<!--TOC-->
<!--ENDTOC-->

<!--ROLEVARS-->
## Default variables
```yaml
---
_ce_provision:
  username: "{% if is_local is defined and is_local %}ce-dev{% else %}provision{% endif %}"

ce_provision:
  username: "{{ _ce_provision.username }}"
  own_repository: "https://github.com/codeenigma/ce-provision.git"
  own_repository_branch: "master"
  config_repository: ""
  config_repository_branch: "master"
  extra_repository: ""
  extra_repository_branch: "master"
  extra_repository_vars_file: "custom.yml"
  extra_repository_allowed_vars: []
  local_dir: "/home/{{ _ce_provision.username }}/ce-provision"

_init:
  # A list of var directories to include. We only support .yml extensions.
  # This is used to detect if the playbook must re-run or not.
  vars_dirs: []

```

<!--ENDROLEVARS-->
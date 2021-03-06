# AMI Debian Buster
Creates an image from Debian Buster base with Packer, provisioned with an Ansible Playbook.

## Dependencies
This requires boto and Packer on the "provisioning" server.

<!--TOC-->
<!--ENDTOC-->
<!--ROLEVARS-->
## Default variables
```yaml
---
ami_debian_buster:
  aws_profile: "{{ _aws_profile }}"
  region: us-east-2
  instance_type: t2.micro
  ami_name: "example"
  encrypt_boot: false
  playbook_file: "{{ playbook_dir }}/base-playbook.yml" # Path to a playbook used to provision the image.
  # Operation can be one of:
  # - create: delete existing image if any and re-create a new one.
  # - ensure: Only create an image if it doesn't already exists.
  # - delete: Delete image and snapshots.
  #@todo find better names.
  operation: ensure
  # Ansible groups to add the target to. Useful for picking up group_vars.
  groups: []
  # groups:
  #   - "all"
  #   - "example"
  # A string of additional arguments to pass as ansible --extra-vars.
  # It must me escaped already, and will be passed as-is.
  extra_vars: ""

```

<!--ENDROLEVARS-->

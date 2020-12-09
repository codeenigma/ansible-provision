# AWS EFS

Creates or update an EFS volume.

<!--TOC-->
<!--ENDTOC-->

<!--ROLEVARS-->

## Default variables

```yaml
aws_rds:
  aws_profile: "{{ _aws_profile }}"
  region: eu-west-3
  multi_az: true
  subnets:
    - subnet-aaaaaaaa
    - subnet-bbbbbbbb
  name: example
  tags: []
  db_instance_class: db.m5.large
  state: present
  description: example
  engine: mariadb
  # engine_version: '5.7.2' # Omit to use latest.
  allocated_storage: 100 # Initial size in GB. Minimum is 100.
  max_allocated_storage: 1000 # Max size in GB for autoscaling.
  master_username: hello # The name of the master user for the DB cluster. Must be 1-16 letters or numbers and begin with a letter.
  master_user_password: hellothere
  publicly_accessible: false # Wether to allocate an IP address
  security_groups: []
```

<!--ENDROLEVARS-->
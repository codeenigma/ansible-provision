# NGINX

Install and configure the nginx webserver.

<!--TOC-->
<!--ENDTOC-->

<!--ROLEVARS-->
## Default variables
```yaml
---
php:
  version:
    - 7.3
symfony_env: "{{ _env_type }}"
nginx:
  # Global default config for nginx.conf.
  user: www-data
  worker_processes: auto
  events:
    worker_connections: 768
  http:
    server_names_hash_bucket_size: 256
    access_log: /var/log/nginx-access.log
    error_log: /var/log/nginx-error.log
  # Group prefix. Useful for grouping by environments.
  log_group_prefix: ""
  # Main log stream for nginx (Cloudwatch).
  log_stream_name: example
  # We can only have one backend, due to the way we use "common" templates.
  # Moving this per domain means instead having templates per project type.
  php_fastcgi_backend: "127.0.0.1:90{{ php.version[-1] | replace('.','') }}"
  ratelimitingcrawlers: false
  client_max_body_size: "700M"
  fastcgi_read_timeout: 60
  overrides: [] # See the '_overrides' role.
  domains:
    - server_name: "{{ _domain_name }}"
      access_log: "/var/log/nginx/access.log"
      error_log: "/var/log/nginx/error.log"
      error_log_level: "notice"
      # Server specific log stream (Cloudwatch),
      log_stream_name: example
      webroot: "/var/www/html"
      project_type: "flat"
      ssl: # @see the 'ssl' role.
        domain: "{{ _domain_name }}"
        handling: selfsigned
      ratelimitingcrawlers: true
      is_default: true
      basic_auth:
        auth_enabled: false
        auth_user: "hello"
        auth_pass: "P3nguin!"
      servers:
        - port: 80
          ssl: false
          https_redirect: true
        - port: 443
          ssl: true
          https_redirect: false
      upstreams: []
      # upstreams:
      #   - name: 'backend_example'
      #     backends:
      #       - 142.42.64.2:8080
      #       - 142.42.64.3:8080

```

<!--ENDROLEVARS-->

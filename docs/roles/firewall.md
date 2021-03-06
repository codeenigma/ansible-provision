# UFW Firewall

<!--TOC-->
<!--ENDTOC-->


<!--ROLEVARS-->
## Default variables
```yaml
---
# rules:
#   - { [port: ""] [rule: allow] [proto: any] [from_ip: any] [to_ip: any] [comment: 'rule comment']}
#
# https://docs.ansible.com/ansible/latest/modules/ufw_module.html#parameters
#

firewall:
  # Define any custom rule.
  rules: []
  # - { to_ip: any, direction: out, port: '123', rule: 'allow', proto: udp, comment: 'Allow outgoing NTP' }
  # - { from_ip: any, direction: in, port: '53', rule: 'allow', comment: 'Allow DNS' }

  input_policy: DROP
  output_policy: ACCEPT
  forward_policy: ACCEPT
  application_policy: SKIP
  ipv6: "yes"
  ipt_modules: "nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns"
  # Defaults IPs to whitelist. Do not override directly in playbooks, but set them in group_vars from your "private" config.
  _outbound_defaults: []
  _inbound_defaults: []
  # _inbound_defaults:
  # - port: '22'
  #     proto: tcp
  #     comment: 'Allow SSH access'
  #     ips:
  #       - '8.8.8.8'
  #       - '1.1.1.1'
  #   - port: '443'
  #     proto: tcp
  #     comment: 'Allow HTTPS access'
  #     ips:
  #       - '8.8.8.8'
  #       - '1.1.1.1'
  # Additional IPs to whitelist for a given playbooks. Those will be merged into the defaults above.
  outbound: []
  inbound: []

```

<!--ENDROLEVARS-->

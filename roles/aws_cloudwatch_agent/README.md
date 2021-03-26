# AWS Cloudwatch agent

<!--TOC-->
<!--ENDTOC-->

<!--ROLEVARS-->
## Default variables
```yaml
---
aws_cloudwatch_agent:
  # A resource name used as prefix for the streams.
  name: "example"
  # You'd normally use IAM policies, but that allows
  # non-AWS servers to log in cloudwatch too.
  use_credentials: false
  credentials:
    aws_access_key_id: XXX
    aws_secret_access_key: XXX
    region: "eu-west-3"

```

<!--ENDROLEVARS-->
# jschol-aws-infra

A work in progress, a collection of Ansible configurations for standing up a "cattle" deployment server in AWS.

Here are our rough notes so far:

## Ansible stuff

We are using the AWS EC2 inventory plugin for Ansible, which comes standard with Ansible, however, you need to install Ansible via Pip to get a new enough version, and install some modules so that the plugin can work correctly.

Docs on inventory plugins:
https://docs.ansible.com/ansible/latest/plugins/inventory.html

To see what inventory plugins are installed:
`ansible-doc -t inventory -l`

To read up on the amazon.aws.aws_ec2 plugin:
`ansible-doc -t inventory amazon.aws.aws_ec2`

### Installing Ansible and related modules:

`pip install ansible boto boto3 botocore`

To confirm things are working, run this command from the pub-cattle-ops-aws-infra/ansible folder:

`ansible-inventory -i pub-cattle-ops-aws_ec2.yml --graph`

output will look something like this:

```
@all:
  |--@arch_x86_64:
  |  |--eb-pub-jschol-prd
  |  |--pub-cattle-ops
  |  |--pub-cattle2-ops
  |--@aws_ec2:
  |  |--eb-pub-jschol-prd
  |  |--pub-cattle-ops
  |  |--pub-cattle2-ops
  |--@instance_type_t3_medium:
  |  |--eb-pub-jschol-prd
  |--@instance_type_t3_small:
  |  |--pub-cattle-ops
  |  |--pub-cattle2-ops
  |--@ungrouped:
```

## License

[MIT](LICENSE)

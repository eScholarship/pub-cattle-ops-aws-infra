

# Notes

Here's how to get the public IP address of the pub-cattle2-ops server

`ansible-inventory -i pub-cattle-ops-aws_ec2.yml --list | jq '._meta.hostvars[] | select(.tags["Name"] == "pub-cattle2-ops") | .public_ip_address'`

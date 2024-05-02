# learn-bash-delete-security-group
how to remove security group that has a tag with key or value

## how to list a security group
```ruby
aws ec2 describe-security-groups --group-id sg-067b847a0807e3d50
```
## how to extract a security group within the inbound/outbound rules
```ruby
aws ec2 describe-security-groups --group-id sg-067b847a0807e3d50 | jq -r '.SecurityGroups[].IpPermissions[].UserIdGroupPairs[].GroupId'
```
## how to list security groups that has a tag with Key
```ruby
aws ec2 describe-security-groups --query 'SecurityGroups[?Tags[?Key!=`<some:name>`]].GroupId' --output text
```

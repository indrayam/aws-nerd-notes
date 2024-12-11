# aws ec2

## VPC

```bash
# Create a Default VPC
aws ec2 create-vpc --instance-tenancy "default" --cidr-block "10.0.0.0/24" --tag-specifications '{"ResourceType":"vpc","Tags":[{"Key":"Name","Value":"default-vpc"}]}' 
# OR
# Create just any VPC
aws ec2 create-vpc --cidr-block "10.0.0.0/24" --tag-specifications '{"ResourceType":"vpc","Tags":[{"Key":"Name","Value":"new-vpc"}]}' 

# Get VPC ID of the default VPC
aws ec2 describe-vpcs --filter "Name=isDefault, Values=true" --query "Vpcs[0].VpcId" --output text
# OR
aws ec2 describe-vpcs | jq -r '.Vpcs[] | if .IsDefault == true then .VpcId else empty end'

# Spit out a simpler version of the VPC block for all VPCs
aws ec2 describe-vpcs | jq '.Vpcs[] | { vpcid: .VpcId, name: (if .Tags[0].Key == "Name" then 
.Tags[0].Value end), cidr: .CidrBlock }'

```

## Subnets

```bash
# Get how many subnets are there 
aws ec2 describe-subnets | jq '.Subnets | length'

# Get the keys of the Subnet object
aws ec2 describe-subnets | jq '.Subnets[0] | keys'

# Get just the Subnet ID, VPC ID, Availability Zone, and Cidr Block
aws ec2 describe-subnets | jq '.Subnets[] | { subnet_id: .SubnetId, vpc_id: .VpcId, az: .AvailabilityZone, cidr: .CidrBlock } '

# Get the first subnet from the VPC using JMESPath and aws --query approach
aws ec2 describe-subnets --filters "Name=vpc-id, Values=vpc-0b05dd03f758cbe8a" --query "Subnets[0].SubnetId" --output text
# OR
aws ec2 describe-subnets | jq -r '.Subnets[0].SubnetId'
```

## Internet Gateway

```bash
# Attach an Internet Gateway to a VPC
aws ec2 attach-internet-gateway --vpc-id "vpc-072b28f442e621e76" --internet-gateway-id "igw-04c5d062a25ba314f" --region us-east-2
```

## Get AMI

```bash
# Notice the hardcoded ownerid. Used ChatGPT to get that info
# Canonical Ubuntu: 099720109477
# Amazon Linux: 137112412989
# RedHat: 309956199498
# Notice the hardcoded pattern for the month and ami name for Ubuntu

# Get AMI details of the images you have authored
aws ec2 describe-images --region us-east-2 --owners self | jq '.Images[] | {name: .Name, ami_id: .ImageId, arch: .Architecture, description: .Description}'

# Latest Ubuntu AMI. Use these to get Name patterns
aws ec2 describe-images --region us-east-2 --image-id ami-0ea3c35c5c3284d82

# Get latest Ubuntu AMI using Name pattern (pay attention to the month in the pattern)
aws ec2 describe-images --region us-east-2 --filters "Name=name,Values=*24.04-amd64-server-202411*" "Name=architecture,Values=x86_64" "Name=owner-id,Values=099720109477" "Name=virtualization-type,Values=hvm" | jq .

# OPTIONAL: Get all Ubuntu AMIs for x86_64. Swap it with "arm" if you need that
aws ec2 describe-images --region us-east-2 --filters "Name=architecture,Values=x86_64" "Name=owner-id,Values=099720109477" "Name=virtualization-type,Values=hvm" | jq .

# Latest Amazon Linux AMI. Use these to get Name patterns
aws ec2 describe-images --region us-east-2 --image-id ami-0c80e2b6ccb9ad6d1

# Get latest Amazon AMI using Name pattern (pay attention to the month in the pattern)
aws ec2 describe-images --region us-east-2 --filters "Name=name,Values=*al2023-ami-2023.*.202411*" "Name=architecture,Values=x86_64" "Name=owner-id,Values=137112412989" "Name=virtualization-type,Values=hvm" | jq .

# OPTIONAL: Get all Amazon AMIs for x86_64. Swap it with "arm" if you need that
aws ec2 describe-images --region us-east-2 --filters "Name=architecture,Values=x86_64" "Name=owner-id,Values=137112412989" "Name=virtualization-type,Values=hvm" | jq .
```

## Get Security groups

```bash
aws ec2 describe-security-groups | jq -r '.SecurityGroups[0].GroupId'
```

## Get Key-Pair

```bash
# Get all key pairs
aws ec2 describe-key-pairs | jq -r '.KeyPairs[] | { name: .KeyName, id: .KeyPairId}'

# Get a specific key-pair Id
aws ec2 describe-key-pairs --key-name "Anand Sharma (Cloudy)" | jq -r '.KeyPairs[0].KeyPairId
```

## Launch an Instance (or a few)

```bash
aws ec2 run-instances \
--count 1 \
--image-id ami-036841078a4b68e14 \
--instance-type t3.micro \
--key-name "Anand Sharma (Cloudy)" \
--subnet-id subnet-0d3961f8577f599c0 \
--security-group-ids sg-0303fbb3c5398af26 \
--iam-instance-profile '{"Name": "ec2-ssm-core"}' \
--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=play4},{Key=Environment,Value=playground}]'
```

## List running instance(s)

```bash
# Using --filters feature of aws cli
aws ec2 describe-instances --filters "Name=instance-state-name,Values=running" | jq '.Reservations[].Instances[] | {id: .InstanceId, state: .State.Name, public_ip: .PublicIpAddress, public_dns: .PublicDnsName}'
# OR using just jq
aws ec2 describe-instances | jq '.Reservations[].Instances[] | if .State.Name == "running" then { id: .InstanceId, state: .State.Name, public_ip: .PublicIpAddress, public_dns: .PublicDnsName, subnet_id: .SubnetId, private_ip: .PrivateIpAddress, name: (.Tags[] | if .Key == "Name" then .Value else empty end) } else empty end'
```

## Create tags after an instance is launched

```bash
aws ec2 create-tags --resources i-061f1d392e8aae76e --tags "Key=Name,Value=play" "Key=Environment,Valu
e=playground"
```



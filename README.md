@echo off
set AWS_PROFILE=aep-aries
set AWS_REGION=us-east-2

echo == 1. VPCs (id, address range, name) ==
aws ec2 describe-vpcs --query "Vpcs[].[VpcId,CidrBlock,Tags[?Key=='Name']|[0].Value]" --output table

echo == 2. Subnets (VPC, name, zone, range, free IPs) ==
aws ec2 describe-subnets --query "Subnets[].[VpcId,Tags[?Key=='Name']|[0].Value,AvailabilityZone,CidrBlock,AvailableIpAddressCount]" --output table

echo == 3. Route tables (VPC, subnets, routes: destination and target) ==
aws ec2 describe-route-tables --query "RouteTables[].{vpc:VpcId,subnets:Associations[].SubnetId,routes:Routes[].join(' -> ',[DestinationCidrBlock||'',GatewayId||TransitGatewayId||NatGatewayId||VpcPeeringConnectionId||''])}" --output json

echo == 4. Transit Gateway attachments (which VPCs are connected) ==
aws ec2 describe-transit-gateway-attachments --query "TransitGatewayAttachments[].[ResourceId,TransitGatewayId,State]" --output table

echo == 5. VPC peerings ==
aws ec2 describe-vpc-peering-connections --query "VpcPeeringConnections[].[VpcPeeringConnectionId,RequesterVpcInfo.VpcId,AccepterVpcInfo.VpcId,Status.Code]" --output table

pause
----------------------------------------

C:\terraform>aws ec2 describe-vpcs --profile aep-aries --region us-east-2 --output table
-----------------------------------------------------------
|                      DescribeVpcs                       |
+---------------------------------------------------------+
||                         Vpcs                          ||
|+-----------------------+-------------------------------+|
||  CidrBlock            |  10.203.1.0/24                ||
||  DhcpOptionsId        |  dopt-87e31fec                ||
||  InstanceTenancy      |  default                      ||
||  IsDefault            |  False                        ||
||  OwnerId              |  387340471575                 ||
||  State                |  available                    ||
||  VpcId                |  vpc-0c32526d57d8e75a1        ||
|+-----------------------+-------------------------------+|
|||               CidrBlockAssociationSet               |||
||+----------------+------------------------------------+||
|||  AssociationId |  vpc-cidr-assoc-04e53fc2d33237bdd  |||
|||  CidrBlock     |  10.203.1.0/24                     |||
||+----------------+------------------------------------+||
||||                  CidrBlockState                   ||||
|||+-------------------+-------------------------------+|||
||||  State            |  associated                   ||||
|||+-------------------+-------------------------------+|||
|||                        Tags                         |||
||+----------------------+------------------------------+||
|||          Key         |            Value             |||
||+----------------------+------------------------------+||
|||  BusinessUnit        |  IT                          |||
|||  DeptID              |  13660                       |||
|||  ProductName         |  Infrastructure              |||
|||  Name                |  Rosa-Mas-Sb_VPC             |||
|||  Owner               |  cloud-engineering@aep.com   |||
|||  Dataclassification  |  Internal                    |||
|||  Team                |  Cloud Engineering           |||
||+----------------------+------------------------------+||
||                         Vpcs                          ||
|+-----------------------+-------------------------------+|
||  CidrBlock            |  10.203.0.0/24                ||
||  DhcpOptionsId        |  dopt-87e31fec                ||
||  InstanceTenancy      |  default                      ||
||  IsDefault            |  False                        ||
||  OwnerId              |  387340471575                 ||
||  State                |  available                    ||
||  VpcId                |  vpc-0bee26f8fe1b724b8        ||
|+-----------------------+-------------------------------+|
|||               CidrBlockAssociationSet               |||
||+----------------+------------------------------------+||
|||  AssociationId |  vpc-cidr-assoc-03e03368d1c5f85ac  |||
|||  CidrBlock     |  10.203.0.0/24                     |||
||+----------------+------------------------------------+||
||||                  CidrBlockState                   ||||
|||+-------------------+-------------------------------+|||
||||  State            |  associated                   ||||
|||+-------------------+-------------------------------+|||
|||                        Tags                         |||
||+----------------------+------------------------------+||
|||          Key         |            Value             |||
||+----------------------+------------------------------+||
|||  BusinessUnit        |  IT                          |||
|||  ProductName         |  Infrastructure              |||
|||  Name                |  Esri-Sb_VPC                 |||
|||  Owner               |  cloud-engineering@aep.com   |||
|||  Dataclassification  |  Internal                    |||
|||  DeptID              |  13660                       |||
|||  Team                |  Cloud Engineering           |||
||+----------------------+------------------------------+||
||                         Vpcs                          ||
|+-----------------------+-------------------------------+|
||  CidrBlock            |  10.203.3.0/24                ||
||  DhcpOptionsId        |  dopt-87e31fec                ||
||  InstanceTenancy      |  default                      ||
||  IsDefault            |  False                        ||
||  OwnerId              |  387340471575                 ||
||  State                |  available                    ||
||  VpcId                |  vpc-0a5c1a4507b784997        ||
|+-----------------------+-------------------------------+|
|||               CidrBlockAssociationSet               |||
||+----------------+------------------------------------+||
|||  AssociationId |  vpc-cidr-assoc-024d8f9ba777543b8  |||
|||  CidrBlock     |  10.203.3.0/24                     |||
||+----------------+------------------------------------+||
||||                  CidrBlockState                   ||||
|||+-------------------+-------------------------------+|||
||||  State            |  associated                   ||||
|||+-------------------+-------------------------------+|||
|||               CidrBlockAssociationSet               |||
||+----------------+------------------------------------+||
|||  AssociationId |  vpc-cidr-assoc-0a427574c4c0a7460  |||
|||  CidrBlock     |  100.64.0.0/16                     |||
||+----------------+------------------------------------+||
||||                  CidrBlockState                   ||||
|||+-------------------+-------------------------------+|||
||||  State            |  associated                   ||||
|||+-------------------+-------------------------------+|||
|||                        Tags                         |||
||+----------------------+------------------------------+||
|||          Key         |            Value             |||
||+----------------------+------------------------------+||
|||  DeptID              |  13660                       |||
|||  Owner               |  cloud-engineering@aep.com   |||
|||  ProductName         |  Infrastructure              |||
|||  Team                |  Cloud Engineering           |||
|||  BusinessUnit        |  IT                          |||
|||  Name                |  Eks-Poc_VPC                 |||
|||  Dataclassification  |  Internal                    |||
||+----------------------+------------------------------+||


aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,AvailabilityZone,CidrBlock,AvailableIpAddressCount]" --output table

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

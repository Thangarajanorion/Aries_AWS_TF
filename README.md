aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "RouteTables[].{table:RouteTableId,subnets:Associations[].SubnetId,dest:Routes[].DestinationCidrBlock,tgw:Routes[].TransitGatewayId}" --output json


aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "VpcEndpoints[].[ServiceName,VpcEndpointType,RouteTableIds]" --output text

aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "RouteTables[].{table:RouteTableId,subnets:Associations[].SubnetId,dest:Routes[].DestinationCidrBlock,tgw:Routes[].TransitGatewayId}" --output json


aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,SubnetId]" --output table

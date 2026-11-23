C:\terraform>aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "VpcEndpoints[].[VpcEndpointId,RouteTableIds]" --output text
vpce-0aa45a822e8bebefb
rtb-05a9625b3aa1e9f92

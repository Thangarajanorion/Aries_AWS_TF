
C:\terraform>aws ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 Name=association.main,Values=true --query "RouteTables[].RouteTableId" --output text
rtb-0a6c50d12be3ba392


C:\terraform>

aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,SubnetId]" --output table

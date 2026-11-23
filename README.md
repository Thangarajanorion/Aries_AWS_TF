aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,AvailabilityZone,CidrBlock,AvailableIpAddressCount]" --output table
aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,AvailabilityZone,CidrBlock,AvailableIpAddressCount]" --output table
-----------------------------------------------------------------------
|                           DescribeSubnets                           |
+--------------------------+-------------+-------------------+--------+
|  tgw-only_Private_1      |  us-east-2a |  10.203.3.192/28  |  10    |
|  eks-poc-eks-us-east-2b  |  us-east-2b |  10.203.3.64/26   |  59    |
|  tgw-only_Private_3      |  us-east-2c |  10.203.3.224/28  |  10    |
|  eks-poc-pods-us-east-2c |  us-east-2c |  100.64.128.0/18  |  16379 |
|  eks-poc-pods-us-east-2b |  us-east-2b |  100.64.64.0/18   |  16379 |
|  eks-poc-pods-us-east-2a |  us-east-2a |  100.64.0.0/18    |  16379 |
|  eks-poc-eks-us-east-2a  |  us-east-2a |  10.203.3.0/26    |  58    |
|  tgw-only_Private_2      |  us-east-2b |  10.203.3.208/28  |  10    |
|  eks-poc-eks-us-east-2c  |  us-east-2c |  10.203.3.128/26  |  58    |
+--------------------------+-------------+-------------------+--------+


C:\terraform>


C:\terraform>aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0bee26f8fe1b724b8 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,SubnetId]" --output table
---------------------------------------------------
|                 DescribeSubnets                 |
+--------------------+----------------------------+
|  esri-sb_Private_3 |  subnet-00b91cc1c13e3e4f9  |
|  esri-sb_Private_2 |  subnet-07c2722ae346deedc  |
|  esri-sb_Private_1 |  subnet-0ead5c457a155d8c1  |
+--------------------+----------------------------+


C:\terraform>

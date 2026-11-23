aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,SubnetId]" --output table
---------------------------------------------------------
|                    DescribeSubnets                    |
+--------------------------+----------------------------+
|  tgw-only_Private_1      |  subnet-05c21e060e772ab7a  |
|  eks-poc-eks-us-east-2b  |  subnet-0aa71c6a26d6dd63c  |
|  tgw-only_Private_3      |  subnet-0f98697dec248c4c2  |
|  eks-poc-pods-us-east-2c |  subnet-0e8dea0dfe1d7a489  |
|  eks-poc-pods-us-east-2b |  subnet-02249c1467c6a5688  |
|  eks-poc-pods-us-east-2a |  subnet-06b969c28d9cd8341  |
|  eks-poc-eks-us-east-2a  |  subnet-0fb03cebcc2514d80  |
|  tgw-only_Private_2      |  subnet-06f0b31ebaf631df1  |
|  eks-poc-eks-us-east-2c  |  subnet-02eefe783fd4e7004  |
+--------------------------+----------------------------+


C:\terraform>
C:\terraform>
C:\terraform>
C:\terraform>
C:\terraform>
C:\terraform>aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "VpcEndpoints[].[ServiceName,PrivateDnsEnabled,State]" --output table cmd aws ec2 describe-vpc-endpoint-services --profile aep-aries --region us-east-2 --query "ServiceNames[?contains(@,'bedrock')]" --output table

Error parsing parameter '--filters': Expected: '=', received: 'EOF' for input:
cmd
   ^

C:\terraform> aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "VpcEndpoints[].[ServiceName,PrivateDnsEnabled,State]" --output table
------------------------------------------------------
|                DescribeVpcEndpoints                |
+-----------------------------+--------+-------------+
|  com.amazonaws.us-east-2.s3 |  False |  available  |
+-----------------------------+--------+-------------+


C:\terraform>aws ec2 describe-vpc-endpoint-services --profile aep-aries --region us-east-2 --query "ServiceNames[?contains(@,'bedrock')]" --output table
------------------------------------------------------------------
|                   DescribeVpcEndpointServices                  |
+----------------------------------------------------------------+
|  com.amazonaws.us-east-2.bedrock                               |
|  com.amazonaws.us-east-2.bedrock-agent                         |
|  com.amazonaws.us-east-2.bedrock-agent-runtime                 |
|  com.amazonaws.us-east-2.bedrock-agentcore                     |
|  com.amazonaws.us-east-2.bedrock-agentcore-control             |
|  com.amazonaws.us-east-2.bedrock-agentcore.gateway             |
|  com.amazonaws.us-east-2.bedrock-data-automation               |
|  com.amazonaws.us-east-2.bedrock-data-automation-fips          |
|  com.amazonaws.us-east-2.bedrock-data-automation-runtime       |
|  com.amazonaws.us-east-2.bedrock-data-automation-runtime-fips  |
|  com.amazonaws.us-east-2.bedrock-fips                          |
|  com.amazonaws.us-east-2.bedrock-mantle                        |
|  com.amazonaws.us-east-2.bedrock-runtime                       |
|  com.amazonaws.us-east-2.bedrock-runtime-fips                  |
+----------------------------------------------------------------+


C:\terraform>aws rds describe-orderable-db-instance-options --profile aep-aries --region us-east-2 --engine aurora-postgresql --engine-version 15.13 --db-instance-class db.t3.medium --query "OrderableDBInstanceOptions[0].DBInstanceClass" --output text
db.t3.medium


C:\terraform>aws bedrock list-inference-profiles --profile aep-aries --region us-east-2 --query "inferenceProfileSummaries[?contains(inferenceProfileId,'sonnet')].inferenceProfileId" --output table

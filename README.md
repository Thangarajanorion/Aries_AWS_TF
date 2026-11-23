. Run four read-only checks in Citrix (type each on one line):

cmd
aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "VpcEndpoints[].[ServiceName,PrivateDnsEnabled,State]" --output table
cmd
aws ec2 describe-vpc-endpoint-services --profile aep-aries --region us-east-2 --query "ServiceNames[?contains(@,'bedrock')]" --output table
cmd
aws rds describe-orderable-db-instance-options --profile aep-aries --region us-east-2 --engine aurora-postgresql --engine-version 15.13 --db-instance-class db.t3.medium --query "OrderableDBInstanceOptions[0].DBInstanceClass" --output text
cmd
aws bedrock list-inference-profiles --profile aep-aries --region us-east-2 --query "inferenceProfileSummaries[?contains(inferenceProfileId,'sonnet')].inferenceProfileId" --output table

They

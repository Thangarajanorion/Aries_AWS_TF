aws ec2 describe-vpc-endpoints --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "VpcEndpoints[].[VpcEndpointId,RouteTableIds]" --output text



aws bedrock list-inference-profiles --profile aep-aries --region us-east-2 --query "inferenceProfileSummaries[].inferenceProfileId" --output table

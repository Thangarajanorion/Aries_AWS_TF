
To perform exactly these actions, run the following command to apply:
    terraform apply "aep.tfplan"

C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>terraform show -no-color aep.tfplan | findstr /c:"aws_vpc_endpoint." /c:"aws_opensearchserverless_vpc_endpoint"
  # module.opensearch.aws_opensearchserverless_vpc_endpoint.this will be created
  + resource "aws_opensearchserverless_vpc_endpoint" "this" {
  # module.vpc_endpoints.aws_vpc_endpoint.interface["bedrock-agent-runtime"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["bedrock-agentcore.gateway"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["bedrock-runtime"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["ecr.api"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["ecr.dkr"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["kms"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["logs"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["secretsmanager"] will be created
  # module.vpc_endpoints.aws_vpc_endpoint.interface["sts"] will be created

C:\terraform\aries-terraform

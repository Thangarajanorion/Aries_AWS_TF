terraform show -no-color aep.tfplan | findstr /c:"aws_vpc_endpoint." /c:"aws_opensearchserverless_vpc_endpoint"

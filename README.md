terraform init -backend-config=backend-aep.hcl
terraform plan -var-file=aep.tfvars -out=aep.tfplan

C:\terraform\terraform.exe plan -var-file=aep.tfvars -out=aep.tfplan

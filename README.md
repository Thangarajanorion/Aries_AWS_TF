aws s3api put-public-access-block --bucket aep-demo-aries-tfstate-387340471575 --public-access-block-configuration BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true --profile aep-aries

terraform plan -var-file=aep.tfvars -out=aep.tfplan

terraform init -backend-config=backend-aep.hcl -reconfigure

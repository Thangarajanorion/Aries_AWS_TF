type each on one line):

cmd
aws s3api create-bucket --bucket aep-demo-aries-tfstate-387340471575 --region us-east-2 --create-bucket-configuration LocationConstraint=us-east-2 --profile aep-aries
cmd
aws s3api put-bucket-versioning --bucket aep-demo-aries-tfstate-387340471575 --versioning-configuration Status=Enabled --profile aep-aries
cmd
aws s3api put-public-access-block --bucket aep-demo-aries-tfstate-387340471575 --public-access-block-configuration BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true --profile aep-aries
2. Put the bucket name into backend-aep.hcl
cmd
notepad backend-aep.hcl

Change the first line to:

hcl
bucket       = "aep-demo-aries-tfstate-387340471575"

Leave the other lines (key, region = "us-east-2", profile, encrypt, use_lockfile) as they are. Save and close Notepad.

3. Initialise again
cmd
terraform init -backend-config=backend-aep.hcl -reconfigure

It should end with "Terraform has been successfully initialized!" Then run the plan:

cmd
terraform plan -var-file=aep.tfvars -out=aep.tfplan

If creating

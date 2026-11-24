C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>aws s3api create-bucket --bucket aep-demo-aries-tfstate-387340471575 --region us-east-2 --create-bucket-configuration LocationConstraint=us-east-2 --profile aep-aries
{
    "Location": "http://aep-demo-aries-tfstate-387340471575.s3.amazonaws.com/"
}


C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>aws s3api put-bucket-versioning --bucket aep-demo-aries-tfstate-387340471575 --versioning-configuration Status=Enabled --profile aep-aries


C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>

C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>aws s3api put-public-access-block --bucket aep-demo-aries-tfstate-387340471575 --public-access-block-configuration

usage: aws [options] <command> <subcommand> [<subcommand> ...] [parameters]
To see help text, you can run:

  aws help
  aws <command> help
  aws <command> <subcommand> help

aws: error: argument --public-access-block-configuration: expected one argument


C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev> notepad backend-aep.hcl

C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>terraform init -backend-config=backend-aep.hcl    

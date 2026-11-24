>terraform init -backend-config=backend-aep.hcl -reconfigure
Initializing the backend...

Successfully configured the backend "s3"! Terraform will automatically
use this backend unless the backend configuration changes.

Initializing modules...

Initializing provider plugins...
- Finding opensearch-project/opensearch versions matching ">= 2.2.0"...
- Finding hashicorp/archive versions matching "~> 2.4"...
- Finding latest version of hashicorp/random...
- Finding hashicorp/aws versions matching "~> 6.0"...
- Installing opensearch-project/opensearch v2.6.0...
- Installed opensearch-project/opensearch v2.6.0 (self-signed, key ID BA81D99981191457)
- Installing hashicorp/archive v2.8.1...
- Installed hashicorp/archive v2.8.1 (signed by HashiCorp)
- Installing hashicorp/random v3.9.1...
- Installed hashicorp/random v3.9.1 (signed by HashiCorp)
- Installing hashicorp/aws v6.74.0...
- Installed hashicorp/aws v6.74.0 (signed by HashiCorp)
Partner and community providers are signed by their developers.
If you'd like to know more about provider signing, you can read about it here:
https://developer.hashicorp.com/terraform/cli/plugins/signing

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.

C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>

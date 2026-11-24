1. Check the load balancer's outputs

The record needs the load balancer's DNS name and zone ID:

cmd
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\modules\alb
findstr /n "output resource" outputs.tf main.tf
Note the name of the resource "aws_lb" "…" line (for example "this" or "main")
Check whether an output like alb_zone_id exists. If it doesn't, add this at the end of modules\alb\outputs.tf (replace this with the real name):
hcl
output "alb_zone_id" {
  value = aws_lb.this.zone_id
}
2. Add two variables

At the end of environments\dev\variables.tf:

hcl
variable "route53_zone_id" {
  description = "Existing public hosted zone cloud.aep.com"
  type        = string
}

variable "app_hostname" {
  description = "ARIES hostname, e.g. aries.cloud.aep.com"
  type        = string
}
3. Add the record

At the end of environments\dev\main.tf:

hcl
########################################
# DNS – aries.cloud.aep.com -> internal ALB
########################################
data "aws_route53_zone" "app" {
  zone_id = var.route53_zone_id
}

resource "aws_route53_record" "app" {
  zone_id = data.aws_route53_zone.app.zone_id
  name    = var.app_hostname
  type    = "A"

  alias {
    name                   = module.alb.alb_dns_name
    zone_id                = module.alb.alb_zone_id
    evaluate_target_health = true
  }
}
4. Add the values to aep.tfvars
hcl
route53_zone_id = "Z07331021PJL72XPRQ45K" # cloud.aep.com (public)
app_hostname    = "aries.cloud.aep.com"
app_url         = "https://aries.cloud.aep.com"

(app_url already exists in the file: change that line, don't add a second one.)

5. Check and plan
cmd
cd C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev
terraform fmt -recursive ..\..
terraform validate
terraform plan -var-file=aep.tfvars -out=aep.tfplan

Expected: Success! The configuration is valid, and the plan now includes aws_route53_record.app

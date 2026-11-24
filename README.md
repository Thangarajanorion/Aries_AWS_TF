# module.vpc_endpoints.aws_vpc_security_group_ingress_rule.https["ecs_frontend"] will be created
  + resource "aws_vpc_security_group_ingress_rule" "https" {
      + arn                          = (known after apply)
      + description                  = "HTTPS from ecs_frontend"
      + from_port                    = 443
      + id                           = (known after apply)
      + ip_protocol                  = "tcp"
      + referenced_security_group_id = (known after apply)
      + region                       = "us-east-2"
      + security_group_id            = (known after apply)
      + security_group_rule_id       = (known after apply)
      + tags_all                     = {
          + "BusinessUnit"       = "TBD"
          + "Dataclassification" = "TBD"
          + "Deployment"         = "aep_demo_ecs"
          + "DeptID"             = "TBD"
          + "Owner"              = "TBD"
          + "ProductName"        = "TBD"
          + "Team"               = "TBD"
        }
      + to_port                      = 443
    }

Plan: 113 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + agentcore_gateway_id          = (known after apply)
  + agentcore_gateway_role_arn    = (known after apply)
  + agentcore_gateway_url         = (known after apply)
  + alb_dns_name                  = (known after apply)
  + aoss_vpc_endpoint_id          = (known after apply)
  + aurora_master_user_secret_arn = (known after apply)
  + aurora_reader_endpoint        = (known after apply)
  + aurora_writer_endpoint        = (known after apply)
  + bedrock_agent_alias_id        = (known after apply)
  + bedrock_agent_id              = (known after apply)
  + bedrock_kb_id                 = ""
  + create_index_command          = (known after apply)
  + incident_retention_summary    = "Incidents retention is DISABLED"
  + opensearch_endpoint           = (known after apply)
  + opensearch_retention_status   = "OpenSearch retention: index='aries-incidents-idx' field='ticket_creation_date.keyword' older_than=90d | dry_run=TRUE (nothing will be deleted) | schedule=DISABLED"
  + retention_lambda_name         = "aep-demo-aries-aoss-retention"
  + retention_log_group           = "/aws/lambda/aep-demo-aries-aoss-retention"
  + retention_manual_invoke       = "aws lambda invoke --function-name aep-demo-aries-aoss-retention --region us-east-2 /tmp/out.json && cat /tmp/out.json"
  + vpc_endpoint_ids              = {
      + bedrock-agent-runtime       = (known after apply)
      + "bedrock-agentcore.gateway" = (known after apply)
      + bedrock-runtime             = (known after apply)
      + "ecr.api"                   = (known after apply)
      + "ecr.dkr"                   = (known after apply)
      + kms                         = (known after apply)
      + logs                        = (known after apply)
      + secretsmanager              = (known after apply)
      + sts                         = (known after apply)
    }
  + vpc_id                        = "vpc-0bee26f8fe1b724b8"

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Saved the plan to: aep.tfplan

To perform exactly these actions, run the following command to apply:
    terraform apply "aep.tfplan"

C:\terraform\aries-terraform-aep\aries-terrafor

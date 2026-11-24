terraform init -backend-config=backend-aep.hcl
Initializing the backend...

Initializing modules...
- ecr in ..\..\modules\ecr
- iam in ..\..\modules\iam
- osi_scheduler in ..\..\modules\osi_scheduler
- secrets in ..\..\modules\secrets
- gateway_tools in ..\..\modules\gateway_tools
- bedrock in ..\..\modules\bedrock
- security_groups in ..\..\modules\security_groups
- s3 in ..\..\modules\s3
- identity in ..\..\modules\identity
- alb in ..\..\modules\alb
- opensearch in ..\..\modules\opensearch
- agentcore_gateway in ..\..\modules\agentcore_gateway
- aurora in ..\..\modules\aurora
- ecs in ..\..\modules\ecs
- retention in ..\..\modules\retention
- vpc_endpoints in ..\..\modules\vpc_endpoints

╷
│ Error: Failed to get existing workspaces: Unable to list objects in S3 bucket "<STATE_BUCKET>" with prefix "env:/": operation error S3: ListObjectsV2, https response error StatusCode: 400, RequestID: Z3901GXGSH3ACVN7, HostID: iNiHm+W9nSrTBAyKL/jBlgg+2lizSu7b2OlVLScs/4zlN29vbKtO89YzRy52OkM6DBdiPLGALOrdXPw6RqD/IZ1Np/4+Rslp, api error InvalidBucketName: The specified bucket is not valid.
│
│
╵

C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>

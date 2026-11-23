 ec2 describe-route-tables --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "RouteTables[].{table:RouteTableId,subnets:Associations[].SubnetId,dest:Routes[].DestinationCidrBlock,tgw:Routes[].TransitGatewayId}" --output json
[
    {
        "table": "rtb-0906b32f6a682b0f1",
        "subnets": [],
        "dest": [
            "10.203.3.0/24",
            "100.64.0.0/16"
        ],
        "tgw": []
    },
    {
        "table": "rtb-0d91c5459d2fd3ce5",
        "subnets": [
            "subnet-02eefe783fd4e7004",
            "subnet-0fb03cebcc2514d80",
            "subnet-0aa71c6a26d6dd63c"
        ],
        "dest": [
            "10.203.3.0/24",
            "100.64.0.0/16",
            "0.0.0.0/0"
        ],
        "tgw": [
            "tgw-02ac34f9cf5cc3667"
        ]
    },
    {
        "table": "rtb-05a9625b3aa1e9f92",
        "subnets": [],
        "dest": [
            "10.203.3.0/24",
            "100.64.0.0/16",
            "10.0.0.0/8",
            "0.0.0.0/0"
        ],
        "tgw": [
            "tgw-02ac34f9cf5cc3667",
            "tgw-02ac34f9cf5cc3667"
        ]
    }
]


C:\terraform> aws ec2 describe-subnets --profile aep-aries --region us-east-2 --filters Name=vpc-id,Values=vpc-0a5c1a4507b784997 --query "Subnets[].[Tags[?Key=='Name']|[0].Value,SubnetId]" --output table
---------------------------------------------------------
|                    DescribeSubnets                    |
+--------------------------+----------------------------+
|  tgw-only_Private_1      |  subnet-05c21e060e772ab7a  |
|  eks-poc-eks-us-east-2b  |  subnet-0aa71c6a26d6dd63c  |
|  tgw-only_Private_3      |  subnet-0f98697dec248c4c2  |
|  eks-poc-pods-us-east-2c |  subnet-0e8dea0dfe1d7a489  |
|  eks-poc-pods-us-east-2b |  subnet-02249c1467c6a5688  |
|  eks-poc-pods-us-east-2a |  subnet-06b969c28d9cd8341  |
|  eks-poc-eks-us-east-2a  |  subnet-0fb03cebcc2514d80  |
|  tgw-only_Private_2      |  subnet-06f0b31ebaf631df1  |
|  eks-poc-eks-us-east-2c  |  subnet-02eefe783fd4e7004  |
+--------------------------+----------------------------+


C:\terraform>

# Plausible Explanation

There are a few steps to creating a VPN.

On the AWS_VPC side, the VGW is a redundant structure, which connects to the customer's infrastructure instead of having to go through an IGW. This VGW is provided the Customer's router's EIP (defined by an EIP in the on-prem_VPC).

To emulate the customer side better, we have an IGW on the customer side. The router (pfsense box) is provided both a private and public ENI - by extension, an EIP for each (the latter is used for the VPN connection), along with Route Tables and SGs defined so that traffic flows through it.

To understand the connection between the VGW and CGW, read this: https://docs.aws.amazon.com/vpn/latest/s2svpn/how_it_works.html

The IGW is basically "like a switch that determines if the VPC will have any public IPs". Thus, the deployment on the customer's side needs to have an IGW to route *any* traffic outside.

Understand VPC networking: https://www.reddit.com/r/aws/comments/10oysxj/basics_of_aws_vpc_understanding_subnets_route/

---

Helpful link: https://medium.com/petabytz/ipsec-vpn-configuration-on-aws-cloud-using-cloudformation-92078c3aa4c9

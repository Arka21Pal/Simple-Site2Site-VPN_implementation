There are a few steps to creating a VPN.

On the AWS_VPC side, the VGW is a redundant structure, which connects to the customer's infrastructure instead of having to go through an IGW. This VGW is provided the Customer's router's EIP (defined by an EIP in the on-prem_VPC).

To emulate the customer side better, we have an IGW on the customer side. The router (pfsense box) is provided both a private and public ENI - by extension, an EIP for each (the latter is used for the VPN connection), along with Route Tables and SGs defined so that traffic flows through it.

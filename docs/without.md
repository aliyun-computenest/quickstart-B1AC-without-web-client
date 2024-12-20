Deploying B1AC Infrastructure Package without SAP Business One (SAP B1)
=======================================================================

SAP Business One (SAP B1) is a cost-effective ERP solution designed to
streamline small business operations, covering areas such as accounting,
financials, purchasing, inventory, sales, customer relationships,
reporting, and analytics. The B1AC Infrastructure Package provides a
cloud environment that is ideal for installing and running the SAP
Business One (SAP B1) software. (Please note that the SAP Business One
(SAP B1) software is not included in this package and needs to be
installed after launching the service.)

Note: You can preview the price of all Alibaba Cloud resources involved
in the environment in step 2.4.

Note: To authorize your SAP B1 service partner (your partner) to conduct
the deployment, utilize the RAM function to grant them necessary access
to your resources (step 1.1 and step 1.2).

Once authorized, your partner can begin their work from Step 2.

###  RAM Authorization

1.  ####  Authorize user to deploy from Compute Nest

    a.  Open the RAM service in console
        ![](media/image1.png){width="6.460416666666666in"
        height="6.197916666666667in"}

    b.  Create Users![](media/image2.png){width="6.71875in"
        height="3.1173611111111112in"}

    c.  Configure Users

> ![](media/image3.png){width="6.575in" height="3.7916666666666665in"}

d.  Create policy

![](media/image4.png){width="7.791666666666667in"
height="4.903472222222222in"}

e.  Click JSON

![](media/image5.png){width="6.916666666666667in"
height="3.8916666666666666in"}

f.  Copy the following JSON file

{

\"Statement\": \[

{

\"Action\": \[

\"ecs:AddTags\",

\"ecs:AllocatePublicIpAddress\",

\"ecs:AttachKeyPair\",

\"ecs:AuthorizeSecurityGroup\",

\"ecs:AuthorizeSecurityGroupEgress\",

\"ecs:ConfigureSecurityGroupPermissions\",

\"ecs:CreateSecurityGroup\",

\"ecs:DeleteInstance\",

\"ecs:DeleteSecurityGroup\",

\"ecs:DescribeAvailableResource\",

\"ecs:DescribeDedicatedHosts\",

\"ecs:DescribeDisks\",

\"ecs:DescribeImageSupportInstanceTypes\",

\"ecs:DescribeImages\",

\"ecs:DescribeInstanceAutoRenewAttribute\",

\"ecs:DescribeInstanceRamRole\",

\"ecs:DescribeInstances\",

\"ecs:DescribeKeyPairs\",

\"ecs:DescribeNetworkInterfaces\",

\"ecs:DescribePrice\",

\"ecs:DescribeSecurityGroupAttribute\",

\"ecs:DescribeSecurityGroups\",

\"ecs:DescribeSnapshots\",

\"ecs:DescribeUserData\",

\"ecs:DetachKeyPair\",

\"ecs:JoinResourceGroup\",

\"ecs:ModifyDiskSpec\",

\"ecs:ModifyInstanceAttribute\",

\"ecs:ModifySecurityGroupEgressRule\",

\"ecs:ModifySecurityGroupRule\",

\"ecs:RemoveTags\",

\"ecs:ReplaceSystemDisk\",

\"ecs:ResizeDisk\",

\"ecs:RunInstances\",

\"ecs:StartInstance\",

\"ecs:StopInstance\",

\"ecs:TagResources\",

\"ecs:UntagResources\"

\],

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \[

\"oss:AbortMultipartUpload\",

\"oss:DeleteBucket\",

\"oss:DeleteBucketEncryption\",

\"oss:DeleteBucketTagging\",

\"oss:DeleteObject\",

\"oss:GetBucketAcl\",

\"oss:GetBucketCors\",

\"oss:GetBucketInfo\",

\"oss:GetBucketLifecycle\",

\"oss:GetBucketLogging\",

\"oss:GetBucketPolicy\",

\"oss:GetBucketReferer\",

\"oss:GetBucketTagging\",

\"oss:GetBucketVersioning\",

\"oss:GetBucketWebsite\",

\"oss:ListMultipartUploads\",

\"oss:ListObjects\",

\"oss:PutBucket\",

\"oss:PutBucketAcl\",

\"oss:PutBucketCors\",

\"oss:PutBucketEncryption\",

\"oss:PutBucketLifecycle\",

\"oss:PutBucketLogging\",

\"oss:PutBucketPolicy\",

\"oss:PutBucketReferer\",

\"oss:PutBucketTagging\",

\"oss:PutBucketVersioning\",

\"oss:PutBucketWebsite\"

\],

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \"quotas:ListProductQuotas\",

\"Effect\": \"Allow\",

\"Resource\": \"acs:quotas:\*:\*:\*\"

},

{

\"Action\": \"ram:GetRole\",

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \[

\"bss:\*\",

\"bssapi:\*\"

\],

\"Resource\": \"\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \[

\"vpc:\*NatGateway\*\",

\"vpc:\*Forward\*\",

\"vpc:\*Snat\*\",

\"vpc:\*FullNat\*\",

\"vpc:DescribeVpcs\",

\"vpc:DescribeVSwitches\",

\"vpc:CreateBandwidthPackage\",

\"vpc:DescribeBandwidthPackages\",

\"vpc:ModifyBandwidthPackageSpec\",

\"vpc:AddBandwidthPackageIps\",

\"vpc:RemoveBandwidthPackageIps\",

\"vpc:DeleteBandwidthPackage\",

\"vpc:ConvertBandwidthPackage\",

\"vpc:\*NatIp\*\"

\],

\"Resource\": \"\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \"vpc:DeletionProtection\",

\"Resource\": \"acs:vpc:\*:\*:natgateway/\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \"ram:CreateServiceLinkedRole\",

\"Resource\": \"\*\",

\"Effect\": \"Allow\",

\"Condition\": {

\"StringEquals\": {

\"ram:ServiceName\": \[

\"nat.aliyuncs.com\",

\"logdelivery.nat.aliyuncs.com\"

\]

}

}

},

{

\"Action\": \"ros:\*\",

\"Resource\": \"\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \[

\"vpc:\*HaVip\*\",

\"vpc:\*RouteTable\*\",

\"vpc:\*VRouter\*\",

\"vpc:\*RouteEntry\*\",

\"vpc:\*RouteEntries\*\",

\"vpc:\*VSwitch\*\",

\"vpc:\*Vpc\*\",

\"vpc:\*Cen\*\",

\"vpc:\*Tag\*\",

\"vpc:\*NetworkAcl\*\",

\"vpc:\*FlowLog\*\",

\"vpc:\*Ipv4Gateway\*\",

\"vpc:\*PrefixList\*\",

\"vpc:\*DhcpOptionsSet\*\",

\"vpc:DeletionProtection\",

\"vpc:\*TagResource\*\",

\"vpc:MoveResourceGroup\"

\],

\"Resource\": \"\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \"computenest:\*\",

\"Resource\": \"\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \[

\"oos:GetParametersByPath\",

\"oos:GetParameter\",

\"oos:UpdateParameter\"

\],

\"Resource\": \"acs:oos:\*:\*:parameter/computenest/\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \[

\"oos:GetSecretParametersByPath\",

\"oos:GetSecretParameter\",

\"oos:UpdateSecretParameter\"

\],

\"Resource\": \"acs:oos:\*:\*:secretparameter/computenest/\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \[

\"kms:GetSecretValue\",

\"kms:PutSecretValue\"

\],

\"Resource\": \"acs:kms:\*:\*:secret/oos/computenest/\*\",

\"Effect\": \"Allow\"

},

{

\"Action\": \"ram:CreateServiceLinkedRole\",

\"Resource\": \"\*\",

\"Effect\": \"Allow\",

\"Condition\": {

\"StringEquals\": {

\"ram:ServiceName\": \[

\"user.computenest.aliyuncs.com\"

\]

}

}

},

{

\"Action\": \[

\"ram:CreateRole\",

\"ram:GetRole\"

\],

\"Resource\":
\"acs:ram:\*:\*:role/AliyunCloudMonitorSendOperationMessageToComputeNestRole\",

\"Effect\": \"Allow\"

},

{

\"Action\": \"slb:DescribeLoadBalancerAttribute\",

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \[

\"tag:TagResources\",

\"tag:UntagResources\"

\],

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \[

\"vpc:AllocateEipAddress\",

\"vpc:AssociateEipAddress\",

\"vpc:CreateNatGateway\",

\"vpc:CreateSnatEntry\",

\"vpc:CreateVpnGateway\",

\"vpc:DeleteBandwidthPackage\",

\"vpc:DeleteNatGateway\",

\"vpc:DeleteSnatEntry\",

\"vpc:DeleteVpnGateway\",

\"vpc:DeletionProtection\",

\"vpc:DescribeBandwidthPackages\",

\"vpc:DescribeEipAddresses\",

\"vpc:DescribeNatGateways\",

\"vpc:DescribeSnatTableEntries\",

\"vpc:DescribeVSwitches\",

\"vpc:DescribeVpcs\",

\"vpc:DescribeVpnGateways\",

\"vpc:DescribeZones\",

\"vpc:GetNatGatewayAttribute\",

\"vpc:ListEnhancedNatGatewayAvailableZones\",

\"vpc:ListTagResources\",

\"vpc:ModifyEipAddressAttribute\",

\"vpc:ModifyNatGatewaySpec\",

\"vpc:ModifySnatEntry\",

\"vpc:ModifyVpnGatewayAttribute\",

\"vpc:ReleaseEipAddress\",

\"vpc:TagResources\",

\"vpc:UnTagResources\",

\"vpc:UnassociateEipAddress\"

\],

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \"yundun-sas:\*\",

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

},

{

\"Action\": \[

\"ros:CreateStack\",

\"ros:GetStack\",

\"ros:UpdateStack\",

\"ros:ListStackEvents\",

\"ros:ListStackResources\",

\"ros:ListStackResources\",

\"ros:DeleteStack\",

\"ram:GetRole\"

\],

\"Effect\": \"Allow\",

\"Resource\": \"\*\"

}

\],

\"Version\": \"1\"

}

g.  Click "ok"

![](media/image6.png){width="5.854166666666667in" height="5.6125in"}

h.  Enter Name for the policy

![](media/image7.png){width="6.229166666666667in" height="3.5in"}

i.  Authorize user to deploy from Compute Nest

![](media/image8.png){width="7.791666666666667in"
height="4.773611111111111in"}

![](media/image9.png){width="7.791666666666667in"
height="3.8784722222222223in"}

####  Access cloud resources to install services

![](media/image10.png){width="7.791666666666667in"
height="1.2229166666666667in"}

###  Configure Compute Nest

####  Click the User Deployment URL to deploy

![](media/image11.png){width="7.790692257217848in"
height="3.4787314085739283in"}

####  Configure the environment by selecting the deployment region.

![](media/image13.png){width="7.791666666666667in"
height="4.3909722222222225in"}

####  Set up the VPC, VSwitch, Availability Zone, Pay Period, and Network, then click Next.

![](media/image14.png){width="7.791666666666667in"
height="5.309722222222222in"}

####  Preview the price and click \"Create Now\" to proceed.

Note: You have the option to export a file, download a configuration
sheet, and view the pricing details of the resources.

![](media/image15.png){width="7.791666666666667in"
height="3.7715277777777776in"}

5.  ####  View Service 

6.  #### ![](media/image17.png){width="7.791666666666667in" height="2.6694444444444443in"}

7.  ####  Please be aware that you are required to commence payment for orders immediately upon deployment status being unpaid. If the order remains unpaid for more than 15 minutes, it will become invalid and you will need to redeploy it.

8.  #### ![](media/image18.png){width="8.271527777777777in" height="2.071527777777778in"}

9.  ####  The deployment has been completed successfully. You can now log in to ECS to proceed with the installation of SAP Business One (SAP B1)

10. #### ![](media/image19.png){width="7.791666666666667in" height="0.8958333333333334in"}

###  Install SAP Business One (SAP B1) \-- for Server

####  Upload the SAP installation package to the ECS

To connect, utilize the Windows built-in \"Remote Desktop Connection\"
client and input the public IP address of the ECS instance as well as
the administrator account information. Upon successful connection to the
ECS instance, you can use the clipboard function to directly copy files
from the local computer and paste them into the remote desktop.

####  Once the Remote Desktop Connection is established, you can right-click on the application you intend to run and select \"Run as Administrator\" to execute it with administrative privileges.

![](media/image20.png){width="5.541666666666667in" height="5.1875in"}

####  Select your preferred installation language and then click \"Next\" to proceed.

![](media/image21.png){width="6.489583333333333in"
height="4.447916666666667in"}

#### Choose your preferred Setup Type and then click \"Next\" to continue.

![](media/image22.png){width="6.489583333333333in" height="4.4375in"}

####  Choose \"New Configuration\" and click \"Next\" to proceed. 

![](media/image23.png){width="6.541666666666667in"
height="4.552083333333333in"}

####  Select \"Install Local SLD\" and then click on \"Next\" to continue with the installation process.

![](media/image24.png){width="6.5in" height="4.427083333333333in"}

####  After setting the SAP password, click \"Next\" to proceed with the installation process.

![](media/image25.png){width="6.458333333333333in"
height="4.447916666666667in"}

####  Please input the database sa account and password, then fill in the server name with the hostname. Click \"Next\" to continue. (In SQL Server, the user name \"sa\" is the default System Administrator (sa) username. This is due to historical reasons and convention, as well as to simplify the installation and setup process.)

![](media/image26.png){width="6.427083333333333in"
height="4.479166666666667in"}

####  Choose the components you want to install and click \"Next\" to proceed with the installation process.

![](media/image27.png){width="6.46875in" height="4.416666666666667in"}

####  Click \"OK\" in the pop-up box to proceed.

![](media/image28.png){width="6.354166666666667in"
height="4.447916666666667in"}

####  Click "Next" to proceed. 

![](media/image29.png){width="6.416666666666667in"
height="4.552083333333333in"}

![](media/image30.png){width="6.479166666666667in"
height="4.447916666666667in"}

####  Click \"OK\" in the pop-up box to proceed.

![](media/image31.png){width="6.395833333333333in" height="4.46875in"}

####  Click \"Setup\" to finish the installation. 

![](media/image32.png){width="6.333333333333333in" height="4.40625in"}

**Note**: Depending on your specific business requirements, it may be
necessary to add additional components before finalizing the application
build. Please refer to the SAP Business One (SAP B1) operational manual
for further instructions.

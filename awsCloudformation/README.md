# Regions and Availability zones
[TOC]
## 1. Regions
* When you launch an instance, you must select an **AMI that's in the same region**
![](../images/aws_regions.png)
**Specifying the Region for a Resource**
* Every time you create an Amazon EC2 resource, you can specify the region for the resource
* You can specify the region for a resource using the AWS Management Console or the command line.
> Note: Some AWS resources might not be available in all regions and Availability Zones
>
> Ensure that you can create the resources you need in the desired regions or Availability Zone before launching an instance in a specific Availability Zone.
* Amazon EC2 is hosted in multiple locations world-wide; 
* these locations are composed of regions and Availability Zones
* each *region* is a separate geographic area
* each region has **multiple, isolated locations known as *Availability Zones***
* The following table lists the regions provided by an AWS account. You can't describe or access additional regions from an AWS account, such as AWS GovCloud (US) or China (Beijing).
| Code             | Name                       |
| ---------------- | -------------------------- |
| `us-east-1`      | US East (N. Virginia)      |
| `us-east-2`      | US East (Ohio)             |
| `us-west-1`      | US West (N. California)    |
| `us-west-2`      | US West (Oregon)           |
| `ca-central-1`   | Canada (Central)           |
| `eu-central-1`   | EU (Frankfurt)             |
| `eu-west-1`      | EU (Ireland)               |
| `eu-west-2`      | EU (London)                |
| `eu-west-3`      | EU (Paris)                 |
| `ap-northeast-1` | Asia Pacific (Tokyo)       |
| `ap-northeast-2` | Asia Pacific (Seoul)       |
| `ap-northeast-3` | Asia Pacific (Osaka-Local) |
| `ap-southeast-1` | Asia Pacific (Singapore)   |
| `ap-southeast-2` | Asia Pacific (Sydney)      |
| `ap-south-1`     | Asia Pacific (Mumbai)      |
| `sa-east-1`      | South America (São Paulo)  |
**To find your regions and Availability Zones using the command line**
* each AWS  resource  is tied to a default region
* Every time you create an Amazon EC2 resource, you can specify the region for the resource 
* You can set the value of an environment variable to the desired regional endpoint (for example, `https://ec2.us-east-2.amazonaws.com`) using `AWS_DEFAULT_REGION` (AWS CLI)
* that is done when configuring the AWSCLI config file
* The AWS CLI config file, which defaults to `~/.aws/config` has the following format:
```shell
  [default]
  aws_access_key_id=foo
  aws_secret_access_key=bar
  region=eu-west-1
```
* The AWS CLI has a few general options:
  | Variable | Option    | Config Entry | Environment Variable | Description          |
  | -------- | --------- | ------------ | -------------------- | -------------------- |
  | profile  | --profile | N/A          | AWS_PROFILE          | Default profile name |
  | region   | --region  | region       | AWS_DEFAULT_REGION   | Default AWS Region   |
  | output   | --output  | output       | AWS_DEFAULT_OUTPUT   | Default output style |
* Alternatively, you can use the `--region` (AWS CLI) command line option with each individual command.  
* use the [describe-regions](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-regions.html) command as follows to describe the regions for your account.
```bash
$ aws ec2 describe-regions
```
* that outputs to
```bash
{                                                                         
    "Regions": [                                                                  {                                                               
            "Endpoint": "ec2.ap-south-1.amazonaws.com",                   
            "RegionName": "ap-south-1"                                           },                                                               
        {                                                                 
            "Endpoint": "ec2.eu-west-3.amazonaws.com",                   
            "RegionName": "eu-west-3"                                     
        },                                                               
        {                                                                 
            "Endpoint": "ec2.eu-west-2.amazonaws.com",                   
            "RegionName": "eu-west-2"                                     
        },                                                               
        {                                                                 
            "Endpoint": "ec2.eu-west-1.amazonaws.com",                  
            "RegionName": "eu-west-1"                                     
        },                                                               
        {                                                                 
            "Endpoint": "ec2.ap-northeast-2.amazonaws.com",               
            "RegionName": "ap-northeast-2"                               
        },                                                               
        {                                                                 
            "Endpoint": "ec2.ap-northeast-1.amazonaws.com",               
            "RegionName": "ap-northeast-1"                               
        },                                                               
        {                                                                 
            "Endpoint": "ec2.sa-east-1.amazonaws.com",
            "RegionName": "sa-east-1"
        },
        {
            "Endpoint": "ec2.ca-central-1.amazonaws.com",
            "RegionName": "ca-central-1"
        },
        {
            "Endpoint": "ec2.ap-southeast-1.amazonaws.com",
            "RegionName": "ap-southeast-1"
        },
        {
            "Endpoint": "ec2.ap-southeast-2.amazonaws.com",
            "RegionName": "ap-southeast-2"
        },
        {
            "Endpoint": "ec2.eu-central-1.amazonaws.com",
            "RegionName": "eu-central-1"
        },
        {
            "Endpoint": "ec2.us-east-1.amazonaws.com",
            "RegionName": "us-east-1"
        },
        {
            "Endpoint": "ec2.us-east-2.amazonaws.com",
            "RegionName": "us-east-2"
        },
        {
            "Endpoint": "ec2.us-west-1.amazonaws.com",
            "RegionName": "us-west-1"
        },
        {
            "Endpoint": "ec2.us-west-2.amazonaws.com",
            "RegionName": "us-west-2"
        }
    ]
}
```
1. Use the [describe-availability-zones](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-availability-zones.html) command as follows to describe the Availability Zones within the specified region.
```bash
$ aws ec2 describe-availability-zones --region eu-west-1
```
* outputs to
```json
{
    "AvailabilityZones": [
        {
            "State": "available",
            "Messages": [],
            "RegionName": "eu-west-1",
            "ZoneName": "eu-west-1a"
        },
        {
            "State": "available",
            "Messages": [],
            "RegionName": "eu-west-1",
            "ZoneName": "eu-west-1b"
        },
        {
            "State": "available",
            "Messages": [],
            "RegionName": "eu-west-1",
            "ZoneName": "eu-west-1c"
        }
    ]
}
```
##  2. Availability Zones
* Amazon operates state-of-the-art, highly available data center facilities
* However, failures can occur that affect the availability of EC2 instances that are in the same location
* So to overcome this **every Amazon Region** is further sub divided into Availability zones
* Amazon Availability Zones are **distinct physical locations** having Low latency network connectivity between them inside the same region and are engineered to be insulated from failures from other AZ’s
* Each availability zone runs on its own physically distinct, independent infrastructure, and is engineered to be highly reliable; 
* they have Independent power, cooling, network and security
* Common points of failures like generators and cooling equipment are not shared across Availability Zones
* Additionally, they are **physically separate**; 
* such that even extremely uncommon disasters such as fires, tornados or flooding would only affect a single Availability Zone
* The following diagram illustrates availability zone concept: *(image Source : AWS)*
  ![](../images/Amazon%20Availability%20zones%20Regions.png)
* Region :US-EAST( North Virginia) has **5** availability zones
* Region :US-West (California + Oregon) has **6** availability zones
* Region :Europe – West (Dublin) has **3** availability zones
* Region :Asia Pacific (Japan) has **2** availability zones
* Region :Asia Pacific (Singapore) has **2** availability zones
* Region :South America (Sao Paulo) has **2** availability zones
* When you launch an instance, you can **select an Availability Zone**
* if you distribute your instances across multiple Availability Zones and one instance fails, you can design your application so that an instance in another Availability Zone can handle requests.
* You can also use **Elastic IP addresses** to mask the failure of an instance in one Availability Zone by rapidly remapping the address to an instance in another Availability Zone
* An Availability Zone is represented by a region code followed by a **letter identifier**; for example, `us-east-1a`.
* to ensure that resources are distributed across the Availability Zones for a region, we independently map Availability Zones to identifiers for each account
* For example, your Availability Zone `us-east-1a` might not be the same location as `us-east-1a` for another account
* There's no way for you to coordinate Availability Zones between accounts
> NOTE: You can have **as many Subnets as you like in each AZ**
>
> By default AWS creates one VPC containing one Subnet in each AZ. The number of AZ varies from region to region
* Use the [describe-availability-zones](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-availability-zones.html) command as follows to describe the Availability Zones within the specified region.
```shell
$ aws ec2 describe-availability-zones --region eu-central-1
```
## 3. Endpoints
>  To reduce **data latency in your applications**, most Amazon Web Services products allow you to select a regional endpoint to make your requests
>
> An endpoint is a URL that is the entry point for a web service.
* When you work with an instance using the **command line interface** or API actions, you must specify its regional endpoint
* to reduce data latency in your applications, most Amazon Web Services offer a **regional endpoint** to make your requests
* an endpoint is a URL that is the entry point for a web service
* for example, `https://dynamodb.us-west-2.amazonaws.com` is an entry point for the Amazon DynamoDB service
* Some services, such as IAM, do not support regions; therefore, their endpoints do not include a region. 
* Some services, such as Amazon EC2, let you specify an endpoint that does not include a specific region, for example, `https://ec2.amazonaws.com`. In that case, AWS routes the endpoint to us-east-1
* If a service supports regions, the resources in each region are independent
* see the endpoints for several services for the region `eu-west-1`
| Service                                         | Endpoint                                                     | Protocol       |
| ----------------------------------------------- | ------------------------------------------------------------ | -------------- |
| Amazon Elastic Compute Cloud (Amazon EC2)       | ec2.eu-west-1.amazonaws.com                                  | HTTP and HTTPS |
| Amazon Elastic Container Registry               | ecr.eu-west-1.amazonaws.com                                  | HTTPS          |
| Amazon Elastic Container Service                | ecs.eu-west-1.amazonaws.com                                  | HTTPS          |
| Amazon Elastic File System                      | elasticfilesystem.eu-west-1.amazonaws.com                    | HTTPS          |
| Elastic Load Balancing                          | elasticloadbalancing.eu-west-1.amazonaws.com                 | HTTPS          |
| Amazon Elasticsearch Service                    | es.eu-west-1.amazonaws.com                                   | HTTPS          |
| AWS Identity and Access Management (IAM)        | iam.amazonaws.com                                            | HTTPS          |
| AWS Key Management Service                      | kms.eu-west-1.amazonaws.com                                  | HTTPS          |
| kms-fips.eu-west-1.amazonaws.comAWS Lambda      | lambda.eu-west-1.amazonaws.com                               | HTTPS          |
| Amazon Relational Database Service (Amazon RDS) | rds.eu-west-1.amazonaws.com                                  | HTTPS          |
| Amazon Simple Notification Service (Amazon SNS) | sns.eu-west-1.amazonaws.com                                  | HTTP and HTTPS |
| Amazon Simple Storage Service (Amazon S3)       | s3.eu-west-1.amazonaws.com<br />  s3-eu-west-1.amazonaws.com | HTTP and HTTPS |
## 4.  Launching Instances in an Availability Zone
* When you launch an instance, select a region 
* By launching your instances in **separate Availability Zones**, you can protect your applications from the failure of a single location
* if you do not specify an Availability Zone, we select one for you
* When you launch your initial instances, we recommend that you accept the **default Availability Zone**, because this enables us to select the best Availability Zone for you based on system health and available capacity
* if you launch additional instances, only specify an Availability Zone if your new instances must be close to, or separated from, your running instances.
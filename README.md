# QuickLoan -- Highly Available Loan Application Deployment on AWS

A cloud deployment project that hosts a loan application on AWS using a
highly available, scalable architecture. The project demonstrates AWS
networking, compute, storage, database, load balancing, auto scaling,
DNS, monitoring, and notifications.

## Project Overview

QuickLoan is a sample loan application where users can submit loan
details through a web form. Application data is stored in an Amazon RDS
MySQL database. The deployment uses an Application Load Balancer and an
Auto Scaling Group to support availability and scaling across
Availability Zones.

**Application URL used in the project:** http://loan.pranavtatar.in

> This URL is included as documented in the project material. Its
> current availability is not guaranteed.

## AWS Services Used

  -----------------------------------------------------------------------
  Area                                AWS services / components
  ----------------------------------- -----------------------------------
  Networking                          Amazon VPC, public and private
                                      subnets, route tables, Internet
                                      Gateway, NAT Gateway, security
                                      groups, Availability Zones

  Compute                             Amazon EC2, Amazon Machine Images
                                      (AMI), launch templates, Auto
                                      Scaling Group

  Storage                             Amazon S3

  Database                            Amazon RDS for MySQL

  High availability                   Application Load Balancer (ALB),
                                      target groups

  Monitoring and notifications        Amazon CloudWatch, Amazon SNS

  DNS                                 Amazon Route 53, with domain
                                      nameservers managed through GoDaddy
  -----------------------------------------------------------------------

## Architecture and Workflow

1.  Configure the VPC and networking components, including subnets,
    gateways, and route tables.
2.  Configure security groups to control traffic to the application and
    supporting resources.
3.  Launch EC2 instances and deploy the website files.
4.  Create an S3 bucket for project storage.
5.  Configure the domain in Route 53 and point the GoDaddy nameservers
    to Route 53.
6.  Create an Amazon RDS MySQL database and connect it to the
    application.
7.  Create an AMI from the configured application instance.
8.  Configure a launch template and an EC2 target group.
9.  Create an Application Load Balancer to distribute incoming
    application traffic.
10. Create an SNS topic and email subscription for notifications.
11. Create an Auto Scaling Group using the launch template.
12. Configure CloudWatch alarms and dynamic scaling policies.

## Application Testing

The project documentation demonstrates submitting a loan application and
checking that the submitted records are stored in the RDS MySQL
database.

Example SQL query used for verification:

``` sql
SELECT * FROM applications;
```

The example database output in the project document shows application
records with fields for ID, name, contact, email, and loan type.

## Monitoring and Auto Scaling

CloudWatch alarms are configured to monitor EC2 CPU utilization:

-   **CPU \> 80%** -- high CPU utilization alarm.
-   **CPU \< 20%** -- low CPU utilization alarm.

Dynamic scaling policies are configured to adjust the number of EC2
instances based on CPU utilization. Amazon SNS is configured with an
email subscription for notifications.

## Deployment Documentation

The accompanying project report contains console screenshots of the AWS
resource configuration and deployment process, including:

-   VPC, subnet, gateway, and route-table configuration
-   Security groups and EC2 instances
-   S3 bucket and Route 53 configuration
-   RDS MySQL database and application testing
-   AMI, launch template, target group, and load balancer
-   SNS topic and subscription
-   Auto Scaling Group, CloudWatch alarms, and scaling policies

## Repository Structure

A suggested GitHub repository layout:

``` text
QuickLoan-AWS/
├── README.md
├── screenshots/
│   └── (add project screenshots here)
└── docs/
    └── (add the project report here, if desired)
```

Add your application source files to the repository as appropriate. The
structure above is a suggested layout; it does not imply that source
files or screenshots are included yet.

## Prerequisites

-   An AWS account with permission to create the services listed above
-   A registered domain name (the documented project uses GoDaddy)
-   Application website files
-   Basic familiarity with AWS networking, EC2, RDS, load balancing, and
    Auto Scaling

## Security Notes

-   Do not upload AWS access keys, passwords, private keys, database
    credentials, or other secrets to GitHub.
-   Do not commit `.pem` files, environment files containing secrets, or
    database dumps with personal information.
-   Use IAM roles and appropriately scoped security groups rather than
    embedding credentials in application files.
-   Review AWS resources and remove anything no longer needed to avoid
    unexpected charges.

## Learning Outcomes

-   Building a VPC-based AWS network with public and private subnets
-   Deploying a web application on EC2
-   Connecting an application to an RDS MySQL database
-   Configuring an Application Load Balancer and target group
-   Creating an AMI and launch template
-   Configuring an Auto Scaling Group and dynamic scaling policies
-   Monitoring EC2 metrics with CloudWatch and sending notifications
    through SNS
-   Managing DNS using Route 53 and GoDaddy

## Author

**Pranav Tatar**

------------------------------------------------------------------------

*Project documentation is based on the AWS deployment report. Refer to
the report and actual repository configuration for
implementation-specific details.*

# A Cloud Guru -- LABS

# Overview

Found new infrastructure to build. This will allow me to get some hands on experience with different AWS services using Terraform. Following different guides I may find along the way will give me a better understanding using different AWS Services along with Terraform Infrastructure and Building Architecture in the cloud.

-----

# Getting Started

As new guides cross my path to assist in my knowledge and understanding of how the AWS Provider works and the best practices to build infrastructure using Terraform. I will update this repository as new tutorials become available for me to learn and use to gain more knowledge. The ***Guides*** portion of this README will be updated accordingly with links used to learn. This is done for future referencing and of course to give credit to the original owner.



## Objective
    1. Create VPC
        - Name tag: In the text field, enter vpc1.
        - IPv4 CIDR block: In the text field, enter 172.16.0.0/16.

    2. Create a Public and Private Subnet in Different Availability Zones
        -- Configure the public subnet:
            --- VPC ID: Use the dropdown to select vpc1.
            --- Subnet name: In the text field, enter Public1.
            --- Availability Zone: Use the dropdown to select us-east-1a.
            --- IPv4 CIDR block: In the field, select 172.16.1.0/24.
            --- Any EC2 instances assigned to this subnet will have an IP address prefix of 172.16.1.
        -- Configure the private subnet:
            --- VPC ID: Use the dropdown to select vpc1.
            --- Subnet name: In the text field, enter Private1.
            --- Availability Zone: Use the dropdown to select us-east-1b.
            --- IPv4 CIDR block: In the field, select 172.16.2.0/24.

    3. Create Two Network Access Control Lists (NACLs), and Associate Each With the Proper Subnet
        -- Create and Configure a Public NACL
            --- Name: In the text field, enter PublicNACL.
            --- VPC: Use the dropdown to select vpc1.
            --- Add an inbound rule
                -*- Rule number: In the text field, enter 100.
                -*- Type: Use the dropdown to select HTTP (80).
                -*- Source: Leave the source as 0.0.0.0/0.
                -*- Rule number: In the text field, enter 110.

                -*- Type: Use the dropdown to select SSH (22).
                -*- Source: Leave the source as 0.0.0.0/0.

            --- Add an outbound rule:
                -*- Rule number: In the text field, enter 100.
                -*- Type: Leave the type as Custom TCP.
                -*- Port range: In the text field, enter 1024-65535.
                -*- Destination: Leave the destination as 0.0.0.0/0.

    4. Create and Configure a Private NACL
        -- Name: In the text field, enter PrivateNACL.
        -- VPC: Use the dropdown to select vpc1.
        -- Add an inbound rule:
            --- Rule number: In the text field, enter 100.
            --- Type: Use the dropdown to select SSH (22).
            --- Source: In the text field, enter 172.16.1.0/24.
        --- Add an outbound rule:
            --- Rule number: In the text field, enter 100.
            --- Type: Leave the type as Custom TCP.
            --- Port range: In the text field, enter 1024-65535.
            --- Destination: Leave the destination as 0.0.0.0/0.

    5. Create Two Route Tables, and Associate Them with the Correct Subnet
        -- Configure the public route table:
            -- Name: In the text field, enter PublicRT.
            -- VPC: Use the dropdown to select vpc1.
        -- Configure the private route table:
            -- Name: In the text field, enter PrivateRT.
            -- VPC: Use the dropdown to select vpc1.

        ** Associate the Route Tables with the Correct Subnet **
        -- Public Route::
            -- Add a route to the internet gateway: 0.0.0.0/0.
        -- Private Route::
            -- private subnet




## Running Terraform

Run the following to ensure ***terraform*** will only perform the expected
actions:

```sh
terraform fmt
terraform init
terraform validate
terraform plan
terraform apply
```

## Tearing Down the Terraform Infrastructure

Run the following to verify that ***terraform*** will only impact the expected
nodes and then tear down the cluster.

```sh
terraform plan
terraform destroy
```
---
[tfhome](https://www.terraform.io)
[tfdocs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
[medium](https://medium.com/)
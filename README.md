# ec2-boto3-provision
Provision ec2 on-demand or spot instances with python boto3

## History
This script was created as I need to migrate a number of boxes from one AWS account
to another in a very short time frame. I would have used Ansible but we were limited
to pre 2.0 version that didn't support SSO Saml authentication (a requirement of the destination account)

There are a number of other approaches which could be a better solution.

* Terraform
* Cloudformation
* Ansible (needs v2.0+ for SAML)

See [Terraform vs Ansible vs Cloudformation](https://groups.google.com/forum/#!topic/terraform-tool/6Fxnl_bejX4)

This script reads a simple YAML file containing security group and instance definitions and provisions and tags them.

## Authentication
The script assumes you have authenticated with aws and have a local **.aws/credentials** file

## Running the script

    $ python2.7 ec2_provision.py --help
    usage: ec2_provision.py [-h] [--verbose] [--profile PROFILE] --definitions
                        DEFINITIONS [--add_security_groups] [--add_instances]

    EC2 Utilities to manage security groups and instances

        optional arguments:
          -h, --help            show this help message and exit
          --verbose, -v         Verbose Logging
          --profile PROFILE, -p PROFILE

                                EC2 Authentication profile (.aws/credentials)

          --definitions DEFINITIONS, -d DEFINITIONS

                                YAML defintion file with security groups and instances

          --add_security_groups
                                Add security groups
          --add_instances       Add instances

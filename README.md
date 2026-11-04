# AWS VPC Peering Project

## Project Overview
This project demonstrates secure private communication between two Amazon Virtual Private Clouds (VPCs) using VPC Peering.

The objective was to establish private network connectivity between EC2 instances deployed in separate VPCs without exposing the application instances to the public internet.

## AWS Services Used
- Amazon VPC
- VPC Peering Connection
- Amazon EC2
- Subnets
- Route Tables
- Internet Gateway
- Security Groups
- Amazon EBS

## Architecture

### VPC A
- VPC Name: ewb-vpc-a
- CIDR: 10.10.0.0/16
- Public Subnet: 10.10.1.0/24
- Private Subnet: 10.10.2.0/24
- EC2 Bastion Host: 10.10.1.10
- EC2 App-A: 10.10.2.10

### VPC B
- VPC Name: ewb-vpc-b
- CIDR: 10.20.0.0/16
- Private Subnet: 10.20.1.0/24
- EC2 App-B: 10.20.1.10

## VPC Peering
A VPC Peering connection was established between VPC A and VPC B.

- Peering Name: ewb-a-b-peer
- Connection ID: pcx-08836456fe57ee7dd
- Region: ap-southeast-2 (Sydney)

Routes were configured in both VPCs to enable communication between their private CIDR ranges.

## Security Configuration
Security Groups were configured to allow:
- SSH access to private instances through the Bastion Host.
- ICMP traffic between the private EC2 instances.
- Restricted inbound access using specific source IP addresses.

## Testing and Results

### 1. SSH Connectivity
Successfully accessed private EC2 instances through the Bastion Host using SSH.

### 2. Forward Connectivity
Tested connectivity from App-A to App-B:

Destination: 10.20.1.10

Result: 4 packets received, 0% packet loss.

### 3. Reverse Connectivity
Tested connectivity from App-B to App-A:

Destination: 10.10.2.10

Result: 4 packets received, 0% packet loss.

### 4. Controlled ICMP Failure
Temporarily removed the required ICMP inbound security group rule.

Result: Ping failed with 100% packet loss.

### 5. Recovery Test
Restored the ICMP inbound security group rule.

Result: Ping connectivity successfully restored with 0% packet loss.

## Cleanup
After completing the project and testing connectivity, the AWS resources created for the lab were cleaned up.

## Project Report
The detailed project report, architecture evidence, screenshots, and test results are provided in the `report` folder.

## Learning Outcomes
- Understanding VPC architecture and CIDR planning.
- Configuring public and private subnets.
- Understanding route tables and subnet associations.
- Establishing VPC Peering connections.
- Configuring security groups.
- Testing private network connectivity.
- Understanding controlled network failure and recovery.
- Cleaning up AWS resources after project completion.

---
**Project:** AWS VPC Peering  
**Region:** Asia Pacific (Sydney)  
**Platform:** Amazon Web Services (AWS)

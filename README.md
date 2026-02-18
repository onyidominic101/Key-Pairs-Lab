# Key-Pairs-Lab
**AWS EC2 Key Pairs Lab**
**A hands-on guide to creating and managing EC2 key pairs for secure SSH access to AWS instances**

**Overview**
This lab demonstrates the fundamental concepts of AWS EC2 key pair management and secure instance access. As part of the AWS Cloud Practitioner certification journey, this project showcases the practical implementation of public-key cryptography for authenticating SSH connections to EC2 instances.
**Key Concepts Covered:**
- Understanding asymmetric encryption (public/private key pairs)
- Creating EC2 key pairs in the AWS Management Console
- Converting AWS key formats for use with PuTTY on Windows
- Establishing secure SSH connections to EC2 instances

This lab is ideal for beginners learning AWS fundamentals and preparing for the Cloud Practitioner exam.

**AWS Services Used**
**Service	                                            Purpose**
**Amazon EC2**                                        Elastic Compute Cloud - provides virtual servers (instances) in the cloud
**EC2 Key Pairs**                                     Security credentials consisting of a public key (stored by AWS) and private key (downloaded by user) for SSH authentication
**AWS Management Console**                            Web-based interface for managing AWS resources and services

**Architecture**
**How EC2 Key Pairs Work**
┌─────────────────────────────────────────────────────────────┐
│                    AWS Cloud                                │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              EC2 Instance                            │  │
│  │  ┌────────────────────────────────────────────────┐  │  │
│  │  │  Public Key (stored on instance)               │  │  │
│  │  │  Validates incoming SSH connections           │  │  │
│  │  └────────────────────────────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                           ↕ SSH Connection
┌─────────────────────────────────────────────────────────────┐
│              Your Local Machine                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Private Key (downloaded .pem file)                 │  │
│  │  Converted to .ppk format for PuTTY                 │  │
│  │  Used to authenticate SSH connections              │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘

**Workflow Diagram**
1. Create Key Pair in AWS Console
   ↓
2. Download .pem File
   ↓
3. Install PuTTY & PuTTYgen
   ↓
4. Convert .pem to .ppk Format
   ↓
5. Configure PuTTY with Private Key
   ↓
6. SSH into EC2 Instance

**Screenshots**


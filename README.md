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

**Prerequisites**
Before starting this lab, you'll need:
- **AWS Account** - Free tier eligible
- **AWS Management Console Access** - With permissions to create EC2 key pairs
- **Windows Machine** - For PuTTY installation (Mac/Linux users can use native SSH)
- **Basic Networking Knowledge** - Understanding of SSH and public-key cryptography
- **Internet Connection** - To download PuTTY tools and access AWS Console
- **File Management Skills** - Ability to navigate file systems and manage downloads

**Setup Instructions**
**Step 1: Navigate to EC2 Key Pairs in AWS Console**
1. Log in to your AWS Management Console
2. Navigate to the **EC2 Dashboard**
3. In the left sidebar under **Network & Security**, click **Key Pairs**
4. Verify you're in the correct region (e.g., US East 1 - N. Virginia)

**Step 2: Create a New Key Pair**
1. Click the **Create key pair** button (orange button in top right)
2. Enter a descriptive name for your key pair (e.g., funkeypair)
3. Ensure **Key pair type** is set to **RSA**
4. Select **Private key file format** as **.pem** (for OpenSSH compatibility)
5. Click **Create key pair**

Key Pair Configuration:
├── Name: funkeypair
├── Type: RSA
├── Format: .pem
└── Status: Created 

**Step 3: Download the Private Key**
- Your .pem file will automatically download to your **Downloads** folder
- **Important**: Store this file securely - it's your only access to instances using this key pair
- Do not share this file with anyone

**Step 4: Install PuTTY and PuTTYgen**
1. Visit putty.org
2. Download the following files:
   - putty.exe - SSH client for connecting to instances
   - puttygen.exe - Key generator for converting key formats
3. Install both applications to your preferred location

**Step 5: Convert .pem Key to .ppk Format**
1.** Open PuTTYgen** (puttygen.exe)
2. Click **Load** under "Load an existing private key file"
3. Navigate to your **Downloads** folder
4. Change file filter to **All Files (.)** to see the .pem file
5. Select your downloaded .pem file (e.g., funkeypair.pem)
6. Click **Open**

**Step 6: Import and Convert the Key**
1. A dialog will appear: **"Successfully imported foreign key (OpenSSH SSH-2 private key)"**
2. Click **OK** to confirm the import
3. The key details will now display in PuTTYgen:
   - Public key for pasting into OpenSSH authorized_keys file
   - Key fingerprint
   - Key comment: imported-openssh-key

**Step 7: Save as Private Key**
1. Click Save private key button
2. Choose a location to save (same folder as .pem file recommended)
3. Name it the same as your key pair (e.g., funkeypair)
4. The file will be saved as .ppk format
5. Click **Save**

Saved Key Files:
├── funkeypair.pem (original AWS format)
└── funkeypair.ppk (PuTTY format) 

**Step 8: Verify Key Pair in AWS Console**
1. Return to the EC2 Key Pairs page in AWS Console
2. Verify your key pair appears in the list with:
   - Name: funkeypair
   - Type: rsa
   - Fingerprint: Displayed
   - Created: Timestamp shown
  
**Learning Outcomes**
Upon completing this lab, you will understand:

**Conceptual Knowledge**
- **Public-Key Cryptography** - How asymmetric encryption secures SSH connections
- **Key Pair Components** - The role of public and private keys in authentication
- **AWS Security Best Practices** - Proper key management and storage
- **SSH Authentication** - How key-based authentication works vs. password-based

**Practical Skills**
- **AWS Console Navigation** - Finding and managing EC2 resources
- **Key Pair Creation** - Creating security credentials in AWS
- **Key Format Conversion** - Converting between .pem and .ppk formats
- **PuTTY Configuration** - Setting up SSH clients for Windows
- **File Management** - Organizing and securing sensitive credentials

**AWS Cloud Practitioner Exam Readiness**
- Understanding EC2 fundamentals
- Knowledge of AWS security mechanisms
- Familiarity with AWS Management Console
- Comprehension of identity and access management basics

**Next Steps & Future Improvements**
**Immediate Next Steps**
1. **Launch an EC2 Instance** - Create a running instance using this key pair
2. **Connect via SSH** - Use PuTTY with the .ppk file to SSH into the instance
3. **Execute Commands** - Run basic Linux commands on the remote instance
4. **Terminate Instance** - Clean up resources to avoid charges

**Future Lab Enhancements**
-  **Security Groups Configuration** - Set up firewall rules for SSH access
-  **EC2 Instance Launch** - Complete hands-on instance creation and connection
-  **Bastion Host Setup** - Use key pairs for secure jump host access
-  **Multiple Key Pairs** - Manage different keys for different environments (dev/prod)
-  **Linux Command Basics** - Execute commands on connected instances
-  **CloudWatch Monitoring** - Monitor instance activity and SSH connections
-  **Key Rotation** - Implement key pair rotation best practices
-  **IAM Integration** - Connect key pairs with IAM roles and policies

**Advanced Topics**
- Implementing Systems Manager Session Manager as keyless alternative
- Using AWS Secrets Manager for key management
- Automating key pair creation with AWS CLI or Terraform
- Setting up MFA for additional security layers

**Key Takeaways**
**Concept	                                                          Importance**
**Private Key Security**                                            Never share or expose your .pem or .ppk files
**Key Pair Regions**	                                              Key pairs are region-specific; create in the region where you'll launch instances
**Format Compatibility**	                                          AWS uses .pem format; PuTTY on Windows requires .ppk format
**Backup Strategy**	                                                Store backup copies of private keys in secure locations
**Access Control**	                                                Restrict file permissions on private keys (chmod 400 on Linux/Mac)

**AWS Certification Alignment**
This lab directly supports the following AWS Cloud Practitioner exam domains:
- **Domain 1: Cloud Concepts** - Understanding AWS infrastructure
- **Domain 2: Security and Compliance** - Identity and access management
- **Domain 3: Technology** - EC2 and compute services
- **Domain 4: Billing and Pricing** - Understanding free tier eligibility

**Troubleshooting**
**Common Issues**
**Issue**: Cannot find .pem file in PuTTYgen file browser
- **Solution**: Change file filter from "PuTTY Private Key Files (.ppk)" to "All Files (.*)"

**Issue**: "Permissions error" when trying to use private key
- **Solution**: Ensure the .ppk file has appropriate read permissions; on Linux/Mac, run chmod 400 filename.ppk

**Issue**: Key pair not appearing in AWS Console
**Solution**: Verify you're viewing the correct AWS region; key pairs are region-specific

**Issue**: PuTTY connection refused
**Solution**: Ensure the EC2 instance is running and security groups allow SSH (port 22) access





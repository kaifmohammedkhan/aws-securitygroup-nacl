# Networking in AWS

Step-by-step tutorial on VPC, EC2, Security Groups, and NACLs with practical demo.

## 📺 Walkthrough
[![AWS Networking Tutorial](https://img.youtube.com/vi/5QTS06kvwfE/0.jpg)](https://www.youtube.com/watch?v=5QTS06kvwfE)

---

## 🛠 Step-by-Step Strategy

### Step 1: Create a VPC
Created a custom VPC with CIDR block `10.0.0.0/16` for networking isolation.

**Screenshots (6 total):**
![VPC Step 1-1](images/aws/Create VPC Step 1/vpc_step1-1.png)  
![VPC Step 1-2](images/aws/Create VPC Step 1/vpc_step1-2.png)  
![VPC Step 1-3](images/aws/Create VPC Step 1/vpc_step1-3.png)  
![VPC Step 1-4](images/aws/Create VPC Step 1/vpc_step1-4.png)  
![VPC Step 1-5](images/aws/Create VPC Step 1/vpc_step1-5.png)  
![VPC Step 1-6](images/aws/Create VPC Step 1/vpc_step1-6.png)

---

### Step 2: Create EC2 Instance
Launched an EC2 instance inside the VPC with default security groups.

**Screenshots (15 total):**
![EC2 Create 1](images/aws/Create EC2 Instance Step 2/ec2_create1.png)  
...  
![EC2 Create 15](images/aws/Create EC2 Instance Step 2/ec2_create15.png)

---

### Step 3: SSH Connect Through Terminal
Connected to the EC2 instance using SSH and verified connectivity.

**Screenshots (5 total):**
![SSH Connect 1](images/aws/SSH Connect Step 3/ssh_connect1.png)  
![SSH Connect 2](images/aws/SSH Connect Step 3/ssh_connect2.png)  
![SSH Connect 3](images/aws/SSH Connect Step 3/ssh_connect3.png)  
![SSH Connect 4](images/aws/SSH Connect Step 3/ssh_connect4.png)  
![SSH Connect 5](images/aws/SSH Connect Step 3/ssh_connect5.png)

---

### Step 4: Simple Python Webserver at Port 8000
Started a Python HTTP server on port `8000` to test traffic routing.

**Screenshots (2 total):**
![Webserver 1](images/aws/Web Server Step 4/webserver_1.png)  
![Webserver 2](images/aws/Web Server Step 4/webserver_2.png)

---

### Step 5: NACL & Security Group Defaults
By default, traffic on port `8000` was blocked by Security Groups and NACLs.

**Screenshots (5 total):**
![NACL Default 1](images/aws/NACL & Security Group Default Step 5/nacl_default1.png)  
![NACL Default 2](images/aws/NACL & Security Group Default Step 5/nacl_default2.png)  
![SG Port 22-1](images/aws/NACL & Security Group Default Step 5/securitygroup_port22_1.png)  
![SG Port 22-2](images/aws/NACL & Security Group Default Step 5/securitygroup_port22_2.png)  
![SG Port 22-3](images/aws/NACL & Security Group Default Step 5/securitygroup_port22_3.png)

---

### Step 6: Add Port 8000 to Security Groups
Updated Security Group rules to allow inbound traffic on port `8000`.

**Screenshots (7 total):**
![SG Port 8000-1](images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_1.png)  
...  
![SG Port 8000-7](images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_7.png)

---

### Step 7: NACL Port 8000 Deny
Added a NACL rule to explicitly deny inbound traffic on port `8000`.

**Screenshots (5 total):**
![NACL Deny 1](images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_1.png)  
![NACL Deny 2](images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_2.png)  
![NACL Deny 3](images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_3.png)  
![NACL Deny 4](images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_4.png)  
![NACL Deny 5](images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_5.png)

---

### Step 8: NACL Port 8000 Allow
Added an allow rule for port `8000` to demonstrate rule precedence.

**Screenshots (2 total):**
![NACL Allow 1](images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_1.png)  
![NACL Allow 2](images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_2.png)

---

### Step 9: NACL Rule Sequence Effects
Showed how NACL rule sequence impacts traffic: if a deny rule is placed first, it overrides allow rules for the same port.

**Screenshots (7 total):**
![NACL Sequence 1](images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_1.png)  
...  
![NACL Sequence 7](images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_7.png)

---

## 📝 Notes
- **VPC:** Provides isolated networking environment.  
- **EC2:** Compute resource inside VPC.  
- **Security Groups:** Stateful firewalls controlling inbound/outbound traffic.  
- **NACLs:** Stateless rules applied at subnet level.  
- **Rule Precedence:** Deny rules override allow rules if placed earlier.  
- **Demo:** Showed practical effects of SG and NACL configurations on port `8000`.

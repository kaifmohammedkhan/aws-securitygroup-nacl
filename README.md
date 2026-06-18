# Networking in AWS

Step-by-step tutorial on VPC, EC2, Security Groups, and NACLs with practical demo.

## 📺 Walkthrough
<iframe 
  width="560" height="315" 
  src="https://www.youtube.com/embed/5QTS06kvwfE?si=tnYn2sV13Dai0Udi" 
  title="AWS Networking Tutorial" 
  frameborder="0" 
  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
  allowfullscreen>
</iframe>

---

## 🛠 Step-by-Step Strategy

### Step 1: Create a VPC
Created a custom VPC with CIDR block `10.0.0.0/16` for networking isolation.

<div align="center">
  <img src="images/aws/Create VPC Step 1/vpc_step1-1.png" width="400"/>
  <img src="images/aws/Create VPC Step 1/vpc_step1-2.png" width="400"/>
  <img src="images/aws/Create VPC Step 1/vpc_step1-3.png" width="400"/>
  <img src="images/aws/Create VPC Step 1/vpc_step1-4.png" width="400"/>
  <img src="images/aws/Create VPC Step 1/vpc_step1-5.png" width="400"/>
  <img src="images/aws/Create VPC Step 1/vpc_step1-6.png" width="400"/>
</div>

---

### Step 2: Create EC2 Instance
Launched an EC2 instance inside the VPC with default security groups.

<div align="center">
  <img src="images/aws/Create EC2 Instance Step 2/ec2_create1.png" width="300"/>
  <img src="images/aws/Create EC2 Instance Step 2/ec2_create2.png" width="300"/>
  <!-- continue up to ec2_create15.png -->
  <img src="images/aws/Create EC2 Instance Step 2/ec2_create15.png" width="300"/>
</div>

---

### Step 3: SSH Connect Through Terminal
Connected to the EC2 instance using SSH and verified connectivity.

<div align="center">
  <img src="images/aws/SSH Connect Step 3/ssh_connect1.png" width="400"/>
  <img src="images/aws/SSH Connect Step 3/ssh_connect2.png" width="400"/>
  <img src="images/aws/SSH Connect Step 3/ssh_connect3.png" width="400"/>
  <img src="images/aws/SSH Connect Step 3/ssh_connect4.png" width="400"/>
  <img src="images/aws/SSH Connect Step 3/ssh_connect5.png" width="400"/>
</div>

---

### Step 4: Simple Python Webserver at Port 8000
Started a Python HTTP server on port `8000` to test traffic routing.

<div align="center">
  <img src="images/aws/Web Server Step 4/webserver_1.png" width="400"/>
  <img src="images/aws/Web Server Step 4/webserver_2.png" width="400"/>
</div>

---

### Step 5: NACL & Security Group Defaults
By default, traffic on port `8000` was blocked by Security Groups and NACLs.

<div align="center">
  <img src="images/aws/NACL & Security Group Default Step 5/nacl_default1.png" width="400"/>
  <img src="images/aws/NACL & Security Group Default Step 5/nacl_default2.png" width="400"/>
  <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_1.png" width="400"/>
  <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_2.png" width="400"/>
  <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_3.png" width="400"/>
</div>

---

### Step 6: Add Port 8000 to Security Groups
Updated Security Group rules to allow inbound traffic on port `8000`.

<div align="center">
  <img src="images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_1.png" width="300"/>
  <!-- continue up to securitygroup_port8000_7.png -->
  <img src="images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_7.png" width="300"/>
</div>

---

### Step 7: NACL Port 8000 Deny
Added a NACL rule to explicitly deny inbound traffic on port `8000`.

<div align="center">
  <img src="images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_1.png" width="400"/>
  <!-- continue up to nacl_port8000deny_5.png -->
  <img src="images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_5.png" width="400"/>
</div>

---

### Step 8: NACL Port 8000 Allow
Added an allow rule for port `8000` to demonstrate rule precedence.

<div align="center">
  <img src="images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_1.png" width="400"/>
  <img src="images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_2.png" width="400"/>
</div>

---

### Step 9: NACL Rule Sequence Effects
Showed how NACL rule sequence impacts traffic: if a deny rule is placed first, it overrides allow rules for the same port.

<div align="center">
  <img src="images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_1.png" width="300"/>
  <!-- continue up to nacl_rulesequence_7.png -->
  <img src="images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_7.png" width="300"/>
</div>

---

## 📝 Notes
- **VPC:** Provides isolated networking environment.  
- **EC2:** Compute resource inside VPC.  
- **Security Groups:** Stateful firewalls controlling inbound/outbound traffic.  
- **NACLs:** Stateless rules applied at subnet level.  
- **Rule Precedence:** Deny rules override allow rules if placed earlier.  
- **Demo:** Showed practical effects of SG and NACL configurations on port `8000`.

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Networking in AWS</title>
  <style>
    body { font-family: Arial, sans-serif; background: #111; color: #eee; line-height: 1.6; }
    h1, h2, h3 { color: #9cf; }
    .section { margin: 2rem 0; }
    .image-gallery { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 10px; }
    .image-gallery img { max-width: 300px; border: 2px solid #444; border-radius: 6px; }
    iframe { border: none; margin-top: 10px; }
  </style>
</head>
<body>

  <!-- Hero Section -->
  <section class="hero">
    <h1>Networking in AWS</h1>
    <p>Step-by-step tutorial on VPC, EC2, Security Groups, and NACLs with practical demo.</p>
  </section>

  <!-- YouTube Tutorial -->
  <section class="section">
    <h2>📺 Access the walkthrough</h2>
    <iframe 
      width="560" height="315" 
      src="https://www.youtube.com/embed/5QTS06kvwfE?si=tnYn2sV13Dai0Udi" 
      title="AWS Networking Tutorial" 
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
      allowfullscreen>
    </iframe>
  </section>

  <!-- Step-by-Step Strategy -->
  <section class="section">
    <h2>🛠 Step-by-Step Strategy</h2>

    <!-- Step 1 -->
    <h3>Step 1: Create a VPC</h3>
    <p>Created a custom VPC with CIDR block <code>10.0.0.0/16</code> for networking isolation.</p>
    <div class="image-gallery">
      <img src="images/aws/Create VPC Step 1/vpc_step1-1.png" />
      <img src="images/aws/Create VPC Step 1/vpc_step1-2.png" />
      <img src="images/aws/Create VPC Step 1/vpc_step1-3.png" />
      <img src="images/aws/Create VPC Step 1/vpc_step1-4.png" />
      <img src="images/aws/Create VPC Step 1/vpc_step1-5.png" />
      <img src="images/aws/Create VPC Step 1/vpc_step1-6.png" />
    </div>

    <!-- Step 2 -->
    <h3>Step 2: Create EC2 Instance</h3>
    <p>Launched an EC2 instance inside the VPC with default security groups.</p>
    <div class="image-gallery">
      <img src="images/aws/Create EC2 Instance Step 2/ec2_create1.png" />
      <img src="images/aws/Create EC2 Instance Step 2/ec2_create2.png" />
      <!-- … continue up to ec2_create15.png -->
      <img src="images/aws/Create EC2 Instance Step 2/ec2_create15.png" />
    </div>

    <!-- Step 3 -->
    <h3>Step 3: SSH Connect Through Terminal</h3>
    <p>Connected to the EC2 instance using SSH and verified connectivity.</p>
    <div class="image-gallery">
      <img src="images/aws/SSH Connect Step 3/ssh_connect1.png" />
      <img src="images/aws/SSH Connect Step 3/ssh_connect2.png" />
      <img src="images/aws/SSH Connect Step 3/ssh_connect3.png" />
      <img src="images/aws/SSH Connect Step 3/ssh_connect4.png" />
      <img src="images/aws/SSH Connect Step 3/ssh_connect5.png" />
    </div>

    <!-- Step 4 -->
    <h3>Step 4: Simple Python Webserver at Port 8000</h3>
    <p>Started a Python HTTP server on port <code>8000</code> to test traffic routing.</p>
    <div class="image-gallery">
      <img src="images/aws/Web Server Step 4/webserver_1.png" />
      <img src="images/aws/Web Server Step 4/webserver_2.png" />
    </div>

    <!-- Step 5 -->
    <h3>Step 5: NACL & Security Group Defaults</h3>
    <p>By default, traffic on port <code>8000</code> was blocked by Security Groups and NACLs.</p>
    <div class="image-gallery">
      <img src="images/aws/NACL & Security Group Default Step 5/nacl_default1.png" />
      <img src="images/aws/NACL & Security Group Default Step 5/nacl_default2.png" />
      <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_1.png" />
      <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_2.png" />
      <img src="images/aws/NACL & Security Group Default Step 5/securitygroup_port22_3.png" />
    </div>

    <!-- Step 6 -->
    <h3>Step 6: Add Port 8000 to Security Groups</h3>
    <p>Updated Security Group rules to allow inbound traffic on port <code>8000</code>.</p>
    <div class="image-gallery">
      <img src="images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_1.png" />
      <!-- … continue up to securitygroup_port8000_7.png -->
      <img src="images/aws/Add Port 8000 to SG Step 6/securitygroup_port8000_7.png" />
    </div>

    <!-- Step 7 -->
    <h3>Step 7: NACL Port 8000 Deny</h3>
    <p>Added a NACL rule to explicitly deny inbound traffic on port <code>8000</code>.</p>
    <div class="image-gallery">
      <img src="images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_1.png" />
      <!-- … continue up to nacl_port8000deny_5.png -->
      <img src="images/aws/NACL Port 8000 Deny Step 7/nacl_port8000deny_5.png" />
    </div>

    <!-- Step 8 -->
    <h3>Step 8: NACL Port 8000 Allow</h3>
    <p>Added an allow rule for port <code>8000</code> to demonstrate rule precedence.</p>
    <div class="image-gallery">
      <img src="images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_1.png" />
      <img src="images/aws/NACL Port 8000 Allow Step 8/nacl_port8000allow_2.png" />
    </div>

    <!-- Step 9 -->
    <h3>Step 9: NACL Rule Sequence Effects</h3>
    <p>Showed how NACL rule sequence impacts traffic: if a deny rule is placed first, it overrides allow rules for the same port.</p>
    <div class="image-gallery">
      <img src="images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_1.png" />
      <!-- … continue up to nacl_rulesequence_7.png -->
      <img src="images/aws/NACL Rule Sequence Allow Deny Step 9/nacl_rulesequence_7.png" />
    </div>

  </section>

  <!-- Notes Section -->
  <section class="section">
    <h2>📝 Notes</h2>
    <ul>
      <li><strong>VPC:</strong> Provides isolated networking environment.</li>
      <li><strong>EC2:</strong> Compute resource inside VPC.</li>
      <li><strong>Security Groups:</strong> Stateful firewalls controlling inbound/outbound traffic.</li>
      <li><strong>NACLs:</strong> Stateless rules applied at subnet level.</li>
      <li><strong>Rule Precedence:</strong> Deny rules override allow rules if placed earlier.</li>
      <li><strong>Demo:</strong> Showed practical effects of SG and NACL configurations on port 8000.</li>
    </ul>
  </section>

</body>
</html>

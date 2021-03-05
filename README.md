# Patch an AMI and update an Auto Scaling group

# Pre-Requisites
    Create EC2 Instance with below userdata also allow 80 port number in security group
    ---------------------------------------------------------------------------------------------
	  #!/bin/bash
	  yum install httpd -y
	  echo '<!DOCTYPE html> <html> <body> <h1>New AMI Auto Scaling Group for patching</h1> </body> </html>' > /var/www/html/index.html
	  chkconfig httpd on
    ----------------------------------------------------------------------------------------------
# Check output of httpd application
  ![image](https://user-images.githubusercontent.com/58024415/110099169-00c7f380-7dc7-11eb-8f68-bba8819455e3.png)
# Create AMI for the abouve server
  ![image](https://user-images.githubusercontent.com/58024415/110112010-2fe66100-7dd7-11eb-93f0-b2c244118d50.png)
# Check AMI Created or not
  ![image](https://user-images.githubusercontent.com/58024415/110112657-0a0d8c00-7dd8-11eb-9540-d1d606ae1a75.png)
# Create Launch configuration for old AMI
  Goto EC2 --> Launch Configuration --> Create Launch Configuration

  ![image](https://user-images.githubusercontent.com/58024415/110112975-6d97b980-7dd8-11eb-81f4-2ea1cbc7751d.png)
# Create AutoScaling Group with loadbalancer



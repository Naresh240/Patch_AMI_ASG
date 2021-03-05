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
  
# Create Launch configuration

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
  ![image](https://user-images.githubusercontent.com/58024415/110114622-f6175980-7dda-11eb-857d-c17c41796d65.png)
  
  Connect to instance and install httpd and check output using UI
  	
    yum install httpd -y
    echo '<!DOCTYPE html> <html> <body> <h1>OLD AMI Auto Scaling Group</h1> </body> </html>' > /var/www/html/index.html
    service httpd start
  ![image](https://user-images.githubusercontent.com/58024415/110116090-04667500-7ddd-11eb-8b49-880c1179277d.png)
 
  Check Load Balancer out as well
  ![image](https://user-images.githubusercontent.com/58024415/110118174-f6feba00-7ddf-11eb-99d0-603701d5c0f2.png)
# Create New Launch Configuration with CustomAMI
  ![image](https://user-images.githubusercontent.com/58024415/110118930-15b18080-7de1-11eb-8eff-c9b8a12fea8d.png)  
# Edit Auto scaling group and provide values as shown in below for Suspended processes and new launch configuration details
  ![image](https://user-images.githubusercontent.com/58024415/110119201-7d67cb80-7de1-11eb-9b55-8e95e06214e6.png)
  ![image](https://user-images.githubusercontent.com/58024415/110118308-2f05fd00-7de0-11eb-8807-797d95ad46d9.png)
# Increate desired and minimum number of instances and remove attached items from Suspended processes in auto scaling group for testing
  ![image](https://user-images.githubusercontent.com/58024415/110119371-ba33c280-7de1-11eb-9ac5-9f4535e11ebd.png)
  ![image](https://user-images.githubusercontent.com/58024415/110119524-f0714200-7de1-11eb-893f-891981d56d97.png)
# Check Launch configuration changed or not
  ![image](https://user-images.githubusercontent.com/58024415/110119815-4f36bb80-7de2-11eb-9f1a-c47de4785509.png)
# Check new instance attached to target group or not
  ![image](https://user-images.githubusercontent.com/58024415/110119925-683f6c80-7de2-11eb-940a-e792eec23547.png)
# Check Load Balancer Output again
  ![image](https://user-images.githubusercontent.com/58024415/110120025-8311e100-7de2-11eb-8071-feec4cc232fc.png)
# Now cleanup old AMI servers

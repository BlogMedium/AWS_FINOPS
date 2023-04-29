Replacing a Bastion Host with Amazon EC2 Systems Manager.

<img width="815" alt="Screen Shot 2023-04-29 at 3 55 00 PM" src="https://user-images.githubusercontent.com/32661402/235297908-ce13fb0e-7a63-4d3e-a8b7-1a64bdb38981.png">


![Uploading Screen Shot 2023-04-29 at 3.48.57 PM.png…]()



<img width="919" alt="Screen Shot 2023-04-29 at 3 57 38 PM" src="https://user-images.githubusercontent.com/32661402/235299132-7cf51baa-1143-4504-8f01-cbea72d8282f.png">






## Pre-requistes

#Create a EC2 Instance in Private subnet

* create a IAM role attach to the EC2
* Install SSM agent using the below commands as part of userdata.

```
#!/bin/bash
cd /tmp
sudo yum install -y https://s3.amazonaws.com/ec2-downloads-windows/SSMAgent/latest/linux_amd64/amazon-ssm-agent.rpm
sudo systemctl enable amazon-ssm-agent
sudo systemctl start amazon-ssm-agent
```


# create vpc endpoints for the following services
com.amazonaws.[region].ec2messages.
com.amazonaws.[region].ssmmessages.
com.amazonaws.[region].ssm


* The security group must allow inbound HTTPS (port 443) traffic from the resources in your VPC that communicate with the service.






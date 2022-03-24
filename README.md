# Voistask

Steps must be done on EC2

1-attach the instance to a new role with policy have the cloudwatch full access to allow using the service or getting the logs
2- connect to the ec2
3- apply the following commands
   - sudo yum update -y
   - sudo yum insrall -y awslogs  ---> to install the awslogs package and use it
   - open or cat "/etc/awslogs/aws.conf" ----> this is to know the logGroupName and logStreamName whereu can find the logs
   - edit or vim "/etc/awslogs/awscli.conf" ---> this for editing the aws region upon your need "use sudo"
   - sudo systemctl start awslogsd  ----> to start the installed package on your instance
   - sudo systemctl enable awslogsd.service  ---->  to enable it on the EC2

4-if you go to cloudwatch>logs>logGroups>logStream .. you will find the stored logs



The python script
 
this script takeing logs from the log group and send it to S3 bucket
-aws configure

1- install python or ensure that the EC2 has python installed ---> sudo yum install -y python3
2-pip3 install boto3 ----> this enable u to use boto3 in your script
  - pip3 show boto3
3-to run the script daily or make schedualed script
 -use crontab job
 sudo crontab -e ----> to create a new cronjob running my script daily
 0 0 * * * /usr/bin/python3 s.py 

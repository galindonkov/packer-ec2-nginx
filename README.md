### Description

A packer project that creates an ```AWS box``` with ```nginx``` installed on it

### Installed software needed prior to using the project

- Packer software installation : [link for packer](https://www.packer.io/intro/getting-started/install.html)

### AWS account required with related keys

- Creating an AWS acccount : [link to AWS](https://docs.aws.amazon.com/AmazonSimpleDB/latest/DeveloperGuide/AboutAWSAccounts.html)

- Creating and managing AWS keys : [how to](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html)

### The repo is having following file

- File ec2-nginx-box.json : a JSON file that configure the various components of Packer in order to create machine images 
with ```nginx``` installed on it.

### How to use the repo

- First of all clone the repo to your pc by : ```git clone git@github.com:galindonkov/packer-ec2-nginx.git```

- Switch to created directory ```packer-ec2-nginx``` by : ```cd packer-ec2-nginx/```

- You can either export your aws_access and aws_secret keys as environment variables or put them into the ec2-box.json file. Following link explains both variants : [set keys](https://www.packer.io/docs/builders/amazon.html#specifying-amazon-credentials)

- Created ```ec2-nginx-box.json``` does not have those keys into it, so in order to use it, please set the keys as environment variables first.

- Once both keys as exported, create the AWS box by : ```packer build ec2-nginx-box.json```

- Please note that created by ```packer``` will be in ```us-east-1``` region, so in order to use it choose the appropriate region :  [choose an AWS region](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-region.html)

### To Do

- Kitchen testing

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

- File ```Gemfile``` : It contains the ruby version and all required by the kitchen bundlers

- File ```.kitchen.yml``` : The kitchen testing configuration file

- File ```test/integration/default/check_pkg.rb``` : a ruby program used by the kitchen to test whether the ```nginx``` is installed

### How to use the repo

- First of all clone the repo to your pc by : ```git clone git@github.com:galindonkov/packer-ec2-nginx.git```

- Switch to created directory ```packer-ec2-nginx``` by : ```cd packer-ec2-nginx/```

- You can either export your aws_access and aws_secret keys as environment variables or put them into the ec2-box.json file. Following link explains both variants : [set keys](https://www.packer.io/docs/builders/amazon.html#specifying-amazon-credentials)

- Created ```ec2-nginx-box.json``` does not have those keys into it, so in order to use it, please set the keys as environment variables first.

- Once both keys as exported, create the AWS box by : ```packer build ec2-nginx-box.json```

- Please note that created by ```packer``` will be in ```us-east-1``` region, so in order to use it choose the appropriate region :  [choose an AWS region](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-region.html)


#### Additional steps that need to be prepared prior to the kitchen testing

- Set AMAZON key pair : [AWS key pair](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)

- Check following link to get aware how the kitchen file should looks like : [AWS kitchen file](https://docs.aws.amazon.com/opsworks/latest/userguide/cookbooks-101-basics-ec2.html)

- Installing ```ruby environment``` by : ```brew install rbenv```

- Add ~/.rbenv/bin to your ```$PATH``` for access to the rbenv command-line utility by : ```echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile```

- Reload your profile by : ```source ~/.bash_profile```

- Set up rbenv in your shell by : ```rbenv init```

- Install ```ruby```, recommended version is : ```rbenv install 2.3.1```

- Select the ruby version for the project by : ```rbenv local 2.3.1```

- Ensure the target version : ```rbenv versions```

- Once you've installed some Ruby versions, you'll want to install gems : ```gem install bundler```

- Install all of the required gems by : ```bundle install```

#### After above requirements are met, you can proceed with kitchen tests

- Change to the directory of the cloned repo : ```cd packer-ec2-nginx/```

- List kitchen environments if any : ```bundle exec kitchen list```

- Build new kitchen environment : ```bundle exec kitchen converge```

- Run the kitchen test by : ```bundle exec kitchen verify```

- After the test passed successfully you ca destroy the created environment by : ```bundle exec kitchen destroy```

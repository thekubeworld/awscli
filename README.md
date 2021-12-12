# awscli
Tips for aws client

## Initial setup
```
$ sudo apt-get -y install python-pip
$ sudo pip install awscli
$ aws configure
provide your data
$ aws --version
```

## Enable ssh to EC2 instance
To access the instance via ssh, you need SSH key pair set up in EC2.
Create a key pair via the CLI, copy the returned private key into a file in your
`~/.ssh/` dir and set permissions.

```
$ aws ec2 create-key-pair --key-name aws
$ vi ~/.ssh/id_rsa_aws
$ chmod 600 ~/.ssh/id_rsa_aws
$ aws ec2 describe-key-pair
```


## Running instance
t1.micro instance type is available via Amazon Linux AMI.
This image also allow to connect via ssh.

```
$ aws ec2 run-instances --image-id ami-7b3db00c \
                        --count 1 \
                        --instance-type t1.micro
                        --key-name awstest
```

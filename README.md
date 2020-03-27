## What is CI CD?

**CI** - Continuous Integration

**CD** - Continuous Delivery/Continuous Deployment

CICD is the automating the process of building, testing, merging, delivering and deploying code. We do this because it saves drastic amounts of time and efficiency of work. We do this by having the same programming environment across all steps of the CICD pipeline, so can see easily where the code is/isn't working.

## What is an automation server

An automation server **(Jenkins)** is a server which listens to the code sent to it and will pass it on through to the test node. You can give your code settings to restrict the builds location, send emails when code is passed through, merge branched code, and automate the process.

I.e: Whenever code is pushed to GitHub, Jenkins will listen and give instructions on how to test the code, and push this forward to the slave node to be tested.

## Why do we restrict builds and how?

We restrict our builds to a slave node so we continue to test our code on a new machine. We do this because the code could break, and if it does break, it shouldn't be on our own machines.

To restrict the build location you have to set Jenkins to link the code to a slave node, where it will be tested on.

## AWS and EC2

### Setting up an EC2 on AWS

1. Select EC2

2. Click on Instances: Launch Instance

3. Select the box you want to use (Ubuntu 18.04)

4. Choose an instance

5. Configure Instance Details:

  - Network: DevOpsStudents
  - Subnet: DevOpsStudentSubnet
  - Auto-assign Public IP: Enable


6. Add storage

7. Add tags:

  - Name: James-eng54-<specify>
  - Cohort: Eng54


8. Configure Security Group:

  - Select an existing security group: Find mine


9. Select the key pair


**If you make a new keypair:**

From Downloads
```
mv <keyname> ~/.ssh
```
to move the key to `.ssh` folder


**To access the EC2 server:**
```
ssh -i ~/.ssh/<keyname> ubuntu@<public IP>
```
or
```
ssh -o 'identitiesOnly yes' -issh -o 'identitiesOnly yes' -i ~/.ssh/<keyname> ubuntu@<public IP>
```

**To transfer files into the EC2:**
```
scp -i ~/.ssh/<keyname> -r <route>/<to>/<file> ubuntu@<public IP>:/<location>/<in EC2>
```


**Rsync** will sync directories together, keeping one appearing the same as the other.

```
rsync -r <directory>/ <directory>/<in EC2>
```

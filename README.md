# AWS-LOAD-BALANCER
## NAME: RISHAB P DOSHI.
## REG NO: 212224240134
## AIM
To use Elastic Load Balancing (ELB) and Auto Scaling services to load balance and automatically scale an AWS infrastructure.

## ALGORITHM
### Step 1: Create an AMI for Auto Scaling
Open the EC2 console, confirm that Web Server 1 is running (2/2 status checks passed), select the instance, and choose Actions → Image and templates → Create image. Name it "WebServerAMI" and create it. This AMI will be used to launch identical instances later.

### Step 2: Create a Target Group and Load Balancer
Create a Target Group named "LabGroup" (type: Instances, VPC: Lab VPC) without registering targets yet. Then create an Application Load Balancer named "LabELB" under Lab VPC, mapped to Public Subnet 1 and Public Subnet 2, using the Web Security Group, with the HTTP:80 listener forwarding to LabGroup.

### Step 3: Create a Launch Template and Auto Scaling Group
Create a Launch Template named "LabConfig" using the WebServerAMI, instance type t2.micro, key pair "vockey", the Web Security Group, and Detailed CloudWatch monitoring enabled. Using this template, create an Auto Scaling group named "Lab Auto Scaling Group" attached to Private Subnet 1 and Private Subnet 2, linked to the LabGroup target group, with desired/minimum/maximum capacity of 2/2/6 and a target tracking scaling policy set to maintain 60% average CPU utilization.

### Step 4: Verify Load Balancing
Confirm that two new "Lab Instance" EC2 instances were launched by Auto Scaling and that both show a "healthy" status in the LabGroup target group. Copy the Load Balancer's DNS name and open it in a browser to confirm the application is being served correctly through the load balancer.

### Step 5: Test Auto Scaling
Lower the scaling policy's target CPU value to 50% to make scaling trigger sooner, then use the application's "Load Test" feature to generate high CPU load across the instances. Monitor the CloudWatch alarms (AlarmLow/AlarmHigh) until AlarmHigh enters the "In alarm" state, then verify in the EC2 console that additional instances were automatically launched to handle the load.

### Step 6: Terminate the Original Web Server
Select Web Server 1 (the original instance used to create the AMI) and terminate it, since it is no longer needed once the Auto Scaling group is managing instances independently.

## COMMANDS
No CLI commands are used in this experiment, as it is performed entirely through the AWS Management Console (GUI-based setup) using EC2, Elastic Load Balancing, Auto Scaling, and CloudWatch services.

## OUTPUT

## OVERVIEW OF EC2

<img width="1918" height="995" alt="image" src="https://github.com/user-attachments/assets/9fc5b5ea-4fab-41f1-b5e5-315cba4917d2" />

## WEB SERVER INSTANCE

<img width="1918" height="1005" alt="image" src="https://github.com/user-attachments/assets/9d503554-0d42-493f-b97d-b7ee5dff8073" />

## CREATING IMAGE FOR WEB SERVER INSTANCE

<img width="1917" height="978" alt="image" src="https://github.com/user-attachments/assets/bd6a0790-a711-4f3e-aa68-1c0b34c1466d" />


<img width="1918" height="980" alt="image" src="https://github.com/user-attachments/assets/32ac653c-bc0e-4668-af6c-11119d0cac41" />

## CREATING NEW TARGET GROUP FOR LOAD BALANCER AND STEPS

<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/0b562aa7-4254-4f3f-b872-857aaa91abcc" />

<img width="1918" height="1007" alt="image" src="https://github.com/user-attachments/assets/58e84acd-f1e5-4ff0-8b82-45a2750946a8" />

<img width="1919" height="907" alt="image" src="https://github.com/user-attachments/assets/a5f0b37a-3ec4-48a7-ad76-07ed2e3e0847" />

<img width="1918" height="976" alt="image" src="https://github.com/user-attachments/assets/7aa417c4-f7dc-4b9b-8e9d-79822400a784" />

## CREATING A NEW LOAD BALANCER
<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/46aa0c6c-e660-4a4d-a029-2f7b0a27b1ed" />

<img width="1918" height="987" alt="image" src="https://github.com/user-attachments/assets/8625d240-5b8c-4cb6-8d91-9965496133b9" />

<img width="1918" height="963" alt="image" src="https://github.com/user-attachments/assets/0e607e40-abac-4518-8d12-423b59da820c" />

## CREATE AND LAUNCH TEMPLATES

<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/1f930a2f-b051-45ce-a1b2-df19522e1a8c" />

<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/ba11ef25-0cff-44c9-adf6-f2e6a06a1173" />

<img width="1917" height="1002" alt="image" src="https://github.com/user-attachments/assets/28a327d4-b4d3-4019-a9eb-292c54bff49c" />

## CREATE A AUTO SCALE BALANCER FOR TEMPLATE(LABCONFIG)

<img width="1917" height="998" alt="image" src="https://github.com/user-attachments/assets/3f3cea92-9f56-4883-9050-59edb89d61f3" />

<img width="1905" height="964" alt="image" src="https://github.com/user-attachments/assets/63e6d2d3-b2bf-49d8-aaeb-8ba5af860e87" />

<img width="1917" height="855" alt="image" src="https://github.com/user-attachments/assets/e3cb5eaa-4586-4fb4-b8f0-7e4ee872664d" />

<img width="1915" height="879" alt="image" src="https://github.com/user-attachments/assets/8de6388a-9673-406b-a665-02e49e831355" />

<img width="1918" height="933" alt="image" src="https://github.com/user-attachments/assets/ec5f3b16-3323-42fa-8036-4a3ec67b0b1a" />

<img width="1914" height="961" alt="image" src="https://github.com/user-attachments/assets/e3d31368-c9dc-43e6-bcf9-47ef8183fe72" />

<img width="1911" height="942" alt="image" src="https://github.com/user-attachments/assets/392ef56c-b6e4-45cf-b39c-f2cee39c03c6" />

## NEW INSTANCES CREATED(LAB INSTANCE) CHECKING IN TARGET GROUPS

<img width="1918" height="961" alt="image" src="https://github.com/user-attachments/assets/a7bc1866-dfab-4712-bc7d-52bc5d41cf15" />

<img width="1911" height="948" alt="image" src="https://github.com/user-attachments/assets/a4b975f0-10e3-43dc-972d-cc9f684d7523" />

## CHECKING ALARMS

<img width="1919" height="1005" alt="image" src="https://github.com/user-attachments/assets/f695ba72-52c1-4f25-99a4-63907c70d6ef" />

<img width="1888" height="891" alt="image" src="https://github.com/user-attachments/assets/c3bc73cf-184f-46bc-a4ba-0c6b2f837489" />

<img width="1917" height="976" alt="image" src="https://github.com/user-attachments/assets/15c7809a-1429-4178-a848-93fad3a48020" />


## CHECKING LOAD BALANCER DNS NAME THROUGH WEB BROWSER

<img width="1917" height="1003" alt="image" src="https://github.com/user-attachments/assets/28112945-02c5-49c2-a324-acc8dd35d4c6" />

<img width="1919" height="1008" alt="image" src="https://github.com/user-attachments/assets/c7c2660b-2dff-4571-a7b5-9f523d8bf43b" />

<img width="1919" height="1003" alt="image" src="https://github.com/user-attachments/assets/4273f482-b548-452c-848a-db4d0bdbab34" />


## VIEW AND TERMINATE WEB SERVER INSTANCE

<img width="1919" height="957" alt="image" src="https://github.com/user-attachments/assets/320bee96-9429-4801-b9f0-7d06b05360e3" />

<img width="1919" height="996" alt="image" src="https://github.com/user-attachments/assets/4dfbbc60-cb72-425b-bfd0-81abb60d0545" />


## SUBMISSION DETAILS

<img width="1538" height="580" alt="image" src="https://github.com/user-attachments/assets/f8bf7859-b842-4acf-9404-72a5246dc542" />


<img width="1917" height="994" alt="image" src="https://github.com/user-attachments/assets/a457e164-24c0-47bc-bac7-d5816c084e5e" />





## RESULT
Thus, an AMI was created from a running EC2 instance, a Load Balancer was configured to distribute traffic across multiple instances, an Auto Scaling group was set up with a target tracking scaling policy, and the infrastructure was verified to automatically scale out under increased load using CloudWatch alarms.

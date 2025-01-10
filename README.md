# NBA Scoreboard App
This project demonstrates the use of an event-driven application.


# About the Project
This project was created to provide updated statistics around the NBA


## **Features**
- Request live NBA game scores using an external API.
- Sends update scores to subscribers via SMS/Email with Amazon SNS.
- Scheduled updates using Amazon EventBridge.


## Prerequisites
- understanding of basic Python language
- AWS account
- sportsdata.io account + API Key


## Setup Instructions
### **Clone the Repository**
```bash
git clone https://github.com/sgoins2/nba-scoreboard-app.git
cd day_2-nba-scoreboard-app
```

### **Create an SNS Topic**
1. Log into AWS Console
2. Navigate over to AWS SNS and click 'create topic'
3. After creating a topic, make an email  subscription and verify your email address


### **Create an SNS publishing policy and Lambda policy**
1. Copy the ARN under the subscription principal of your SNS topic
2. Navigate over to IAM and click 'create policy'
3. Click the JSON tab and create an sns policy that allows SNS publishing. 
4. Paste your SNS topic ARN next to the Resource section.
5. Create a role and add your sns policy + AWS Lambda Basic Exec Role. Be sure to verify that both roles are added and save the role


### **Deploy the NBA Lambda Function**
1. Navigate over to Lambda and create a new function with the attached role that was previously created in IAM.
2. Next, add in your python code to call the sportsdata.io acct and return the game scores in readable language and click 'Deploy'.
3. Click the "configuration" tab and the environment variable section to setup the environment variables for your python code including your API KEY and SNS Topic ARN
4. Go to the Test tab and test your code (should get a status code of 200)


### **Setup the EventBridge rule and schedule**
1. Navigate over to EventBridge and create a schedule rule type.
2. Configure the cron expression for the rule details
3. Create the schedule and verify notifications in your source email


### **What We Learned**
1. Designing a notification system with AWS SNS and Lambda.
2. Securing AWS services with least privilege IAM policies.
3. Automating workflows using EventBridge.
4. Integrating external APIs into cloud-based workflows.
# Week 0 — Billing and Architecture

## Required Homework

### 1. Set up an IAM User

I was able to create an admin IAM user

![IAM-Management-Console](https://user-images.githubusercontent.com/17044063/221654561-6e5095aa-62c1-4926-95d0-93f41a24d9e0.png)

### 2. Enable MFA
I was able to add MFA on both my root account and my IAM user
![IAM-Management-Console (1)](https://user-images.githubusercontent.com/17044063/221656328-c7565df4-8ea1-4f41-a897-5d145f4e9a38.png)


### 3. AWS CLI

I was able to connect Gitpod to my Github and launched Gitpod on the browser to access my workspace.
To ensure that the AWS CLI is installed automatically everytime I open the workspace, the workspace below was added in the gitpod.yaml file

``` ruby
cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

### 4. AWS Cloudshell

I accessed the AWS Cloudshell and ran some commands to enable auto prompt and find my Account ID
![AWS-CloudShell](https://user-images.githubusercontent.com/17044063/221660170-eb05cd79-e41e-4ae6-bad8-2e6b843797ec.png)

### 5. AWS Budget

I created a budget using both the CLI method and the UI method. When creating the budget using CLI, I used the code below:

<details><summary><b>Json Code to create budget</b></summary>
<p>


```json
   {
    "BudgetLimit": {
        "Amount": "1",
        "Unit": "USD"
    },
    "BudgetName": "Example Tag Budget",
    "BudgetType": "COST",
    "CostFilters": {
        "TagKeyValue": [
            "user:Key$value1",
            "user:Key$value2"
        ]
    },
    "CostTypes": {
        "IncludeCredit": true,
        "IncludeDiscount": true,
        "IncludeOtherSubscription": true,
        "IncludeRecurring": true,
        "IncludeRefund": true,
        "IncludeSubscription": true,
        "IncludeSupport": true,
        "IncludeTax": true,
        "IncludeUpfront": true,
        "UseBlended": false
    },
    "TimePeriod": {
        "Start": 1477958399,
        "End": 3706473600
    },
    "TimeUnit": "MONTHLY"
}
```

</p>
</details>

![AWS Budget](https://user-images.githubusercontent.com/17044063/221664222-49c21924-b0d0-4f75-b36e-aeb0b60c602d.png)


### 6. Billing Alarm
I was able to create a billing alarm as shown in the screenshot below

![Billing Alarm](https://user-images.githubusercontent.com/17044063/221661341-bff76c95-92c0-43fc-8902-86f4a6719b6c.png)

### 7. Logical / Architecture Diagram

Below is the logical / architecture diagram created

```
https://lucid.app/lucidchart/7a3eb0d4-6c4b-40fc-ab74-9e18266754e5/view?page=0_0#
```
![Screenshot (252)](https://user-images.githubusercontent.com/17044063/221663238-96f69db8-a32f-4bb9-9336-0118f16a976f.png)





### **AWS Hands-on Lab: Introduction to EC2, IAM Users, and Roles**

**Objective**: Gain a foundational understanding of AWS IAM (users, roles, and policies) and EC2 instances.

**Lab Outline:**
#### 1. Create a Custom IAM Policy for EC2 Read-Only Access:

Access the AWS Management Console and navigate to IAM.
Create a new custom policy using the Visual Editor.
Review and finalize the policy creation.
#### 2. Create an IAM Role with the Custom Policy:

Start the process of creating an IAM role.
Choose EC2 as the trusted entity.
Attach the previously created custom policy.
Complete the role creation process.
#### 3. Launch an EC2 Instance:

Navigate to the EC2 dashboard.
Initiate the process to launch a new EC2 instance.
Set up the EC2 instance configurations.
Define security group settings.
Launch the EC2 instance.
#### 4. Associate the IAM Role with the EC2 Instance:

Access the EC2 dashboard.
Locate and select the newly launched EC2 instance.
Use the instance settings to attach the IAM role.
#### 5. Create an IAM User with the Custom Policy:

Define a new policy that allows an IAM user to assume a role.
Attach this new policy to the IAM user.
Verification Steps:
Confirm the IAM role association with the EC2 instance.
Validate the attached policies for the IAM user.
Conclusion:
Reinforce the importance of AWS IAM in context with EC2.
Reflect on the learning outcomes of the lab.
This outline provides a clear, step-by-step roadmap of the hands-on lab activities, allowing both instructors and students to easily follow along and understand the progression of the lab.


### **Lab Steps**:

#### **Task 1: Create a Custom IAM Policy for EC2 Read-Only Access**

1. **Log in to the AWS Management Console**.
2. Navigate to `Services -> IAM`.
3. In the left navigation pane, select `Policies`, then click the `Create policy` button.
4. In the "Visual Editor":
   - Choose `EC2` for the service.
   - Expand the "List" action and select `DescribeInstances`.
   - Ensure "All resources" is selected.
5. Click `Review policy`.
6. Name the policy `EC2ReadOnlyCustom` and give it a description: "Provides read-only access to EC2 instances".
7. Click `Create policy`.

#### **Task 2: Create an IAM Role with the Custom Policy**

1. In the IAM dashboard, click on `Roles` in the left pane, then click the `Create role` button.
2. For the trusted entity type:
   - Choose `AWS service`.
   - In the next pane, choose `EC2`.
   - Click `Next: Permissions`.
3. Search and attach the `EC2ReadOnlyCustom` policy you created earlier.
4. Click `Next: Tags` and `Next: Review`.
5. Name the role `EC2ReadOnlyRole` and provide a description: "Role with read-only access to EC2 instances".
6. Click `Create role`.

#### **Task 3: Launch an EC2 Instance**

1. Navigate to `Services -> EC2`.
2. Click on the `Launch Instance` button.
3. For the Amazon Machine Image (AMI), choose the free tier eligible `Amazon Linux 2 AMI`.
4. Choose the `t2.micro` instance type and proceed to the `Next: Configure Instance Details` step.
5. Keep default configurations and proceed through `Add Storage` and `Add Tags`.
6. In `Configure Security Group`, create a new group and ensure SSH (port 22) access is allowed from your IP.
7. Review and click `Launch`.
8. You'll be prompted for a key pair:
   - If you already have one, select it.
   - Otherwise, create a new key pair, download, and save it securely.
9. Click `Launch Instances`.

#### **Task 4: Associate the IAM Role with the EC2 Instance**

1. In the EC2 Dashboard, find and select the instance you just created.
2. Under the Actions menu, navigate to Security and choose Modify IAM Role.
3. From the list provided, select the EC2ReadOnlyRole and then click Update IAM Role.

#### **Task 5: Create an IAM User with the Custom Policy**

1. Back in the IAM dashboard, select `Users` on the left pane, then click the `Add user` button.
2. Provide a username, for example, `EC2ReadOnlyUser`, and choose `AWS Management Console access`. Set a custom password or auto-generate one.
3. On the permissions page, click `Attach policies directly` and attach the `EC2ReadOnlyCustom` policy.
4. Review the user details to ensure the policy is attached and click `Create user`.


---

### **Verification**:

1. Navigate to the EC2 dashboard and select your instance. Ensure the associated role (`EC2ReadOnlyRole`) is visible in the instance details.
2. In the IAM dashboard, select `Users`, then `EC2ReadOnlyUser`. Confirm  `EC2ReadOnlyCustom` is attached.

### **Conclusion**:
Upon completing this lab, You will have a well-rounded understanding of how AWS IAM (users, roles, policies) interacts with EC2 instances.

--- 

### ** other Example: ** 
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Deny",
            "Action": [
                "ec2:StopInstances",
                "ec2:TerminateInstances"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": "ec2:*",
            "Resource": "*"
        }
    ]
}

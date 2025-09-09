### 🔐 AWS Account Creation & IAM
When we create an AWS account for any organization, it comes with a root user that has superuser privileges. This account has full access to all AWS resources and should only be used for initial setup and critical tasks.
Since we don’t typically get admin access for any system in an organization if we belongs to Dev/QA teams, we create IAM (Identity and Access Management) users from the root account. These users can also be added to groups and assigned specific permissions based on their roles.
IAM AWS Service allows us to:
* Create users for authentication
* Attach permissions or policies to control access, follow the principle of least privilege, ensuring users only have access to what they need
IAM handles both authentication (who the user is) and authorization (what the user is allowed to do) for AWS services.

### 🏦 Analogy: AWS is Like a Bank
Think of AWS like a bank:
You might be allowed to enter the bank, but you can’t access the vault unless you're authorized. Similarly, in AWS, unrestricted access to resources can be dangerous. If someone accesses the account with root privileges, they could accidentally delete or modify critical resources.
To prevent this, IAM helps organizations manage access securely by:
* Creating users with defined permissions through attaching policies/roles
* Attaching policies that specify what each user can do
* Ensuring users are authenticated and authorized only for what they need based on RBAC(ROle Based Access Control)

Step1:
<img width="925" height="452" alt="image" src="https://github.com/user-attachments/assets/331afe5c-29d9-49cc-badb-6da4980f6d21" />
Step2:
<img width="925" height="455" alt="image" src="https://github.com/user-attachments/assets/8a542a8f-12b7-41d5-a3b4-47a42d2050a6" />
Step3:
<img width="923" height="455" alt="image" src="https://github.com/user-attachments/assets/c687fa18-e8fe-44ae-a32f-e33ee4f6c736" />






# SurvConf API

## Debugging

## Deployment

### Environment Variables

- ACCESS_KEY - AWS Access key
- API KEY -
- API SECRET -
- APP ID -
- BUCKET - AWS bucket to store data in
- REGION - AWS region (ex us-east-1)
- SECRET_KEY - AWS Secret key
- TOKEN_APP_NAME - subdomain of Node APP

## AWS Permissions

Here’s how you can create an AWS access key that allows access to a single S3 bucket. This involves creating an IAM user, attaching a custom policy to restrict access, and generating an access key.

---

### **Step 1: Log in to the AWS Management Console**

1. Go to the [AWS Management Console](https://aws.amazon.com/console/).
2. Log in with your AWS account credentials.

---

### **Step 2: Create a New IAM User**

1. Navigate to the **IAM Management Console**:
   - In the search bar, type "IAM" and select it.
2. Go to **Users** > **Add users**.
3. Enter a **User name** (e.g., `s3-bucket-access-user`).
4. Choose **Access key - Programmatic access** under **Access type**.
5. Click **Next** to move to permissions.

---

### **Step 3: Attach a Custom Policy**

1. On the **Permissions** page, select **Attach policies directly**.
2. Click **Create policy** to create a custom policy.
3. In the JSON tab, paste the following policy, replacing `YOUR_BUCKET_NAME` with your bucket's name:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Action": [
           "s3:GetObject",
           "s3:PutObject",
           "s3:DeleteObject",
           "s3:ListBucket"
         ],
         "Resource": [
           "arn:aws:s3:::YOUR_BUCKET_NAME",
           "arn:aws:s3:::YOUR_BUCKET_NAME/*"
         ]
       }
     ]
   }
   ```

4. Click **Next: Tags**. Add tags (optional), then click **Review policy**.
5. Name the policy (e.g., `s3-bucket-access-policy`) and click **Create policy**.
6. Back on the **Permissions** page, search for the custom policy you just created and select it.
7. Click **Next: Tags** > **Next: Review**, and then click **Create user**.

#### **Step 4: Generate and Download Access Key**

1. Once the user is created, you'll see a success page with an **Access key ID** and **Secret access key**.
2. **Download the CSV file** or copy these credentials securely. You won’t be able to retrieve the secret key again.
3. Click **Close**.

## Updating requirements

Install the updated libraries

```bash
pip install --upgrade -r requirements.txt
```

Update the requirements file

```bash
pip freeze > requirements.txt
```

## Development

1. Create a virtual env

```bash
python -m venv venv
```

2. Activate the virtual environment

The method for activation depends on your operating system:
On Windows:

```
venv\Scripts\activate
```

On macOS/Linux:

```bash
source venv/bin/activate
```

3. Install the requirements

```bash
pip install -r requirements.txt
```

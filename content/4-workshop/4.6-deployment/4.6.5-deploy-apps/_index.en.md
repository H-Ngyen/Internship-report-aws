---
title : "Deploy Applications"
date :  "2024-01-01" 
weight : 5
chapter : false
pre : " <b> 4.6.5 </b> "
---

### Deploy Applications

In this section, we will deploy the carbuyer-aws application to both EC2 instances and connect with the ALB setup in step 4.6.4.

#### 1. Deploy Customer Service

1. Connect to Customer Service instance (already connected from step 4.6.3)

2. Clone repository:

```bash
cd ~
git clone https://github.com/khaizr0/carbuyer-aws.git
cd carbuyer-aws/customer-service
```

![](/images/5-workshop/6.deployment/046-clone.png?width=90pc)

3. Install dependencies:

```bash
npm install
```

![](/images/5-workshop/6.deployment/047-npm.png?width=90pc)

4. Create `.env` file for Customer Service:

```bash
nano .env
```

Paste the following content (replace with actual values):

```env
# Server Configuration
PORT=3000
BASE_URL=http://YOUR_ALB_DNS_NAME
SESSION_SECRET=carbuyer_session_secret_2024_production

# AWS Configuration (DynamoDB + S3)
AWS_REGION=ap-southeast-1
AWS_ACCESS_KEY_ID=your_access_key_from_4.2.3
AWS_SECRET_ACCESS_KEY=your_secret_key_from_4.2.3

# S3 + CloudFront
S3_BUCKET=carbuyer-fcj-bucket
S3_PUBLIC_URL=https://YOUR_CLOUDFRONT_ID.cloudfront.net

# JWT Configuration
JWT_SECRET=carbuyer_jwt_secret_production_2024

# Lambda Email Service
LAMBDA_EMAIL_API_URL=https://YOUR_API_GATEWAY_URL/prod/send-email
LAMBDA_EMAIL_API_KEY=your_api_key_from_4.5.4

# Google Maps Configuration
GOOGLE_MAPS_EMBED_URL=https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2098.047098103885!2d106.70327503669084!3d10.772062044514472!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31752f3acf87eaeb%3A0xc969a1975f3be32a!2sBitexco%20Financial%20Tower!5e0!3m2!1svi!2s!4v1760106692113!5m2!1svi!2s
```

![](/images/5-workshop/6.deployment/048-env.png?width=90pc)

Save file: `Ctrl + X`, `Y`, `Enter`

5. Start application with PM2:

```bash
pm2 start app.js --name "customer-service"
pm2 startup
pm2 save
```
![](/images/5-workshop/6.deployment/052-pm2.png?width=90pc)

#### 2. Deploy Admin Service

1. Connect to Admin Service instance (already connected from step 4.6.3):

```bash
# From Customer Service instance
ssh -o StrictHostKeyChecking=accept-new -i ~/.ssh/carbuyer-keypair.pem ec2-user@ADMIN_PRIVATE_IP
```

![](/images/5-workshop/6.deployment/053-admin.png?width=90pc)

2. Clone repository and install:

```bash
cd ~
git clone https://github.com/khaizr0/carbuyer-aws.git
cd carbuyer-aws/employee-and-admin-service
npm install
```

![](/images/5-workshop/6.deployment/054-admin-install.png?width=90pc)

3. Create `.env` file for Admin Service:

```bash
nano .env
```

```env
# Server Configuration
PORT=3001
BASE_URL=http://YOUR_ALB_DNS_NAME
SESSION_SECRET=carbuyer_session_secret_2024_production

# AWS Configuration (DynamoDB + S3)
AWS_REGION=ap-southeast-1
AWS_ACCESS_KEY_ID=your_access_key_from_4.2.3
AWS_SECRET_ACCESS_KEY=your_secret_key_from_4.2.3

# S3 + CloudFront
S3_BUCKET=carbuyer-fcj-bucket
S3_PUBLIC_URL=https://YOUR_CLOUDFRONT_ID.cloudfront.net

# JWT Configuration
JWT_SECRET=carbuyer_jwt_secret_production_2024

# Lambda Email Service
LAMBDA_EMAIL_API_URL=https://YOUR_API_GATEWAY_URL/prod/send-email
LAMBDA_EMAIL_API_KEY=your_api_key_from_4.5.4
```

![](/images/5-workshop/6.deployment/055-admin-env.png?width=90pc)

4. Start Admin Service with PM2:

```bash
pm2 start app.js --name "admin-service"
pm2 startup
pm2 save
```

![](/images/5-workshop/6.deployment/056-admin-pm2.png?width=90pc)

#### 3. Add Instances to Target Groups

1. Add Customer Service instance:

- Access **Target Groups** → Select `carbuyer-customer-tg`

![](/images/5-workshop/6.deployment/090-tg.png?width=90pc)

- **Targets** tab → **Register targets**

![](/images/5-workshop/6.deployment/091-tg.png?width=90pc)

- Select Customer Service instance
- **Port**: `3000`
- Click **Include as pending below** → **Register pending targets**
![](/images/5-workshop/6.deployment/092-tg.png?width=90pc)

- Confirm result after register

![](/images/5-workshop/6.deployment/100-tg.png?width=90pc)

2. Add Admin Service instance:

- Select `carbuyer-admin-employee-tg`

![](/images/5-workshop/6.deployment/093-tg.png?width=90pc)

- **Targets** tab → **Register targets**
- Select Admin Service instance
- **Port**: `3001`

![](/images/5-workshop/6.deployment/094-tg.png?width=90pc)

- Click **Include as pending below** → **Register pending targets**

- Confirm result after register

![](/images/5-workshop/6.deployment/101-tg.png?width=90pc)

3. Check Health Status:

- Wait 2-3 minutes for health checks to run
- Both targets must be in `healthy` state

![healthy](/images/5-workshop/6.deployment/098-health.png?width=90pc)

![healthy](/images/5-workshop/6.deployment/099-health.png?width=90pc)

Next proceed to [4.6.6 - Test Application](../4.6.6-test-application) to verify the application.
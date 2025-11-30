---
title : "Test Application"
date :  "2024-01-01" 
weight : 6
chapter : false
pre : " <b> 4.6.6 </b> "
---

### Test Application

After deployment, verify the functions:

#### 1. Get ALB DNS Name

From step 4.6.4:
- DNS name: `carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com`

#### 2. Access Customer Service

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com
```

![](/images/5-workshop/6.deployment/102-customer-webui.png?width=90pc)

#### 3. Access Admin

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com/admin/login
```

![](/images/5-workshop/6.deployment/103-admin-webui.png?width=90pc)

Login credentials (from DynamoDB data import in step 4.3.2):
- **Email**: `nguyenvanb@example.com`
- **Password**: `hashedpassword123`

![](/images/5-workshop/6.deployment/104-admin-webui.png?width=90pc)

#### 4. Access Employee

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com/employee/login
```

![](/images/5-workshop/6.deployment/105-employee-webui.png?width=90pc)

Login credentials:
- **Email**: `caophankhai2004@gmail.com`
- **Password**: `hashedpassword123`

![](/images/5-workshop/6.deployment/106-employee-webui.png?width=90pc)

#### 5. Test Email Function

- Access Customer Service home page
- Select any car → Click **Register Test Drive**

![](/images/5-workshop/6.deployment/108-booking.png?width=90pc)

- Fill in information:
  - **Name**: Your name
  - **Phone Number**: 0123456789
  - **Email**: Your real email
  - **Date**: Select date
  - **Time**: Select time
- Click **Register**

![](/images/5-workshop/6.deployment/107-booking.png?width=90pc)

- Check email (may take 10-30 seconds):

![](/images/5-workshop/6.deployment/109-booking.png?width=90pc)

- On employee page

![](/images/5-workshop/6.deployment/110-booking.png?width=90pc)

{{% notice info %}}
Email may be delayed 10-30 seconds due to Lambda cold start. Check Spam folder if email not found.
{{% /notice %}}
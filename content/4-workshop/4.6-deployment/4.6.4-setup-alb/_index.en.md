---
title : "Setup Application Load Balancer"
date :  "2024-01-01" 
weight : 4
chapter : false
pre : " <b> 4.6.4 </b> "
---

### Setup Application Load Balancer (ALB)

In this section, we will configure Application Load Balancer to prepare for deploying applications with cookie-based session persistence.

### Why ALB Before Deployment?

- **Session Management**: ALB manages sticky sessions for admin/employee
- **Load Balancing**: Distributes traffic between instances
- **Health Checks**: Automatically checks application status
- **Scalability**: Easy to add instances later

### Steps

#### 1. Create Security Group for ALB

Access [EC2 Console](https://console.aws.amazon.com/ec2/) → **Security Groups** → **Create security group**:

![](/Internship-report-aws/images/5-workshop/6.deployment/057-alb.png?width=90pc)

- **Security group name**: `carbuyer-alb-sg`
- **Description**: `Security group for CarBuyer ALB`
- **VPC**: Select VPC created in step 4.2.1

**Inbound rules:**
- **Type**: HTTP, **Port**: 80, **Source**: 0.0.0.0/0
- **Type**: HTTPS, **Port**: 443, **Source**: 0.0.0.0/0

**Outbound rules:** (default - All traffic)

![](/Internship-report-aws/images/5-workshop/6.deployment/058-alb.png?width=90pc)

#### 2. Update Security Groups for EC2

**Customer Service Security Group:**

![](/Internship-report-aws/images/5-workshop/6.deployment/059-alb.png?width=90pc)

- Add rule: **Type**: Custom TCP, **Port**: 3000, **Source**: `carbuyer-alb-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/060-alb.png?width=90pc)

**Admin Service Security Group:**

![](/Internship-report-aws/images/5-workshop/6.deployment/061-alb.png?width=90pc)

- Add rule: **Type**: Custom TCP, **Port**: 3001, **Source**: `carbuyer-alb-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/062-alb.png?width=90pc)

#### 3. Create Target Groups

**Target Group for Customer Service:**

Access **Target Groups** → **Create target group**:

![](/Internship-report-aws/images/5-workshop/6.deployment/063-alb.png?width=90pc)

1. Create target group:
- **Target type**: `Instances`
- **Target group name**: `carbuyer-customer-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/064-alb.png?width=90pc)

- **Protocol**: `HTTP`, **Port**: `3000`
- **VPC**: Select VPC created

![](/Internship-report-aws/images/5-workshop/6.deployment/065-alb.png?width=90pc)

- **Health check path**: `/`

![](/Internship-report-aws/images/5-workshop/6.deployment/066-alb.png?width=90pc)

Click **Next**

2. Register targets (recommended):
- **Leave empty** - Don't select any instances
- Click **Next**

![](/Internship-report-aws/images/5-workshop/6.deployment/067-alb.png?width=90pc)

3. Review and create:
- Verify configuration
- Click **Create target group**

![](/Internship-report-aws/images/5-workshop/6.deployment/068-alb.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/6.deployment/069-alb.png?width=90pc)

**Target Group for Admin & Employee Service:**

Repeat the steps above with:
- **Target group name**: `carbuyer-admin-employee-tg`
- **Protocol**: `HTTP`, **Port**: `3001`
- **Health check path**: `/admin/login` or `/employee/login`

![](/Internship-report-aws/images/5-workshop/6.deployment/070-alb.png?width=90pc)

#### 4. Configure Stickiness for Admin & Employee Target Group

In Target Group `carbuyer-admin-employee-tg`:
- **Actions** → **Edit target group attributes**

![](/Internship-report-aws/images/5-workshop/6.deployment/071-alb.png?width=90pc)

- **Stickiness**: `Enabled`
- **Stickiness type**: `Load balancer generated cookie`
- **Stickiness duration**: `1 days`

![](/Internship-report-aws/images/5-workshop/6.deployment/072-alb.png?width=90pc)

- Select **save changes**

#### 5. Create Application Load Balancer

Access **Load Balancers** → **Create load balancer** 

![](/Internship-report-aws/images/5-workshop/6.deployment/073-alb.png?width=90pc)

Select create **Application Load Balancer**:

![](/Internship-report-aws/images/5-workshop/6.deployment/074-alb.png?width=90pc)

**Basic configuration:**
- **Name**: `carbuyer-alb`
- **Scheme**: `Internet-facing`
- **IP address type**: `IPv4`

![](/Internship-report-aws/images/5-workshop/6.deployment/075-alb.png?width=90pc)

**Network mapping:**
- **VPC**: Select VPC created
- **Mappings**: Select both public subnets

![](/Internship-report-aws/images/5-workshop/6.deployment/076-alb.png?width=90pc)

- **Security groups**: Select `carbuyer-alb-sg`

**Listeners and routing:**
- **Protocol**: HTTP, **Port**: 80

![](/Internship-report-aws/images/5-workshop/6.deployment/077-alb.png?width=90pc)

- **Default action**: Forward to `carbuyer-customer-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/078-alb.png?width=90pc)

Click **Create load balancer**

#### 6. Configure Listener Rules

After ALB is created, go to **Listeners** tab:

**Rule 1 - Admin paths:**
- Click on listener **HTTP:80**
- **Manage rules** → **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/079-alb.png?width=90pc)

**Name and tags:**
- **Name**: `admin-rule`

**Conditions:**
- **Add condition** → Select **Path**
- **Path pattern**: `/admin/*`

![](/Internship-report-aws/images/5-workshop/6.deployment/080-alb.png?width=90pc)

**Actions:**
- **Routing action**: `Forward to target groups`
- **Target group**: Select `carbuyer-admin-employee-tg`
- **Weight**: `1`, **Percent**: `100%`

![](/Internship-report-aws/images/5-workshop/6.deployment/081-alb.png?width=90pc)

Click **Next**

2. Set rule priority:
- **Priority**: `100` (or any number from 1-50,000)
- Click **Next**

![](/Internship-report-aws/images/5-workshop/6.deployment/082-alb.png?width=90pc)

3. Review and create:
- Verify configuration
- Click **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/083-alb.png?width=90pc)

**Rule 2 - Employee paths:**
- **Add rule** following similar steps:

1. Add rule:
- **Name**: `employee-rule`
- **Condition**: Path = `/employee/*`

![](/Internship-report-aws/images/5-workshop/6.deployment/084-alb.png?width=90pc)

- **Action**: Forward to `carbuyer-admin-employee-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/085-alb.png?width=90pc)

2. Set rule priority:
- **Priority**: `200` (different from admin rule)

![](/Internship-report-aws/images/5-workshop/6.deployment/086-alb.png?width=90pc)

3. Review and create:
- Click **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/087-alb.png?width=90pc)

**Additional rules:**

Add the following rules using similar steps:

| Priority | Rule Name | Path Pattern | Target Group | Stickiness |
|----------|-----------|--------------|--------------|------------|
| 100 | admin-rule | `/admin` | carbuyer-admin-employee-tg | Off |
| 101 | admin-rule-2 | `/admin/*` | carbuyer-admin-employee-tg | Off |
| 200 | employee-rule | `/employee/*` | carbuyer-admin-employee-tg | Off |
| 300 | private-rule | `/private/*` | carbuyer-admin-employee-tg | Off |
| 400 | login-rule | `/login` | carbuyer-admin-employee-tg | Off |
| 500 | forgot-psw-rule | `/forgot*` | carbuyer-admin-employee-tg | Off |
| 600 | reset-psw-rule | `/reset-password*` | carbuyer-admin-employee-tg | Off |

![](/Internship-report-aws/images/5-workshop/6.deployment/096-alb.png?width=90pc)

#### 7. Get ALB DNS Name

In **Load Balancers** → Select `carbuyer-alb`:

![](/Internship-report-aws/images/5-workshop/6.deployment/091-dns.png?width=90pc)

- Copy **DNS name**: `carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com`

![](/Internship-report-aws/images/5-workshop/6.deployment/092-dns.png?width=90pc)

{{% notice info %}}
**Save ALB DNS Name:**
This DNS name will be used in step 4.6.5 to configure applications
{{% /notice %}}

#### 8. Verify ALB Status

- **State**: `Active`
- **Target Groups**: Both target groups created
- **Listeners**: HTTP:80 with configured rules

### Verify Results

After completion, you will have:

- ✅ ALB with DNS name ready
- ✅ Target Groups for Customer (port 3000) and Admin/Employee (port 3001)
- ✅ Sticky sessions configured for admin/employee
- ✅ Security Groups updated
- ✅ Listener rules for path-based routing

![](/Internship-report-aws/images/5-workshop/6.deployment/089-alb-2.png?width=90pc)

Next proceed to [4.6.5 - Deploy Applications](../4.6.5-deploy-apps) to deploy applications and add instances to Target Groups.
---
title : "Setup Application Load Balancer"
date :  "2024-01-01" 
weight : 4
chapter : false
pre : " <b> 4.6.4 </b> "
---

### Setup Application Load Balancer (ALB)

Trong phần này, chúng ta sẽ cấu hình Application Load Balancer để chuẩn bị cho việc deploy applications với cookie-based session persistence.

### Tại sao cần ALB trước khi deploy?

- **Session Management**: ALB quản lý sticky sessions cho admin/employee
- **Load Balancing**: Phân phối traffic giữa các instances
- **Health Checks**: Tự động kiểm tra trạng thái applications
- **Scalability**: Dễ dàng thêm instances sau này

### Các bước thực hiện

#### 1. Tạo Security Group cho ALB

Truy cập [EC2 Console](https://console.aws.amazon.com/ec2/) → **Security Groups** → **Create security group**:

![](/Internship-report-aws/images/5-workshop/6.deployment/057-alb.png?width=90pc)

- **Security group name**: `carbuyer-alb-sg`
- **Description**: `Security group for CarBuyer ALB`
- **VPC**: Chọn VPC đã tạo ở bước 4.2.1

**Inbound rules:**
- **Type**: HTTP, **Port**: 80, **Source**: 0.0.0.0/0
- **Type**: HTTPS, **Port**: 443, **Source**: 0.0.0.0/0

**Outbound rules:** (mặc định - All traffic)

![](/Internship-report-aws/images/5-workshop/6.deployment/058-alb.png?width=90pc)

#### 2. Cập nhật Security Groups cho EC2

**Customer Service Security Group:**

![](/Internship-report-aws/images/5-workshop/6.deployment/059-alb.png?width=90pc)

- Thêm rule: **Type**: Custom TCP, **Port**: 3000, **Source**: `carbuyer-alb-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/060-alb.png?width=90pc)

**Admin Service Security Group:**

![](/Internship-report-aws/images/5-workshop/6.deployment/061-alb.png?width=90pc)

- Thêm rule: **Type**: Custom TCP, **Port**: 3001, **Source**: `carbuyer-alb-sg`

![](/Internship-report-aws/images/5-workshop/6.deployment/062-alb.png?width=90pc)

#### 3. Tạo Target Groups

**Target Group cho Customer Service:**

Truy cập **Target Groups** → **Create target group**:

![](/Internship-report-aws/images/5-workshop/6.deployment/063-alb.png?width=90pc)

1. Create target group:
- **Target type**: `Instances`
- **Target group name**: `carbuyer-customer-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/064-alb.png?width=90pc)

- **Protocol**: `HTTP`, **Port**: `3000`
- **VPC**: Chọn VPC đã tạo

![](/Internship-report-aws/images/5-workshop/6.deployment/065-alb.png?width=90pc)

- **Health check path**: `/`

![](/Internship-report-aws/images/5-workshop/6.deployment/066-alb.png?width=90pc)

Click **Next**

2. Register targets (recommended):
- **Để trống** - Không chọn instance nào
- Click **Next**

![](/Internship-report-aws/images/5-workshop/6.deployment/067-alb.png?width=90pc)

3. Review and create:
- Kiểm tra cấu hình
- Click **Create target group**

![](/Internship-report-aws/images/5-workshop/6.deployment/068-alb.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/6.deployment/069-alb.png?width=90pc)

**Target Group cho Admin & Employee Service:**

Lặp lại các bước trên với:
- **Target group name**: `carbuyer-admin-employee-tg`
- **Protocol**: `HTTP`, **Port**: `3001`
- **Health check path**: `/admin/login` hoặc `/employee/login`

![](/Internship-report-aws/images/5-workshop/6.deployment/070-alb.png?width=90pc)

#### 4. Cấu hình Stickiness cho Admin & Employee Target Group

Trong Target Group `carbuyer-admin-employee-tg`:
- **Actions** → **Edit target group attributes**

![](/Internship-report-aws/images/5-workshop/6.deployment/071-alb.png?width=90pc)

- **Stickiness**: `Enabled`
- **Stickiness type**: `Load balancer generated cookie`
- **Stickiness duration**: `1 days`

![](/Internship-report-aws/images/5-workshop/6.deployment/072-alb.png?width=90pc)

- Chọn **save changes**

#### 5. Tạo Application Load Balancer

Truy cập **Load Balancers** → **Create load balancer** 

![](/Internship-report-aws/images/5-workshop/6.deployment/073-alb.png?width=90pc)

Chọn create **Application Load Balancer**:

![](/Internship-report-aws/images/5-workshop/6.deployment/074-alb.png?width=90pc)

**Basic configuration:**
- **Name**: `carbuyer-alb`
- **Scheme**: `Internet-facing`
- **IP address type**: `IPv4`

![](/Internship-report-aws/images/5-workshop/6.deployment/075-alb.png?width=90pc)

**Network mapping:**
- **VPC**: Chọn VPC đã tạo
- **Mappings**: Chọn cả 2 public subnets

![](/Internship-report-aws/images/5-workshop/6.deployment/076-alb.png?width=90pc)

- **Security groups**: Chọn `carbuyer-alb-sg`
**Listeners and routing:**
- **Protocol**: HTTP, **Port**: 80

![](/Internship-report-aws/images/5-workshop/6.deployment/077-alb.png?width=90pc)

- **Default action**: Forward to `carbuyer-customer-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/078-alb.png?width=90pc)

Click **Create load balancer**

#### 6. Cấu hình Listener Rules

Sau khi ALB được tạo, vào **Listeners** tab:

**Rule 1 - Admin paths:**
- Click vào listener **HTTP:80**
- **Manage rules** → **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/079-alb.png?width=90pc)

**Name and tags:**
- **Name**: `admin-rule`

**Conditions:**
- **Add condition** → Chọn **Path**
- **Path pattern**: `/admin/*`

![](/Internship-report-aws/images/5-workshop/6.deployment/080-alb.png?width=90pc)

**Actions:**
- **Routing action**: `Forward to target groups`
- **Target group**: Chọn `carbuyer-admin-employee-tg`
- **Weight**: `1`, **Percent**: `100%`

![](/Internship-report-aws/images/5-workshop/6.deployment/081-alb.png?width=90pc)

Click **Next**

2. Set rule priority:
- **Priority**: `100` (hoặc bất kỳ số từ 1-50,000)
- Click **Next**

![](/Internship-report-aws/images/5-workshop/6.deployment/082-alb.png?width=90pc)

3. Review and create:
- Kiểm tra cấu hình
- Click **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/083-alb.png?width=90pc)

**Rule 2 - Employee paths:**
- **Add rule** tiếp theo các bước tương tự:

1. Add rule:
- **Name**: `employee-rule`
- **Condition**: Path = `/employee/*`

![](/Internship-report-aws/images/5-workshop/6.deployment/084-alb.png?width=90pc)

- **Action**: Forward to `carbuyer-admin-employee-tg`

![](/Internship-report-aws/images/5-workshop/6.deployment/085-alb.png?width=90pc)

2. Set rule priority:
- **Priority**: `200` (khác với admin rule)

![](/Internship-report-aws/images/5-workshop/6.deployment/086-alb.png?width=90pc)

3. Review and create:
- Click **Add rule**

![](/Internship-report-aws/images/5-workshop/6.deployment/087-alb.png?width=90pc)

**Các rules còn lại:**

Thêm các rules sau theo các bước tương tự:

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

#### 7. Lấy ALB DNS Name

Trong **Load Balancers** → Chọn `carbuyer-alb`:

![](/Internship-report-aws/images/5-workshop/6.deployment/091-dns.png?width=90pc)

- Sao chép **DNS name**: `carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com`

![](/Internship-report-aws/images/5-workshop/6.deployment/092-dns.png?width=90pc)

{{% notice info %}}
**Lưu lại ALB DNS Name:**
DNS name này sẽ được sử dụng trong bước 4.6.5 để cấu hình applications
{{% /notice %}}

#### 8. Kiểm tra ALB Status

- **State**: `Active`
- **Target Groups**: Cả 2 target groups đã được tạo
- **Listeners**: HTTP:80 với rules đã cấu hình

### Kiểm tra kết quả

Sau khi hoàn thành, bạn sẽ có:

- ✅ ALB với DNS name sẵn sàng
- ✅ Target Groups cho Customer (port 3000) và Admin/Employee (port 3001)
- ✅ Sticky sessions được cấu hình cho admin/employee
- ✅ Security Groups được cập nhật
- ✅ Listener rules cho path-based routing

![](/Internship-report-aws/images/5-workshop/6.deployment/089-alb-2.png?width=90pc)


Tiếp theo chuyển sang [4.6.5 - Deploy Applications](../4.6.5-deploy-apps) để deploy ứng dụng và add instances vào Target Groups.
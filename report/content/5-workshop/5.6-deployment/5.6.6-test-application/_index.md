---
title : "Test Application"
date :  "2024-01-01" 
weight : 6
chapter : false
pre : " <b> 5.6.6 </b> "
---

### Kiểm tra ứng dụng

Sau khi deploy xong, kiểm tra các chức năng:

#### 1. Lấy ALB DNS Name

Từ bước 5.6.4:
- DNS name: `carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com`

#### 2. Truy cập Customer Service

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com
```

![](/images/5-workshop/6.deployment/102-customer-webui.png?width=90pc)

#### 3. Truy cập Admin

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com/admin/login
```

![](/images/5-workshop/6.deployment/103-admin-webui.png?width=90pc)

Thông tin đăng nhập (từ DynamoDB data import ở bước 5.3.2):
- **Email**: `nguyenvanb@example.com`
- **Password**: `hashedpassword123`

![](/images/5-workshop/6.deployment/104-admin-webui.png?width=90pc)

#### 4. Truy cập Employee

```
http://carbuyer-alb-xxxxxxxxx.ap-southeast-1.elb.amazonaws.com/employee/login
```

![](/images/5-workshop/6.deployment/105-employee-webui.png?width=90pc)

Thông tin đăng nhập:
- **Email**: `caophankhai2004@gmail.com`
- **Password**: `hashedpassword123`

![](/images/5-workshop/6.deployment/106-employee-webui.png?width=90pc)

#### 5. Kiểm tra chức năng gửi email

- Truy cập trang chủ Customer Service
- Chọn một xe bất kỳ → Click **Đăng ký lái thử**

![](/images/5-workshop/6.deployment/108-booking.png?width=90pc)

- Điền thông tin:
  - **Họ tên**: Tên của bạn
  - **Số điện thoại**: 0123456789
  - **Email**: Email thật của bạn
  - **Ngày đặt**: Chọn ngày
  - **Thời gian**: Chọn giờ
- Click **Đăng ký**

![](/images/5-workshop/6.deployment/107-booking.png?width=90pc)

- Kiểm tra email (có thể mất 10-30 giây):

![](/images/5-workshop/6.deployment/109-booking.png?width=90pc)

- Bên trang employee

![](/images/5-workshop/6.deployment/110-booking.png?width=90pc)

{{% notice info %}}
Email có thể bị delay 10-30 giây do Lambda cold start. Kiểm tra cả thư mục Spam nếu không thấy email.
{{% /notice %}}
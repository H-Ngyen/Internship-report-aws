---
title : "Test Lambda Function"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.5.2. </b> "
---

### Test Lambda Function

Trong phần này, chúng ta sẽ test Lambda function với 2 loại email: Reset Password và Booking Confirmation.

#### 1. Tạo Test Event cho Reset Password

Trong tab **Test**:
![](/Internship-report-aws/images/5-workshop/5.email/009-test.png?width=90pc)

**Test event action:**
- Chọn **Create new event**

**Invocation type:**
- Chọn **Synchronous**

![](/Internship-report-aws/images/5-workshop/5.email/010-test.png?width=90pc)

**Event name:**
- Nhập: `test-reset-password`

**Event sharing settings:**
- Chọn **Private**

**Template:**
- Chọn **Hello World**

**Event JSON:**
Xoá nội dung mặc định và paste:

```json
{
  "type": "RESET_PASSWORD",
  "data": {
    "email": "test@example.com",
    "resetUrl": "https://yourapp.com/reset-password?token=abc123"
  }
}
```

Click **Save**

#### 2. Chạy Test Reset Password

Click **Test** để chạy test event. Kiểm tra kết quả trong **Execution results**:

![](/Internship-report-aws/images/5-workshop/5.email/010-run-test-reset.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/5.email/011-run-test-reset.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/5.email/012-run-test-reset.png?width=90pc)

#### 3. Tạo Test Event cho Booking Confirmation

Tạo test event mới trong tab **Test**:

![](/Internship-report-aws/images/5-workshop/5.email/013-run-test-booking.png?width=90pc)

**Test event action:**
- Chọn **Create new event**

**Event name:**
- Nhập: `test-booking-confirmation`

![](/Internship-report-aws/images/5-workshop/5.email/014-run-test-booking.png?width=90pc)

**Event sharing settings:**
- Chọn **Private**

**Template:**
- Chọn **Hello World**

**Event JSON:**
Xoá nội dung mặc định và paste:

```json
{
  "type": "BOOKING_CONFIRMATION",
  "data": {
    "email": "customer@example.com",
    "hoTenKH": "Nguyễn Văn A",
    "id": "BK001",
    "soDT": "0901234567",
    "ngayTao": "2024-01-15",
    "time": "14:30"
  }
}
```

Click **Save**

#### 4. Chạy Test Booking Confirmation

Chọn test event `test-booking-confirmation` và click **Test**:

![](/Internship-report-aws/images/5-workshop/5.email/012-run-test-booking.png?width=90pc)

Bạn đã hoàn thành việc test Lambda function! Tiếp theo chuyển sang [4.5.3 - Setup API Gateway](../4.5.3-setup-api-gateway).
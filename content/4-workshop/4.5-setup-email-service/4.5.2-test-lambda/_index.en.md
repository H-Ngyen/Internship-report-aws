---
title : "Test Lambda Function"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 4.5.2. </b> "
---

### Test Lambda Function

In this section, we will test the Lambda function with 2 types of emails: Reset Password and Booking Confirmation.

#### 1. Create Test Event for Reset Password

In the **Test** tab:
![](/Internship-report-aws/images/5-workshop/5.email/009-test.png?width=90pc)

**Test event action:**
- Select **Create new event**

**Invocation type:**
- Select **Synchronous**

![](/Internship-report-aws/images/5-workshop/5.email/010-test.png?width=90pc)

**Event name:**
- Enter: `test-reset-password`

**Event sharing settings:**
- Select **Private**

**Template:**
- Select **Hello World**

**Event JSON:**
Delete the default content and paste:

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

#### 2. Run Reset Password Test

Click **Test** to run the test event. Check the results in **Execution results**:

![](/Internship-report-aws/images/5-workshop/5.email/010-run-test-reset.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/5.email/011-run-test-reset.png?width=90pc)

![](/Internship-report-aws/images/5-workshop/5.email/012-run-test-reset.png?width=90pc)

#### 3. Create Test Event for Booking Confirmation

Create a new test event in the **Test** tab:

![](/Internship-report-aws/images/5-workshop/5.email/013-run-test-booking.png?width=90pc)

**Test event action:**
- Select **Create new event**

**Event name:**
- Enter: `test-booking-confirmation`

![](/Internship-report-aws/images/5-workshop/5.email/014-run-test-booking.png?width=90pc)

**Event sharing settings:**
- Select **Private**

**Template:**
- Select **Hello World**

**Event JSON:**
Delete the default content and paste:

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

#### 4. Run Booking Confirmation Test

Select the `test-booking-confirmation` test event and click **Test**:

![](/Internship-report-aws/images/5-workshop/5.email/012-run-test-booking.png?width=90pc)

You have completed testing the Lambda function! Next, proceed to [4.5.3 - Setup API Gateway](../4.5.3-setup-api-gateway).
---
title: "Week 9 Worklog"
date: "2024-01-01"
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
- Set up S3, CloudFront, and VPC Gateway Endpoint.
- Develop Lambda email service with Nodemailer.
- Modify code of 2 services to be compatible with Lambda.
- Deploy application to EC2.
- Continue writing workshop documentation.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference |
|-----|------|------------|----------------|-----------|
| 2 | - Continue writing workshop <br> - Set up S3 and CloudFront <br>&emsp; + Create S3 bucket for images <br>&emsp; + Configure bucket policies <br>&emsp; + Create CloudFront distribution <br>&emsp; + Configure VPC Gateway Endpoint for S3 <br> - Develop Lambda email service <br>&emsp; + Create Lambda function with Nodemailer <br>&emsp; + Configure SMTP <br>&emsp; + Create API Gateway with REST endpoints | 10/11/2025 | 10/11/2025 |  |
| 3 | - Watch videos and complete quizzes for Week 7 and Week 8 <br> - Modify code of 2 services and reconfigure to be compatible with new Lambda | 11/11/2025 | 11/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/2249de2a-47b6-4476-8a46-68b161aa51f8> <https://specialforce.awsstudygroup.com/#/certPublic/62b0159b-570d-436e-a561-f1d7de56244a> |
| 4 | Watch videos and complete quizzes for Week 9 and Week 10 | 12/11/2025 | 12/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/164eeffd-a33d-4964-a322-ac4f31527f18> <https://specialforce.awsstudygroup.com/#/certPublic/296362cd-86ab-4e0d-afbe-caae8f43462a> |
| 5 | - Continue writing workshop <br> - Deploy application to EC2 <br>&emsp; + Create Security Groups <br>&emsp; + Launch EC2 instances <br>&emsp; + Install Node.js and PM2 <br>&emsp; + Deploy Customer and Admin services <br> - Configure Application Load Balancer <br>&emsp; + Create Target Groups <br>&emsp; + Set up path-based routing <br> - Fix some application errors after deployment | 13/11/2025 | 13/11/2025 |  |
| 6 | Watch videos and complete quizzes for Week 11 | 14/11/2025 | 14/11/2025 | <https://specialforce.awsstudygroup.com/#/certPublic/59d150de-68d2-4ba2-88df-573948555fa6> |

### Week 9 Achievements:
- Completed videos and quizzes for weeks 7, 8, 9, 10, and 11.
- Successfully set up S3 bucket, CloudFront distribution, and VPC Gateway Endpoint for S3.
- Developed Lambda email service with Nodemailer, configured SMTP, and created API Gateway with REST endpoints.
- Modified code of 2 services to integrate with Lambda email service.
- Successfully deployed Customer and Admin services to EC2 with Node.js and PM2.
- Configured Application Load Balancer with Target Groups and path-based routing.
- Fixed some errors after deployment.
- Continued writing workshop documentation.

### Challenges:
- Initially used Amazon SES for SMTP configuration but encountered some limitations, so switched to another SMTP provider.
- Path-based routing on ALB required precise configuration to correctly route between Customer and Admin services.
- Encountered some errors after deployment that needed debugging and fixing.

### Plan for Next Week:
- Re-test the entire system (Customer, Admin, Lambda email).
- Fix bugs, optimize, and improve UI/UX.
- Continue finalizing workshop documentation.

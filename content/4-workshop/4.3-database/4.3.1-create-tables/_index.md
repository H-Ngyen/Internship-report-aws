---
title : "Tạo DynamoDB Tables"
date :  "2024-01-01" 
weight : 1
chapter : false
pre : " <b> 4.3.1 </b> "
---

1. Khởi động AWS CloudShell tại [Giao diện CloudShell](https://console.aws.amazon.com/cloudshell/home?region=ap-southeast-1)

2. **Open ap-southeast-1 environment**

![](/images/5-workshop/3.dynamodb/001-dynamoDB.png?width=90pc)

3. Gõ lệnh **`aws configure`**

4. Nhập chi tiết thông tin từ file csv ở phần [4.2.3 Tạo Access Keys](../../4.2-Prerequiste/4.2.3-create-access-keys/):

- **AWS Access Key ID**
- **AWS Secret Access Key**
- **Default region name**: `ap-southeast-1`
- **Default output format**

![](/images/5-workshop/3.dynamodb/002-dynamoDB.png?width=90pc)

5. Để tạo table, ta sử dụng lệnh **`create-table`**. Gõ lệnh:

```bash
aws dynamodb create-table --table-name DanhGia --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name DatLichKH --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name KieuDang --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name LoaiPhuKien --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name MauXe --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name NguyenLieuXe --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name PhuKien --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name Slider --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name ThuongHieu --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name TinTuc --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name User --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1

aws dynamodb create-table --table-name XeOto --attribute-definitions AttributeName=id,AttributeType=S --key-schema AttributeName=id,KeyType=HASH --billing-mode PAY_PER_REQUEST --region ap-southeast-1
```

6. Kết quả:

- Kết quả trên AWS CloudShell:

![](/images/5-workshop/3.dynamodb/003-dynamoDB.png?width=90pc)

- Kết quả trên giao diện:

![Create Tables](/images/5-workshop/3.dynamodb/004-dynamoDB.png?width=90pc)

7. Xác nhận Tables đã tạo

Sau khi tạo xong, kiểm tra danh sách tables:

```bash
aws dynamodb list-tables --region ap-southeast-1
```

Kết quả sẽ hiển thị 12 tables:

```json
{
    "TableNames": [
        "DanhGia",
        "DatLichKH",
        "KieuDang",
        "LoaiPhuKien",
        "MauXe",
        "NguyenLieuXe",
        "PhuKien",
        "Slider",
        "ThuongHieu",
        "TinTuc",
        "User",
        "XeOto"
    ]
}
```

Bạn đã hoàn thành việc tạo DynamoDB tables! Tiếp theo sẽ import dữ liệu mẫu.

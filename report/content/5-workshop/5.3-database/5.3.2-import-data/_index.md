---
title : "Import dữ liệu mẫu"
date :  "2024-01-01" 
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---

### Import dữ liệu mẫu vào DynamoDB

Sau khi tạo tables ở [bước 5.3.1 Tạo tables](../5.3.1-create-tables/), tiếp tục import dữ liệu mẫu bằng AWS CloudShell.

#### Import dữ liệu

1. Để ghi dữ liệu, sử dụng lệnh **`put-item`**

2. Tiếp tục trên AWS CloudShell, gõ lệnh:

```bash
aws dynamodb put-item --table-name DanhGia --item '{"id":{"S":"DG1760497475409"},"tenKH":{"S":"Văn B"},"hinhAnh":{"S":"1760497475406-65792375.jpg"},"noiDung":{"S":"xe lướt đầy đủ thông tin, kiểm tra kĩ càng, giá cả hợp lý rõ ràng"},"ngayTao":{"S":"2025-10-15T03:04:35.409Z"}}' --region ap-southeast-1

aws dynamodb put-item --table-name DanhGia --item '{"id":{"S":"DG1760497598834"},"tenKH":{"S":"Văn A"},"hinhAnh":{"S":"1760497598832-300428767.jpg"},"noiDung":{"S":"xe lướt báo đúng tình trạng, cho lái thử để biết xe có vấn đề gì phát sinh không"},"ngayTao":{"S":"2025-10-15T03:06:38.834Z"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD001"},"tenKieuDang":{"S":"Sedan"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD002"},"tenKieuDang":{"S":"SUV"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD003"},"tenKieuDang":{"S":"Hatchback"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD004"},"tenKieuDang":{"S":"Coupe"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD005"},"tenKieuDang":{"S":"Convertible"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD006"},"tenKieuDang":{"S":"Pickup"}}' --region ap-southeast-1

aws dynamodb put-item --table-name KieuDang --item '{"id":{"S":"KD007"},"tenKieuDang":{"S":"Minivan"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK001"},"tenLoai":{"S":"Camera"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK002"},"tenLoai":{"S":"Cảm biến"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK003"},"tenLoai":{"S":"Loa Bluetooth"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK004"},"tenLoai":{"S":"Gương cầu lồi"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK005"},"tenLoai":{"S":"Sạc điện thoại"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK006"},"tenLoai":{"S":"Máy bơm lốp"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK007"},"tenLoai":{"S":"Bọc ghế"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK008"},"tenLoai":{"S":"Thảm lót sàn"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK009"},"tenLoai":{"S":"Tẩu sạc đa năng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK010"},"tenLoai":{"S":"Hệ thống định vị GPS"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK011"},"tenLoai":{"S":"Đèn LED"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK012"},"tenLoai":{"S":"Kính chắn nắng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK013"},"tenLoai":{"S":"Túi khí bổ sung"}}' --region ap-southeast-1

aws dynamodb put-item --table-name LoaiPhuKien --item '{"id":{"S":"LPK999"},"tenLoai":{"S":"Khác"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX001"},"tenMau":{"S":"Đen"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX002"},"tenMau":{"S":"Trắng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX003"},"tenMau":{"S":"Xám"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX004"},"tenMau":{"S":"Bạc"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX005"},"tenMau":{"S":"Đỏ"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX006"},"tenMau":{"S":"Xanh dương"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX007"},"tenMau":{"S":"Vàng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX008"},"tenMau":{"S":"Nâu"}}' --region ap-southeast-1

aws dynamodb put-item --table-name MauXe --item '{"id":{"S":"MX1760493365226"},"tenMau":{"S":"Hồng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name NguyenLieuXe --item '{"id":{"S":"NL001"},"tenNguyenLieu":{"S":"Xăng"}}' --region ap-southeast-1

aws dynamodb put-item --table-name NguyenLieuXe --item '{"id":{"S":"NL002"},"tenNguyenLieu":{"S":"Dầu Diesel"}}' --region ap-southeast-1

aws dynamodb put-item --table-name NguyenLieuXe --item '{"id":{"S":"NL003"},"tenNguyenLieu":{"S":"Điện"}}' --region ap-southeast-1

aws dynamodb put-item --table-name NguyenLieuXe --item '{"id":{"S":"NL004"},"tenNguyenLieu":{"S":"Hybrid"}}' --region ap-southeast-1

aws dynamodb put-item --table-name Slider --item '{"id":{"S":"SL001"},"tieuDe":{"S":"Slide 1"},"hinhAnh":{"S":"/Public/images/SlideShow/img5.png"}}' --region ap-southeast-1

aws dynamodb put-item --table-name Slider --item '{"id":{"S":"SL002"},"tieuDe":{"S":"Slide 2"},"hinhAnh":{"S":"/Public/images/SlideShow/img2.png"}}' --region ap-southeast-1

aws dynamodb put-item --table-name Slider --item '{"id":{"S":"SL003"},"tieuDe":{"S":"Slide 3"},"hinhAnh":{"S":"/Public/images/SlideShow/img3.jpg"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE001"},"TenTH":{"S":"Toyota"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE002"},"TenTH":{"S":"Honda"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE003"},"TenTH":{"S":"Ford"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE004"},"TenTH":{"S":"Hyundai"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE005"},"TenTH":{"S":"Kia"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE006"},"TenTH":{"S":"Mazda"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE007"},"TenTH":{"S":"Chevrolet"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE008"},"TenTH":{"S":"BMW"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE009"},"TenTH":{"S":"Mercedes-Benz"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE010"},"TenTH":{"S":"Audi"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE011"},"TenTH":{"S":"Nissan"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE012"},"TenTH":{"S":"Mitsubishi"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE013"},"TenTH":{"S":"Lexus"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE014"},"TenTH":{"S":"Volkswagen"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THXE015"},"TenTH":{"S":"Subaru"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"TH1760488658291"},"TenTH":{"S":"MG"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"TH1760493095566"},"TenTH":{"S":"Porsche"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THKHAC0"},"TenTH":{"S":"Khác"},"idPhanLoaiTH":{"N":"0"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK001"},"TenTH":{"S":"Bosch"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK002"},"TenTH":{"S":"Pioneer"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK003"},"TenTH":{"S":"Bridgestone"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK004"},"TenTH":{"S":"Michelin"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK005"},"TenTH":{"S":"Philips"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK006"},"TenTH":{"S":"Hankook"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK007"},"TenTH":{"S":"Kenwood"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK008"},"TenTH":{"S":"Sony"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK009"},"TenTH":{"S":"Thule"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK010"},"TenTH":{"S":"Yokohama"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK011"},"TenTH":{"S":"Mobil 1"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK012"},"TenTH":{"S":"Castrol"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK013"},"TenTH":{"S":"Denso"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK014"},"TenTH":{"S":"NGK"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"THPK015"},"TenTH":{"S":"Goodyear"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"TH1760491477533"},"TenTH":{"S":"ICAR"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1

aws dynamodb put-item --table-name ThuongHieu --item '{"id":{"S":"TH1760492080519"},"TenTH":{"S":"VIETMAP"},"idPhanLoaiTH":{"N":"1"}}' --region ap-southeast-1
```

3. Kết quả:

![Import Data](/images/5-workshop/3.dynamodb/005-dynamoDB.png?width=90pc)

#### Xác nhận dữ liệu

Kiểm tra số lượng items trong mỗi table:

```bash
aws dynamodb scan --table-name DanhGia --select COUNT --region ap-southeast-1
aws dynamodb scan --table-name KieuDang --select COUNT --region ap-southeast-1
aws dynamodb scan --table-name MauXe --select COUNT --region ap-southeast-1
```

#### Import dữ liệu phức tạp (PhuKien, TinTuc, XeOto, User)

Các tables PhuKien, TinTuc, XeOto, User có dữ liệu phức tạp. Sử dụng script backup/restore có sẵn:

1. Clone project và chạy restore script:

```bash
# Clone project
git clone https://github.com/khaizr0/RAB_Data.git
cd RAB_Data

# Tạo package.json
echo '{}' > package.json

# Cài đặt dependencies
npm install @aws-sdk/client-dynamodb @aws-sdk/lib-dynamodb

# Chạy restore script
node restoreData.js backup-2025-10-15T03-13-22-686Z.json
```

3. Kết quả:

```
Importing PhuKien...
✓ Imported 2 items to PhuKien
Importing TinTuc...
✓ Imported 2 items to TinTuc
Importing XeOto...
✓ Imported 2 items to XeOto

Import completed!
```

![Import Complex Data](/images/5-workshop/3.dynamodb/006-dynamoDB.png?width=90pc)

Database đã sẵn sàng cho ứng dụng!

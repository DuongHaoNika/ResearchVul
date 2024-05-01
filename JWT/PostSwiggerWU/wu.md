## JWT authentication bypass via unverified signature

Sau khi đăng nhập wiener, ta thử url /admin -> bị chặn

![Alt text](image.png)

Ta thấy sự xuất hiện của JWT, thử sửa sub thành `administrator`

![Alt text](image-1.png)

Giờ ta đã bypass authentication, giờ chỉ cần xóa user carlos là được.

![Alt text](image-2.png)

## JWT authentication bypass via flawed signature verification

Tương tự như trên:

Ở lần này, ta sửa alg: none 

![Alt text](image-3.png)

Như vậy đã bypass

## Lab: JWT authentication bypass via weak signing key

Lab này ta sẽ brute-force để tìm signing key, lỗi này do key yếu hoặc cop code về không sửa key

![Alt text](image-4.png)

-> Thử bypass bằng cách trên nhưng không được.

Giờ ta brute-force tìm key, chú ý ở đây thuật toán là HS256

![Alt text](image-5.png)

![Alt text](image-6.png)

Ở đây ta đã tìm dc key: `secret1`

![](image-7.png)

Ta điền key rồi generate ra signature

![Alt text](image-8.png)

Paste vào cookie rồi chạy

![Alt text](image-9.png)

Vậy đã bypass được.
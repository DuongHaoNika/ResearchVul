## Reflected XSS into HTML context with nothing encoded

Ta chỉ cần chèn `<script>alert("cc")</script>` vào ô search

![alt text](image.png)

## Stored XSS into HTML context with nothing encoded

Ta nhận thấy form này nhận input từ người dùng, sau đó sẽ lưu dữ liệu -> database

![alt text](image-1.png)

![alt text](image-2.png)

## DOM XSS in `document.write` sink using source `location.search`

Ta nhận thấy khi ta submit thì 1 hình ảnh được tạo ra.

![alt text](image-3.png)

Ta chỉ cần đóng thẻ img lại, và định nghĩa 1 thẻ mới.

![alt text](image-4.png)

## DOM XSS in `innerHTML` sink using source `location.search`

Khi ta submit thì nó sẽ nối chuỗi mà mình nhập với innerHTML

![alt text](image-5.png)


## Lab: SSRF with blacklist-based input filter

Khi nhấn check stock -> api như hình

![alt text](image.png)

ta thử chèn localhost xemm sao

![alt text](image-1.png)

-> Ăn black list

![alt text](image-2.png)

đổi sang 127.0.0.1 hay 127.1 vẫn ăn black list

thử urlencode 'a' -> %2561

![alt text](image-3.png)

![alt text](image-4.png)

Done!

![alt text](image-5.png)



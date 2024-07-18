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

## DOM XSS in jQuery anchor href attribute sink using location.search source

We go to submit feedback page 

![alt text](image-7.png)

![alt text](image-6.png)


## Lab: DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded

Khi ta submit thì thấy chuỗi ta nhập được đặt trong ng-app
![alt text](image-8.png)

`{{$on.constructor('alert(1)')()}}`

![alt text](image-9.png)

`$on` is event handler function in Angular JS. The $ sign just represents it is a function. `$on.constructor` is constructor function when invoked with parameters executes it's argument passed as a string. Thus passed with argument it is `$on.constructor('alert(1)')` and to denote constructor is a function "()" is added to look like: $on.constructor('alert(1)')(). This is similar to the following snippet in javascript:

```js
function (){
   alert(1);
}
```
## Lab: Reflected DOM XSS

![alt text](image-10.png)

![alt text](image-11.png)

=> escape `"`

![alt text](image-13.png)

![alt text](image-12.png)

## Lab: Reflected XSS into HTML context with most tags and attributes blocked

When I try:

![alt text](image-14.png)

Server send: 
![alt text](image-15.png)

Tag: body is not blocked!

![alt text](image-16.png)

![alt text](image-17.png)




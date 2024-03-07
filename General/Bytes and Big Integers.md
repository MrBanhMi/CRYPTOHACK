# Bài 4 Bytes and Big Integers
![image](https://hackmd.io/_uploads/r1vKjr4_p.png)

- Mô tả: challenge này sẽ giúp chúng ta hiểu rõ hơn về hai câu lệnh `bytes_to_long()` và `long_to_bytes()`.
- Hướng dẫn: Sau khi khai báo Mô-đun PyCryptodome bằng câu lệnh `from Crypto.Util.number import *` thì ta sử dụng câu lệnh `bytes_to_long()` để chuyển các số nguyên sang ký tự.
- Đoạn code như sau:
  ```python
  from Crypto.Util.number import *
  data = 11515195063862318899931685488813747395775516287289682636499965282714637259206269
  flag = long_to_bytes(data).decode()
  print(flag)
  #sau khi chạy đoạn code thì ta được output: crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
  ```
 - Vậy Cờ của challenge này là: **crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}**
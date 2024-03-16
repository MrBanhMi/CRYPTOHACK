# Extended GCD
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/cd2885c8-53b5-465e-9eb4-834045692a01)

- Challenge nãy sẽ giới thiệu chúng ta về **Extended GCD** và cách để tính EGCD.
- **Extended GCD** hay còn gọi là **thuật toán euclid mở rộng**. EGCD là một cách vô cùng hiệu quả để tính hai số nguyên **u** và **v** sao cho:
    - **a * u + b * v = gcd(a,b)**
    - Hai số **u** và **v** này sẽ có ứng dụng rất lớn trong mã hóa **RSA** mà ta sẽ học sau này.
- **Thuật toán euclid mở rộng** hoạt động như sau:
    - Ta biết rằng **a % b = r**, nghĩa là **a = b * q + r** với **q** là **"the quotient"** tức phần thương và **r** là **"the remainder"** phần dư.
        - ví dụ: 13 = 5 * 2 + 3 (q = 2 và r = 3)
    - Bây giờ để tính EGCD, ta tính GCD trước bằng cách **lặp lại các phép chia lấy dư** cho đến khi nào **phần dư bằng 0**. Như ví dụ sau đây:
        - Tìm EGCD của 81 và 57.
        ```
        Đầu tiên ta tìm GCD
        81 = 1(57) + 24
        57 = 2(24) + 9
        24 = 2(9) + 6
        9 = 1(6) + 3
        6 = 2(3) + 0.
        #vậy GCD của 81 và 57 sẽ là 3.
        ```
        - **GCD(a, b) = r** thì tồn tại hai số nguyên **u** và **v** sao cho ***u * (a) + v * (b) = r***. Bây giờ ta sẽ tìm hai số **u** và **v** sao cho **u * 81 + v * 57 = 3**.
        - Ta làm như sau:
            - Bắt đầu bằng dòng **gần dòng cuối cùng nhất** là dòng **9 = 1(6) + 3** ta viết lại thành **3 = 9 - 1(6)**.
            - Sử dụng dòng ở trên dòng vừa rồi là dòng **24 = 2(9) + 6**, ta viết lại thành **6 = 24 - 2(9)**.
            - Sau đó ta thế dòng **6 = 24 - 2(9)** vào dòng **3 = 9 - 1(6)** sẽ được **3 = 9 - 1(24 - 2(9))** rút gọn được **3 = 3(9) - 1(24)**.
            - Ta lại tiếp tục sử dụng dòng ở trên là **57 = 2(24) + 9**, viết lại thành **9 = 57 - 2(24)**.
            - Sau đó thế **9 = 57 - 2(24)** vào lại phương trình **3 = 3(9) - 1(24)** sẽ được **3 = 3(57) - 7(24)**.
            - Cuối cùng ta sử dụng dòng trên cùng là **81 = 1(57) + 24** viết thành **24 = 81 - 1(57)** rồi đem thế vào **3 = 3(57) - 7(24)** ta được **3 = 10(57) -7(81)**.
            - Vậy ta đã tìm được hai số **u** và **v** thỏa phương trình **u * 81 + v * 57 = 3** là **u = -7** và **v = 10**.
    - Ta có thêm một tính chất khá quan trọng sau này đó là nếu **GCD(a, b) = 1** thì **u * a + b * v = 1** hay **u * a = 1 + (-v) * b** (chuyển vế) được viết thành **u * a ≡ 1 (mod b)** tức **u** chính là **phần tử nghịch đảo** của **a** trong mod b. Nghĩa là tồn tại một số **u** nào đó sao cho khi nó nhân cho **a** và đem đi mod b sẽ được **1**.
            - Ví dụ: tìm **x** sao cho **5 * x ≡ 1 (mod 3)**, tức là tìm phần tử nghịch đảo của 5 trong mod 3 hay tìm x để cho khi x nhân 5 mod 3 sẽ được 1. Ta sẽ tìm được x = 2 là phần tử nghịch đảo của 5 trong mod 3 vì 2 * 5 = 10; 10 % 3 = 1.
- Hướng dẫn giải challenge:
    - Ta code như sau:
    ```python
    def extended_euclidean_algorithm(a, b):
        if b == 0:
            return a, 1, 0
        else:
            gcd, x, y = extended_euclidean_algorithm(b, a % b)
            return gcd, y, x - (a // b) * y

    # Thay đổi giá trị của a và b tại đây
    a = 26513
    b = 32321

    gcd_result, x, y = extended_euclidean_algorithm(a, b)

    print(f"Ước chung lớn nhất của {a} và {b} là {gcd_result}")
    print(f"Các số u và v sao cho a*u + b*v = GCD(a, b) là ({x}, {y})")
    
    #Ước chung lớn nhất của 26513 và 32321 là 1
    #Các số x và y sao cho ax + by = GCD(a, b) là (10245, -8404)
    ```
- ***Vậy Flag của challenge này là -8404***

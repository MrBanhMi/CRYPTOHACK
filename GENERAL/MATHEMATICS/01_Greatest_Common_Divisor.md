# Greatest Common Divisor
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/073579b1-73b2-4b64-9b29-3e4681092493)

- Mô tả: Challenge này sẽ giới thiệu cho chúng ta **The Greatest Common Divisor** (GCD) là gì và cách dùng **thuật toán Euclid** để tìm GCD.
- **The Greatest Common Divisor** (GCD) tiếng việt là **Ước chung lớn nhất**. Ước chung lớn nhất là số nguyên dương lớn nhất là ước số chung của các số đó. Ví dụ, ước chung lớn nhất của 6 và 15 là 3, kí hiệu GCD(6, 15) = 3.
- Hai số **a** và **b** được gọi là **số nguyên tố cùng nhau** nếu có GCD(a, b) = 1.
- Để tính GCD thì ta có nhiều cách nhưng bây giờ ta sẽ sử dụng **thuật toán euclid** để tính GCD.
- **Thuật toán euclid** hoạt động như sau: cho hai số nguyên **a** và **b** với a > b. Ta lấy a % b được r. Sau đó ta lấy b % r được r1. Rồi lấy r % r1 được r2. Ta thực hiện như thế đến khi nào r(n) % r(n+1) = 0 thì dừng lại. Lúc này GCD của a và b sẽ là r(n+1).
- Ví dụ: Yêu cầu tính **GCD(17, 11)**. Ta lấy 17 % 11 được 6, tiếp tục lấy 11 % 6 được 5, sau đó lấy 6 % 5 được 1. Cuối cùng lấy **5 % 1** được 0. Vì phần dư cuối cùng là 0 nên ta sẽ lấy 1 làm ước chung lớn nhất.
- Đoạn code để tính GCD ở ví dụ trên:
    ```python
    a = 17
    b = 11
    def gcd(a, b):
        while b != 0:
            a, b = b, a % b #gán lại a bằng b và b sẽ được gán bằng phần dư
        return a
    print(gcd(a, b))
    #Kết quả sẽ là 1
    ```
- Hướng dẫn giải:
    - Sử dụng đoạn code ở trên để tính:
    ```python
    a = 66528
    b = 52920
    def gcd(a, b):
        while b != 0:
            a, b = b, a % b
        return a
    print(gcd(a, b))
    #kết quả sẽ là 1512
    ```
- ***Vậy Flag của challenge này là 1512***

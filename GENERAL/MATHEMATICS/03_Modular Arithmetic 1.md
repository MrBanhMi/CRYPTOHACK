# Modular Arithmetic 1
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/6edc6638-23fe-4433-b9d9-7fdbe6dec0e5)

- **Mô tả**: challenge này sẽ giới thiệu chúng ta khái niệm  **congruent modulo**.
- **congruent modulo** nghĩa là đồng dư modulo, hai số nguyên được gọi là đồng dư modulo m **nếu a ≡ b (mod m)**. Tức là **a** và **b** sẽ **cùng** một **số dư** khi **chia cho m**.
- Ví dụ: 9 ≡ 1 mod 4 nghĩa là 9 % 4 và 1 % 4 đều có chung kết quả là 1.
- Nói cách khác thì **a ≡ b (mod m)** cùng có nghĩa là **a % m = b**.
- Nếu **a ≡ 0 (mod m)** thì có nghĩa **a chia hết cho m**, kí hiệu là **m | a**.
- Hướng dẫn giải challenge:
    - Challenge yêu cầu chúng ta tìm x và y, flag sẽ là số nhỏ hơn.
    - Sử dụng tính chất **a ≡ b (mod m)** =>** a % m = b**
    - Ta sẽ code như sau:
       ```python
          print(8146798528947%17)
          print(11%6)
          #Chạy chương trình và thấy 4 < 5
       ```
  - **_Vậy flag của challenge này là 4_**.

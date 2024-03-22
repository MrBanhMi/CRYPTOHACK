# Modular Arithmetic 2
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/ea9d42ea-e9d8-4d59-b62f-286313859d14)

- **Mô tả**: Challenge này giới thiệu cho chúng ta về **phần tử nghịch đảo** và **định lí Fermat nhỏ**.
- Trong miền **Fp** giới hạn, là tập hợp của **các số nguyên {0,1,...,p-1}**, với **phép cộng** và **phép nhân** thì ta có một **phần tử nghịch đảo b** với một phần tử **a** nào đó sao cho **a + b = 0** và **a * b = 1**.
- Để nói rõ hơn thì mình xin giải thích như sau: **phần tử nghịch đảo** của phép nhân là một số **b** nào đó khi mà **nhân với a** rồi đem kết quả **chia lấy dư** cho **p** thì được kết quả là **1**.

   ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/2b82a23e-17e5-447f-8814-ef8aca297f56)

- **Định lý nhỏ Fermat nhỏ** khẳng định rằng nếu **p** là một **số nguyên tố**, thì với mọi số nguyên **a** bất kì, **a ^ p - a** sẽ **chia hết cho p**. Kí hiệu như sau: **a ^ p ≡ a (mod p)**.
- Ta có thể viết Định lý nhỏ Fermat nhỏ thành: **a ^ (p-1) ≡ 1 (mod p)**.
- Ví dụ với a = 4, p = 5 => 4 ^ (5-1) - 1 = 255 ≡ (mod 5).
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/d39a14e5-d7ee-47e2-acf2-ae92314a3c04)
- Hướng dẫn giải challenge:
  - Đề cho một số nguyên tố **p = 65537** và một số vô cùng lớn là **273246787654^65536**. Bây giờ yêu cầu tính 273246787654^65536 mod p.
  - Ta sẽ sử dụng công thức vừa học ở trên: **a ^ (p-1) ≡ 1 (mod p)**
  - Vì số mũ là **p - 1** thõa mãn công thức nên kết quả sẽ là **273246787654^65536 ≡ 1 (mod 65537)**
- _**Vậy Flag của challenge này là 1**_.
- Các nguồn sử dụng:
  - https://vi.wikipedia.org/wiki/Định_lý_nhỏ_Fermat
  - https://viblo.asia/p/so-hoc-dong-du-phan-1-dong-du-thuc-va-nghich-dao-modulo-Az45b0aqZxY

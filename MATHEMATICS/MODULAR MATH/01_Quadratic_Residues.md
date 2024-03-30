# Bài 1 Quadratic Residues
![Screenshot 2024-03-07 214409](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/41f7f2c1-85d4-4551-a96a-f3a87d671c7e)

- Mô tả: Challenge này sẽ giúp ta hiểu được **Quadratic Residues** và **Quadratic Non-Residues** là gì, cách kiểm tra một số nguyên **a** có phải là Quadratic Residues hay không?
- Quadratic Residues tiếng việt nghĩa là **thặng dư bậc hai**, còn Quadratic Non-Residues là **bất thặng dư bậc 2**; Một số **a** được gọi là **thặng dư bậc hai mod p** nếu tồn tại số nguyên **x** sao cho **x^2 ≡ a (mod p)** với 0 < x < p và p là số nguyên tố.
- Ví dụ: 8^2 ≡ **6** (mod 29) nghĩa là: "6 là thặng dư bậc 2 mod 29" vì trong khoảng (1, 29) số 8 khi bình phương là 64, số 64 khi mod cho 29 sẽ bằng 6.
- Ví dụ: x^2 ≡ **3** (mod 5) nghĩa là: "3 là bất thặng dư bậc 2 mod 5" vì trong khoảng (1, 5) ta không thể tìm được số nào bình phương lên mà mod cho 5 bằng 3.
- Tính Chất: x^2 ≡ a (mod p) => **a ≡ x^2 (mod p)**.

  ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/79a6a128-768c-4b77-9b8e-ab2f12ef6509)

- Hướng dẫn cách giải:
  - Đề bài cho sẵn 1 số nguyên tố p = 29 và một list có 3 số gồm 2 số Quadratic Non-Residues và 1 số Quadratic Residues, yêu cầu của đề là tìm chính xác số Quadratic Residues và tính căn bậc hai của số Quadratic Residues đó, kết quả sẽ là số nhỏ hơn.
  - Để tìm được **a** thì ta dùng tính chất **a ≡ x^2 (mod p)**, sau đó ta cho **x** chạy trong khoảng (1, 29) để tìm ra **a**.
  - Đoạn code sẽ như sau:

    ```python
    p = 29
    ints = [14, 6, 11]
    for i in range(1, 29):
      if i**2 % 29 in ints: 
        print(i, i**2 % 29)
    #đoạn code trên sẽ cho kết quả là hai cặp số (8, 6) và (21, 6), ta sẽ lấy kết quả là 8. 
    ```
- _**Vậy Flag của challenge này là: 8**_




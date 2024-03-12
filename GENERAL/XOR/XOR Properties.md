#  XOR Properties
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/91fc0aee-bf6b-4772-a74f-f22c12c301a9)

- Mô tả: Challenge này sẽ giới thiệu chúng ta về các tính chất của Xor bao gồm Commutative (giao hoán), Associative (kết hợp), Identity (đồng nhất) và Self-Inverse (nghịch đảo).
- Xor có những tính chất sau:
    - Commutative: A ⊕ B = B ⊕ A
    - Associative: A ⊕ (B ⊕ C) = (A ⊕ B) ⊕ C
    - Identity: A ⊕ 0 = A
    - Self-Inverse: A ⊕ A = 0
- Hướng dẫn giải:
    - Chú ý vào hàng cuối cùng vì nó có chứa flag, như ta thấy thì hàng cuối là kết quả của **flag ⊕ key1 ⊕ key3 ⊕ key2**.
    - Để giải ra được flag thì ta sử dụng tính chất thứ 4 là **Self-Inverse**. Ta sẽ xor hàng cuối cùng với key1, key3 và key2 vì khi ta xor key1, key2, key3 với chính nó thì chúng sẽ triệt tiêu và còn lại giá trị **0**, mà khi xor một đoạn mã với 0 thì ta sẽ được chính nó nên ta sẽ còn lại flag.
    - Lưu ý: đoạn mã đề cho là mã hex nên ta phải chuyển thành kiểu số nguyên thì mới xor được với nhau.
    - Đoạn code như sau:
    ```python
    from Crypto.Util.number import*
    def xor(a, b):
        return a^b
    k1=int('a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313',16)
    k2k1=int('37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e',16)
    k3k2=int('c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1',16)
    fk1k3k2=int('04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf',16)
    flag = xor(xor(fk1k3k2, k3k2), k1)
    flag1 = long_to_bytes(flag).decode()
    #ta dùng hàm long_to_bytes để chuyển kiểu số nguyên ở tên thành kiểu bytes rồi dùng hàm .decode() để chuyển thành kiểu ASCII.
    print(flag1)
    #ta sẽ được output là: crypto{x0r_i5_ass0c1at1v3}
    ```
- ***Vậy Flag của challenge này là: crypto{x0r_i5_ass0c1at1v3}***

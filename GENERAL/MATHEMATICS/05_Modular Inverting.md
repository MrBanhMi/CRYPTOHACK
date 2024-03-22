# Modular Inverting
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/161efcf7-d85f-4b29-a59b-6f2692dc130a)

- **Mô tả**: challenge này sẽ cho ta một vài ví dụ và đào sâu vào **phần tử nghịch đảo modulo**.
- Chúng ta biết rằng trong trường **Fp**, là tập hợp các số nguyên **{0,1,2,..p-1}**. Với mọi phần tử **g** của miền **Fp**, **tồn tại** một số nguyên **d** duy nhất nào đó sao cho **g * d ≡ 1 (mod p)**. 
- Nói cách khác thì **d** là **phần tử nghịch đảo** của **g**. Hai số này khi **nhân cho nhau** và **chia cho p** thì sẽ **dư 1**. Hai số nguyên **g** & **d** này phải nằm trong trường Fp nghĩa là chúng nó phải nằm trong đoạn **[0, p-1]**.
- **Chú ý quan trọng**: chỉ khi **GCD(a, p) = 1**, tức **a** và **p** là hai số nguyên tố cùng nhau thì mới **tồn tại phần tử nghịch đảo** của **a**.
  - Ví dụ: **x * 6 ≡ 1 mod 10**, ở đây **p = 10** và **a = 6** không nguyên tố cùng nhau, bạn sẽ không thể tìm được số x nào mà nhân với 6 rồi đem chia cho 10 mà ra 1 cả.
  - Nhưng nếu ta thay **p** bằng số nguyên tố **11** thì kết quả sẽ khác: **x * 6 ≡ 1 mod 11** thì kết quả là **x = 2**. Vì 2 * 6 bằng 12, và 12 % 11 = 1.
- Hướng dẫn giải challenge:
  - Đề bài như sau: **3 * d ≡ 1 mod 1**, tìm d.
  - Tức là đang kêu ta tìm phần tử nghịch đảo của **3** trong **modulo 13**.
  - Mình thì hiểu như này: là tìm số nguyên **d** nào đó nằm trong đoạn **[0,12]** sao cho **nhân với 3** rồi **chia cho 13** còn **dư 1**. Ở đây **p = 13** là **số nguyên tố**, chắc chắn trong trường Fp sẽ tồn tại số **d** nào đó là phần tử nghịch đảo của **3**.
  - Nếu như bạn đã hiểu được những gì mình giải thích ở trên thì chúng ta sẽ vào python code như sau:
    ```python
    for i in range(13): #Tìm trong trường p
        if (i*3) % 13 == 1: #Phần tử nào nhân 3 mà chia cho 13 còn dư 1
            print(i) #Thì in nó ra, kết quả là 9
        #Vì 9 * 3 ≡ 1 (mod 13)
    ```
    Hoặc bạn có thể sử dụng hàm **Pow()**, chúng ta sẽ nói qua hàm này ở chương RSA, nhưng nếu ta biết sớm hơn thì vẫn tốt. **Pow(a, b, c)** nghĩa là tính **(a ^ b) % c**. Code như sau:

    ```python
    print(pow(3, -1, 13))
    # Kết quả là 9
    ```
- **_Vậy Flag của challenge này là 9_**.

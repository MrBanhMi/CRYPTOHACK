# Legendre Symbol
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/ddec4988-0246-41e5-a7a5-1d2e722f0da9)
- **Mô tả**: Challenge này giới thiệu cho chúng ta về **Ký Hiệu Legendre**, **công thức**, **tính chất** của nó và cách tìm **Căn bậc hai** của một thặng dư bậc hai (Quadratic Residues) khi số p quá lớn.
- **Ký Hiệu Legendre** như sau: $\left ( \frac{a}p{} \right )$

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/d50b011b-f882-475d-a8b4-13d5cb8bcad7)


- Ta có $\left ( \frac{a}p{} \right )$  với **p** là một số nguyên tố lẻ và **a** là một số nguyên dương.
- Ta có tính chất sau

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/d3a84c0f-e380-44c8-b505-d3017a5683bc)

- Nghĩa là ta có thể dựa vào tính chất trên để kiểm tra một số nguyên dương **a** nào đó có phải thặng dư bậc hai modulo p hay không:
  - Nếu $\left ( \frac{a}p{} \right ) = 1$ thì số a đích thị là thặng dư bậc 2 modulo p, ngược lại nếu $\left ( \frac{a}p{} \right ) = -1$ thì a không phải thặng dư bậc 2 modulo p, còn nếu $\left ( \frac{a}p{} \right ) = 0$ thì a ≡ 0 (mod p) hay a chia hết cho p.
- Công thức tổng quát của Legendre như sau:

  ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/396a7a28-ee1f-4610-9b7c-5c9e0676808b)

- Trong python thì nó như thế này:
  ```python
  pow(a, (p-1)//2, p)
  ```
- Ví dụ: kiểm tra xem trong các số **a** sau, số nào là **thặng dư bậc hai** của **p**:
  - a = [6, 12, 21, 28] & p = 29
  - Hướng dẫn: Sử dụng công thức

     ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/7ca40372-ba7f-4701-94d5-d5737c4ed87a)

  - Ta sẽ vào python code như sau:
    ```python
    a = [6, 12, 21, 28] 
    p = 29
    for i in a:
        if pow(i, (p-1)//2, p) == 1: #tức là nếu số nào có (a/p) = 1 thì số đó sẽ là thặng dư bậc hai
            print(i)
    #kết quả sẽ là 6 và 28
    ```
- Quay trở lại bài toán, challenge này cho ta 10 số nguyên dương và 1 số nguyên tố có độ dài 1024 bit (dài tầm 300 số), yêu cầu tìm trong 10 số nguyên dương số nào là thặng dư bậc hai và tính chính xác căn bậc hai của giá trị thặng dư bậc hai đó. Flag sẽ là giá trị của căn bậc hai.
- Challenge này giống challenge trước ở chỗ là nó kêu ta tìm căn bậc hai của thặng dư bậc hai trong modulo p. Nhưng bài toán này khó hơn ở chỗ là số của bài này rất lớn.
- Đầu tiên ta xử lý 10 số nguyên kia trước, để tìm được số nào là thặng dư bậc hai trong list ints kia thì ta code như sau:
    ```python
    p = 101524035174539890485408575671085261788758965189060164484385690801466167356667036677932998889725476582421738788500738738503134356158197247473850273565349249573867251280253564698939768700489401960767007716413932851838937641880157263936985954881657889497583485535527613578457628399173971810541670838543309159139
    
    ints = [...] #các bạn tự thêm vào nha
    
    for i in ints:
        if pow(i, (p-1)//2, p) == 1:
            print(i)
    
    #output sẽ là 85256449776780591202928235662805033201684571648990042997557084658000067050672130152734911919581661523957075992761662315262685030115255938352540032297113615687815976039390537716707854569980516690246592112936796917504034711418465442893323439490171095447109457355598873230115172636184525449905022174536414781771
    ```
- Vậy ta đã tìm được thặng dư bậc hai modulo p, giờ ta sẽ đi tìm căn bậc hai của nó.
- Ở bài trước, ta dùng vòng lặp for trong range(p) để tìm căn bậc hai của a tức số x nào mà khi bình phương đem mod cho p được a. Còn bài này, số p đề cho là cực kỳ lớn
  ```python
  p = 101524035174539890485408575671085261788758965189060164484385690801466167356667036677932998889725476582421738788500738738503134356158197247473850273565349249573867251280253564698939768700489401960767007716413932851838937641880157263936985954881657889497583485535527613578457628399173971810541670838543309159139
  #với số p này mà dùng vòng lặp for chắc tới mùa quýt =))
  ```
- Đề cho ta một dữ kiện khá quan trọng như sau: **p ≡ 3 (mod 4)** tức **p = 4k + 3** với k là một số nguyên nào đó. Ta sẽ sử dụng dữ kiện này sau.
-  Ta đặt thặng dư bậc hai vừa tìm được là a, ta sẽ biến đổi như sau:
    ```
      1 = a ^ (p - 1)/2 mod p 
      #ta nhân hai vế cho a được
      a = a * a ^ (p - 1)/2 mod p
      a = a ^ ( (p - 1)/2 + 1 ) mod p
      a = a ^ (p + 1)/2 mod p
      #giờ để tính căn bậc hai của a thì ta chỉ việc căn bậc hai hai vế
      sqrt(a) = a ^ ( (p + 1)/2 * 1/2 ) mod p
    => sqrt(a) = a ^ (p + 1)/4 mod p
    ```
 - Ta có được công thức tính căn bậc hai của thặng dư bậc hai như sau:

   ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/a3442b26-5ba5-41ba-a244-74f8a9415a23)
- Chú ý: Công thức trên chỉ áp dụng khi **p ≡ 3 (mod 4)** tức **p = 4k + 3** vì khi ta thế p = 4k + 3 vào a ^ (p + 1)/4 thì ta được a ^ (k + 1) với số mũ nguyên. Nhưng ở bài sau ta sẽ gặp **p ≡ 1 (mod 4)**. Khi thế vào ta được a ^ (k + 1/2) với số mũ không nguyên, thế là ta không thể tìm được căn bậc hai của a. Tóm lại công thức trên chỉ áp dụng khi **p ≡ 3 (mod 4)**.
- Để kết thúc challenge này thì chúng ta code như sau:

    ```python
    p = 101524035174539890485408575671085261788758965189060164484385690801466167356667036677932998889725476582421738788500738738503134356158197247473850273565349249573867251280253564698939768700489401960767007716413932851838937641880157263936985954881657889497583485535527613578457628399173971810541670838543309159139
    
    a = 85256449776780591202928235662805033201684571648990042997557084658000067050672130152734911919581661523957075992761662315262685030115255938352540032297113615687815976039390537716707854569980516690246592112936796917504034711418465442893323439490171095447109457355598873230115172636184525449905022174536414781771
    
    print(pow(a, (p + 1)//4, p))
    
    #ouput sẽ là 93291799125366706806545638475797430512104976066103610269938025709952247020061090804870186195285998727680200979853848718589126765742550855954805290253592144209552123062161458584575060939481368210688629862036958857604707468372384278049741369153506182660264876115428251983455344219194133033177700490981696141526
    ```
- **_Vậy flag của challenge này là: 93291799125366706806545638475797430512104976066103610269938025709952247020061090804870186195285998727680200979853848718589126765742550855954805290253592144209552123062161458584575060939481368210688629862036958857604707468372384278049741369153506182660264876115428251983455344219194133033177700490981696141526_**





  
 



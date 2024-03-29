# Legendre Symbol
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/ddec4988-0246-41e5-a7a5-1d2e722f0da9)
- **Mô tả**: Challenge này giới thiệu cho chúng ta về **Ký Hiệu Legendre**, **công thức**, **tính chất** của nó và cách tìm **Căn bậc hai** của một thặng dư bậc hai (Quadratic Residues) khi số p quá lớn.
- **Ký Hiệu Legendre** như sau: $\left ( \frac{a}p{} \right )$
- $\left ( \frac{a}p{} \right )$  với **p** là một số nguyên tố lẻ và **a** là một số nguyên dương.
- Ta có tính chất sau

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/715d6bb3-79e7-47f3-b0d1-0912b864ce95)
- Nghĩa là ta có thể dựa vào tính chất trên để kiểm tra một số nguyên dương **a** nào đó có phải thặng dư bậc hai modulo p hay không:
  - Nếu $\left ( \frac{a}p{} \right ) = 1$ thì số a đích thị là thặng dư bậc 2 modulo p, ngược lại nếu $\left ( \frac{a}p{} \right ) = -1$ thì a không phải thặng dư bậc 2 modulo p, còn nếu $\left ( \frac{a}p{} \right ) = 0$ thì a ≡ 0 (mod p) hay a chia hết cho p.
- Công thức tổng quát của Legendre như sau:

  ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/2292fae8-75b0-4275-baff-5b5f30e9eae1)
- Trong python thì nó như thế này:
  ```python
  pow(a, (p-1)//2, p)
  ```
- Ví dụ: kiểm tra xem trong các số **a** sau, số nào là **thặng dư bậc hai** của **p**:
  - a = [6, 12, 21, 28] & p = 29
  - Hướng dẫn: Sử dụng công thức

     ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/fc839773-94b6-4920-91dd-038000332f32)
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
- Ở bài trước, ta dùng vòng lặp for trong range(p) để tìm số x nào mà khi bình phương đem mod cho p được a. Còn bài này, số p đề cho là cực kỳ lớn
  ```python
  p = 101524035174539890485408575671085261788758965189060164484385690801466167356667036677932998889725476582421738788500738738503134356158197247473850273565349249573867251280253564698939768700489401960767007716413932851838937641880157263936985954881657889497583485535527613578457628399173971810541670838543309159139
  #với số p này mà dùng vòng lặp for chắc tới mùa quýt =))
  ```
- Đầu tiên ta xử lý 10 số nguyên kia trước
- Đề cho ta một dữ kiện khá quan trọng như sau: **p ≡ 3 (mod 4)** tức **p = 4k + 3** với k là một số nguyên nào đó, ta sẽ sử dụng dữ kiện này sau.

  
 



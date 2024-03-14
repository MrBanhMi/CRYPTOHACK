# You either know, XOR you don't
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/a906057f-e919-400e-9bdf-dc88596b329c)

- Mô tả: Challenge này xor flag với key nào đó và yêu cầu ta đi tìm flag, nó sẽ giúp chúng ta hiểu rõ hơn về xor và dùng xor thành thạo hơn.
    - Challenge này sẽ phức tạp hơn challenge trước, điểm chung ở đây là nó xor flag với một key nào đó, khác ở chỗ ở challenge trước thì key này là 1 bit bất kì, còn ở challenge này key bị giấu nhẹm đi.
    -  May mắn là đề có gợi ý "Nhớ cái format của flag sẽ giúp chúng ta giải challenge này"
- Mình sẽ giới thiệu một hàm cực mạnh là hàm xor() của pwn tool, từ giờ ta không cần phải mệt mỏi tách từng phần tử rồi xor nữa mà ta chỉ cần khai báo rồi dùng thôi.
    - Hướng dẫn sử dụng trước khi dùng: 
        - Khai báo: `from pwn import xor`
        - Ví dụ: 
        ```python
        from pwn import xor
        print(xor(b'hao', b'kcsc'))
        print(xor(50, 60))
        #kết quả là: b'\x03\x02\x1c\x0b' và b'\x0e' đều là kiểu bytes
        ```
        - Lưu ý: hàm xor() chỉ có thể xor 2 kiểu dữ liệu là kiểu bytes hoặc integer với nhau, nên kết quả của cuộc tình trên sẽ là kiểu dữ liệu bytes.
- Hướng dẫn cách giải:
    - Vì đề gợi ý là hãy nhớ format của flag nên ta sẽ **thử** xor dữ kiện đề cho với từ **"crypto{"**.
        
        ```python
        #Ta sẽ sử dụng hàm xor để xor nhanh hơn, chú ý là phải đổi về kiểu bytes trước khi xor
        
        from pwn import xor

        data = bytes.fromhex('0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104')

        hint = b'crypto{'

        test = xor(hint, data)
        
        print(test)
        #output là b'myXORke+y_Q\x0bHOMe$~seG8bGURN\x04DFWg)a|\x1dTM!an\x7f'
        ```
    - Kết quả vô cùng bất ngờ, nhìn vào output ta đoán rằng **key** của challenge này sẽ là **b'myXORkey**.
    - Để kết thúc challenge thì ta sẽ xor dữ kiện của đề với key mà ta vừa kiếm được, đoạn code sẽ như sau:
        ```python
        from pwn import xor

        data = bytes.fromhex('0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104')

        key = b'myXORkey'

        flag = xor(key, data)

        print(flag)
        
        #output sẽ là: b'crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}'
        
- ***Vậy flag của challenge này sẽ là: crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}***

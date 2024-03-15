# QnA
- Có thể XOR những trong trường hợp nào?
  - Xor 2 dãy **bit** với nhau: đây là trường hợp đơn giản nhất, bạn chỉ cần dùng kí hiệu "^" để xor chúng. Chú ý là 2 dãy bit trên có thể khác độ dài nhau.
      - Ví dụ:
        ```python
        text = 0b10110
        key = 0b1011111
        print(text^key)
        #kết quả sẽ là 73
        ```
  - Xor 2 kiểu dữ liệu **int** với nhau: Ta code tương tự như trên. Và 2 dữ liệu có thể khác chiều dài nhau.
      - Ví dụ:
        ```python
          text = 124
          key = 1111
          print(text^key)
          #kết quả sẽ là 1067
          ```
          
  - Xor kiểu dữ liệu **int** và kiểu dữ liệu **bin**. Ta vẫn có thể tiếp tục dùng kí hiệu **"^"** để xor.
      - Ví dụ:
        ```python
        text = 124
        key = 0b1111
        print(text^key)
        #kết quả sẽ là 115
        ```
  - Xor kiểu dữ liệu **string** với **binary** hoặc **integer**: Bây giờ thì ta không thể dùng kí hiệu **"^"** để xor nguyên chuỗi với giá trị bin/int được mà phải tách từng phần tử của chuỗi ra, chuyển thành kiểu integer hoặc binary rồi xor với dữ liệu kiểu binary/integer.
      - Ví dụ:
        ```python
        text = "hao"
        key = 0b1011
        for i in text:
            print(chr(ord(i) ^ key), end="")
        #kết quả sẽ là cjd
        ```
  - Xor hai dữ liệu kiểu **String** với nhau. Đây sẽ là kiểu xor khó nhằn nhất. Để giải thích cách xor thì mình sẽ giải thích như sau: 
      - **Trường hợp 1**: hai dãy string có cùng chiều dài. Máy tính sẽ xor như sau: nó lấy kí tự đầu tiên của chuỗi một rồi xor với kí tự đầu tiên của chuỗi hai, rồi kí tự thứ hai của chuỗi một xor với kí tự thứ hai của chuỗi hai và làm như thế cho đến hết.
      - **Trường hợp 2**: hai dãy string khác chiều dài nhau. Ví dụ chuỗi thứ nhất dài hơn chuỗi thứ hai, máy tính sẽ xor như sau: nó lấy kí tự đầu tiên của chuỗi một xor với kí tự đầu tiên của chuỗi thứ hai, tiếp tục xor theo thứ tự cho đến kí tự cuối cùng của chuỗi hai, khi này chuỗi một vẫn **còn** kí tự nhưng chuỗi hai đã **hết** kí tự. Lúc này máy sẽ **lặp chuỗi hai** lại tự đầu rồi xor kí tự đầu tiên của chuỗi hai với kí tự tiếp theo của chuỗi một. Điều đó lý giải tại sao ở bài **Favourite byte** ta không xor nguyên output với một bit mà phải xor từng ký tự của output với 1 bit.
    - Ví dụ: Nếu chuỗi 1 là "hello" và chuỗi hai là "ab", thì quá trình XOR sẽ như sau:
        ```python=
        "h" XOR "a"
        "e" XOR "b"
        "l" XOR "a"
        "l" XOR "b"
        "o" XOR "a"
        ```
    - Đoạn code để XOR hai kiểu string cùng hoặc khác độ dài:
        ```python
        # Khởi tạo hàm xor
        def encrypt(ptxt, key):
            ctxt = b''
            for i in range(len(ptxt)):
                a = ptxt[i]
                b = key[i % len(key)]
                ctxt += bytes([a ^ b])
            return ctxt

        # Đoạn văn bản thông điệp cần mã hóa
        plaintext = b"kcsc2024"

        # Khóa sử dụng để mã hóa
        key = b"2005"

        # Mã hóa đoạn văn bản thông điệp
        ciphertext = encrypt(plaintext, key)

        print("Plaintext:", plaintext)
        print("Key:", key)
        print("Ciphertext:", ciphertext)
        ```
    - Kết luận: dùng hàm xor() của pwn cho khỏe =))
- Làm sao để xor hai hình ảnh?
        
          

# QnA
- Có thể Xor những trong trường hợp nào?
  - Xor 2 dãy bit với nhau: đây là trường hợp đơn giản nhất, bạn chỉ cần dùng kí hiệu "^" để xor chúng. Chú ý là 2 dãy bit trên có thể khác độ dài nhau.
      - Ví dụ:
        ```python
        text = 0b10110
        key = 0b1011111
        print(text^key)
        #kết quả sẽ là 73
        ```
  - Xor 2 kiểu dữ liệu int với nhau: Ta code tương tự như trên. Và 2 dữ liệu có thể khác chiều dài nhau
      - Ví dụ:
        ```python
          text = 124
          key = 1111
          print(text^key)
          #kết quả sẽ là 1067
          ```
          
  - Xor kiểu dữ liệu int và kiểu dữ liệu bin. Ta vẫn có thể tiếp tục dùng kí hiệu "^" để xor.
      - Ví dụ:
            ```python
            text = 124
            key = 0b1111
            print(text^key)
            #kết quả sẽ là 115
            ```
    - Xor hai dữ liệu kiểu String với nhau
        
          

# Bài 2 Hex
![image](https://hackmd.io/_uploads/rJT0Q4Vda.png)
- Mô tả: Challenge này sẽ giúp ta hiểu thêm về mã Hex, một mã mà chúng ta sẽ thường xuyên gặp phải trong Cryptohacking và cách chuyển đổi từ mã Hex sang Bytes.
- Hướng dẫn: Ta sẽ làm quen với hàm **bytes.fromhex()**, một hàm với khả năng chuyển đổi từ mã hex sang mã Bytes.
- Đoạn code sẽ như sau:
    ```python
    hex_string = "63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d"
    decoded_bytes = bytes.fromhex(hex_string)
    print(decoded_bytes)
    #chạy code sẽ được output là: b'crypto{You_will_be_working_with_hex_strings_a_lot}'
    ```
- Vậy Cờ của challenge này là:
**crypto{You_will_be_working_with_hex_strings_a_lot}**
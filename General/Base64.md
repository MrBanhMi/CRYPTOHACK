# Bài 3 Base64
![image](https://hackmd.io/_uploads/SJ3-F44_6.png)
- Mô tả: Challenge này giúp ta làm quen với mã Base64 và cách chuyển đổi từ mã Hex sang mã Base64.
- Hướng dẫn: sau khi khai báo Mô-đun Base64 bằng lệnh `import base64` ta có thể sử dụng câu lệnh `base64.b64encode()` để chuyển đổi từ mã Bytes sang Base64.
- Chú ý: Vì đoạn mã mà Challenge đưa ra là mã Hex nên ta phải chuyển từ mã Hex sang mã Bytes bằng câu lệnh `bytes.fromhex()`
- Đoạn Code như sau:
    ```python
    import base64
    hex_string = "72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf"
  decoded_bytes = bytes.fromhex(hex_string)
  base64_encoded = base64.b64encode(decoded_bytes)
  print(base64_encoded)
  #sau khi chạy thì ta được output: b'crypto/Base+64+Encoding+is+Web+Safe/'
    ```
- Vậy Cờ của challenge này là: **crypto/Base+64+Encoding+is+Web+Safe/**
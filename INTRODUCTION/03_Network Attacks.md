# Network Attacks
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/68f62c3b-ce2d-4eca-ab93-6fc55d23793d)

- Một vài challenge sẽ yêu cầu ta kết nối với chủ sever để giải được challenge.
- Những cách thức kết nối này có thể được thực hiện bằng thư viện `pwntools`. Nhưng mà thư viện này không có sẵn nên ta phải cài nó bằng câu lệnh `pip install pwntools`. Để hiểu rõ hơn thì hãy truy cập vào đường dẫn này https://cryptohack.org/faq/#install.
- Hướng dẫn giải:
  - Challenge yêu cầu ta kết nối đến sever `socket.cryptohack.org`với port là `11112`, ta sẽ nhập như sau: `nc socket.cryptohack.org 11112`
  - Kết quả như sau:

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/461b03f9-9dd6-4ae0-b218-fe2f2cd54252)
  - Vì đề yêu cầu hãy gửi một chuỗi `JSON` cho nó với key là `buy` và giá trị là `flag`, mình sẽ trả lời nó như sau:

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/47b126b1-d22d-4ecf-9cc1-f7ba5d008030)
  - Kết quả nó sẽ trả lại cho mình giá trị của flag:

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/9e4cdd6b-5449-4954-8b12-7ad8ef8f12f5)
- Ở trên là cách làm thông dụng nhất, sau đây là cách giải khác của challenge này khi đề đã cho ta source code:
  - Tải file mà đề đã cho là:

    ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/e3f51753-cd70-49b3-9ed3-b84fd59bdfeb)
  - Ta sẽ được đoạn code sau:
    ```python
    #!/usr/bin/env python3
    
    from pwn import * # pip install pwntools
    import json
    
    HOST = "socket.cryptohack.org"
    PORT = 11112
    
    r = remote(HOST, PORT)
    
    
    def json_recv():
        line = r.readline()
        return json.loads(line.decode())
    
    def json_send(hsh):
        request = json.dumps(hsh).encode()
        r.sendline(request)
    
    
    print(r.readline())
    print(r.readline())
    print(r.readline())
    print(r.readline())
    
    request = {
        "buy": "clothes"
    }
    json_send(request)
    
    response = json_recv()
    
    print(response)
    ```
    - Ta sẽ chú ý ở phần **request**

      ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/42747dd3-4709-4760-824c-5a3e07e361d7)
    - Vì đề đã nói là `Send a JSON object with the key buy and value flag` nên ta sẽ sửa **value** từ `clothes` thành `flag`:

      ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/c4d02829-e998-4de3-a2bc-a38fa7defb80)
    - Sau khi chạy thì ta được kết quả
   
      ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/14531df7-0bd5-4f57-a42c-0dc767cf14a2)
- **_Vậy flag của challenge này là crypto{sh0pp1ng_f0r_fl4g5}_**.





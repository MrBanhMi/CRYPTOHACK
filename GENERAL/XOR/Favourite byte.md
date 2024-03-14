# Favourite byte
- Challenge này sẽ giúp ta ứng dụng các kiến thức đã học vào việc giải challenge.
- Đề bài: Đề đã xor **flag** với một **bit** nào đó mà ta không biết, ta chỉ biết rằng bit đó nằm trong khoảng [0, 255]. Sau khi xor thì ta được kết quả:
    - **73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d**
- Hướng dẫn giải: Ta sẽ dùng vòng lặp **for** để xor **output** với **256 bit**, nếu có một bit chính xác thì output sẽ là flag:
- Chú ý: 
    - Challenge này ta sẽ xor hai dữ liệu không có cùng độ dài bit
    - Nên chú ý rằng: xor một bit với output ở trên sẽ cho kết quả khác hoàn toàn với việc xor từng phần tử của output với 1 bit. Tức là để hoàn thành bài trên thì ta phải xor từng phần tử của output trên với 1 bit chứ không phải xor toàn bộ output với 1 bit.
    - Vì vậy: phải tìm cách để tách output thành từng phần tử riêng lẻ rồi xor với 1 bit.
- Hướng dẫn:
    - Ta sẽ khai báo một **list**, rồi thêm từng phần tử của ouput vào list. Sau đó ta dùng vòng lặp **for** cho i đi qua từng phần tử của list. Với mỗi phần tử của list ta sẽ xor với 1 bit, thử qua toàn bộ 256 bit khi nào ra flag thì dừng.
    - Đoạn code sẽ như sau:
        ```python=
        output = "73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d"
        bytes_value = bytes.fromhex(output)
        data = []
        for i in bytes_value:
            data.append(i)
        for i in range(256):
            a = ""
            for j in data:
                a = a + chr(j ^ i)
        #vì có tới 256 giá trị nên ta phải tìm flag thông qua format của flag là: crypto{    
            if "crypto{" in a:
                print(a)
        #output sẽ là: crypto{0x10_15_my_f4v0ur173_by7e}
        ```
- ***Vậy Flag của challenge này là: crypto{0x10_15_my_f4v0ur173_by7e}***
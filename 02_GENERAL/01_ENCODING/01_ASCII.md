# Bài 1 ASCII
![image](https://hackmd.io/_uploads/SJtAkVN_6.png)
- Mô tả: Challenge này giúp ta hiểu thêm về một mã là mã **ASCII** và cách chuyển đổi từ kiểu **số nguyên** sang kiểu **ASCII**.
- Hướng dẫn: chúng ta có thể sử dụng hàm **chr()** để chuyển đổi từ kiểu **số nguyên** sang kiểu **ASCII** tương ứng và sử dụng hàm **ord()** để làm ngược lại.
- Lưu ý: Hàm **chr()** và hàm **ord()** chỉ có thể mã hóa duy nhất **một** ký tự, nên ta không thể để **toàn bộ** list vào hàm chr() hoặc ord() mà phải dùng vòng lặp **for** để chuyển đổi từng phần tử trong list sang **ASCII**.
- Đoạn Code sẽ như sau:
```python
integer_array = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
for i in integer_array:
    ascii_characters = chr(i)
    print(ascii_characters, end='') 
#chạy code sẽ được ouput là: crypto{ASCII_pr1nt4bl3}
```
- Vậy cờ của challenge này là: crypto{ASCII_pr1nt4bl3}

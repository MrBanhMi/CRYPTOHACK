# Xor Starter
![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/bf4cb0eb-f80e-4751-8706-fa4748bc0a9c)
- Mô tả: Challenge này sẽ giới thiệu cho chúng ta về **Xor**, rằng Xor là gì, và cách để Xor hai kiểu dữ liệu.
- Xor hay đầy đủ là **Exclusive Or**, tức là cách nó hoạt động ngược lại với hàm Or. Khi ta thực hiện phép Xor hai dãy bit **cùng độ dài**, nó sẽ trả về giá trị là 0 (tức là sai) nếu hai bit đang xét giống nhau và sẽ trả về 1 (đúng) nếu hai bit đang xét khác nhau.
- ![image](https://github.com/MrBanhMi/CRYPTOHACK/assets/155632468/48436d9d-911f-465f-bde7-d2e269b1843b)
- Người ta thường ký hiệu Xor bằng ký tự **⊕**, nhưng trong khi lập trình thì ta sẽ dùng ký tự **"^"** này.
- Ví dụ: hãy tính 1101 ^ 0100. Đầu tiên phải kiểm tra chiều dài của hai dãy bit, nếu chúng bằng nhau thì ta sẽ bắt đầu xor. Ta sẽ xor từng bit của 2 dãy bit trên, đầu tiên là xor 1 và 0 sẽ được 1, xor 1 và 1 được 0, xor 0 và 0 được 0 và cuối cùng xor 1 và 0 sẽ được 1. Vậy kết quả là: 1101 ^ 0100 = 1001
- Khi lập trình, ta có thể xor hai kiểu dữ liệu Integer với nhau, Ví dụ:
 ```python
  print(13^9)
  #output sẽ là 4
 ```
- Hướng dẫn cách giải:
  - Đề bài cho ta một chuỗi là **"label"** và số nguyên **13**, đề bài yêu cầu ta hãy xor **từng ký tự** của chuỗi **label** với số **13** và ta sẽ được chuỗi mới, gắn chuỗi đó vào **crypto{...}** và ta sẽ có được Flag.
  - Vì đề bài yêu cầu phải Xor từng ký tự với số 13 nên ta phải biến đổi từng ký tự đó về kiểu dữ liệu Integer thì mới Xor được với số 13.
  - Ta sẽ sử dụng hai hàm đó là hàm **chr()** và hàm **ord()**, hàm **chr()** sẽ có tác dụng biến một kiểu dữ liệu Integer sang kiểu dữ liệu ASCII tương ứng, còn hàm **ord()** sẽ thực hiện ngược lại.
  - Ta sẽ dùng vòng lặp **For**, cho **i** chạy qua từng ký tự của **"label"**, rồi dùng hàm **ord()** để chuyển ký tự đó sang Integer, sau đó Xor số 13 với kiểu Integer ta vừa mới chuyển đổi, rồi ta dùng hàm chr() để đổi kiểu dữ liệu ta vừa mới Xor được sang lại ASCII.
  - Vd: khi i = "l", hàm ord() sẽ chuyển chữ "l" thành số 118, sau đó xor số 108 với số 13 sẽ được số 97, cuối cùng ta dùng hàm chr() chuyển từ số 97 thành chữ "a"
  - Đoạn Code sẽ như sau:
    ```python
    string = "label"
    for i in string:
      int_value = ord(i)
      new_int = int_value ^ 13
      new_string = chr(new_int)
      print(new_string, end="")
    #output sẽ là aloha
    ```
 - Vậy Flag của challenge này là: crypto{aloha}


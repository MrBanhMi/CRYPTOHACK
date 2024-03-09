# Bài 1 Quadratic Residues
- Mô tả: Challenge này sẽ giúp ta hiểu được **Quadratic Residues** và **Quadratic Non-Residues** là gì, cách kiểm tra một số nguyên **x** có phải là Quadratic Residues hay không?
- Quadratic Residues tiếng việt nghĩa là **thặng dư bậc hai**; một số **a** được gọi là **thặng dư bậc hai mod p** nếu tồn tại số nguyên **x** sao cho **x^2 ≡ a (mod p)**.
- Ví dụ: 8^2 ≡ 6 (mod 29) nghĩa là: "6 là thặng dư bậc 2 mod 29" vì trong khoảng (1,29) số 8 khi bình phương = 64 khi mod cho 29 sẽ bằng 6.
- ví dụ: x^2 ≡ 3 (mod 5) nghĩa là: "3 là bất thặng dư bậc 2 mod 5" vì trong khoảng từ 1 đến 5 ta không thể tìm được số nào bình phương lên mà mod cho 5 bằng 3.
- Tính Chất: x^2 ≡ a (mod p) <=> **a ≡ x^2 (mod p)**.
- Hướng dẫn:

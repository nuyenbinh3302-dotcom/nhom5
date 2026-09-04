
## 📋 Mục lục

1. [Chú thích (Comments)](#1-chú-thích-comments)
2. [Nhập/Xuất dữ liệu (Input/Output)](#2-nhậpxuất-dữ-liệu-inputoutput)
3. [Chuyển đổi kiểu dữ liệu (Type Casting)](#3-chuyển-đổi-kiểu-dữ-liệu-type-casting)


## 1. Chú thích (Comments)

* **Trong C (C89):** Chỉ hỗ trợ chú thích nhiều dòng bằng cú pháp `/* ... */`.
* **Trong C++:** Bổ sung chú thích dòng đơn bằng `//` (C99 sau này cũng đã cập nhật cú pháp này).

```c
/* Trong C: Chú thích nhiều dòng
   hoặc một dòng đều phải dùng cặp dấu này */
```

```cpp
// Trong C++: Có thể chú thích một dòng nhanh chóng bằng dấu //
/* Hoặc dùng chú thích nhiều dòng
   như trong C */
```

---

## 2. Nhập/Xuất dữ liệu (Input/Output)

* **Trong C:** Sử dụng hàm `printf()` và `scanf()` từ thư viện `<stdio.h>`. Lập trình viên phải nhớ và chỉ định chính xác mã định dạng (format specifier) như `%d`, `%f`, `%s`.
* **Trong C++:** Sử dụng các đối tượng luồng `cin` (input stream) và `cout` (output stream) từ thư viện `<iostream>`. C++ tự động nhận diện kiểu dữ liệu của biến.

```c
// C
#include <stdio.h>

int age;
printf("Nhập tuổi: ");
scanf("%d", &age);
printf("Tuổi của bạn là: %d\n", age);
```

```cpp
// C++
#include <iostream>
using namespace std;

int age;
cout << "Nhập tuổi: ";
cin >> age;
cout << "Tuổi của bạn là: " << age << endl;
```

---

## 3. Chuyển đổi kiểu dữ liệu (Type Casting)

* **Trong C:** Dùng C-style casting: `(kiểu_dữ_liệu)giá_trị`. Cách này thiếu an toàn vì có thể ép chuyển đổi các kiểu dữ liệu không liên quan mà không báo lỗi lúc biên dịch.
* **Trong C++:** Cung cấp 4 toán tử ép kiểu chuyên biệt để kiểm soát chặt chẽ:
  1. `static_cast`: Ép kiểu an toàn giữa các kiểu dữ liệu có liên quan (lúc biên dịch).
  2. `dynamic_cast`: Dùng cho ép kiểu an toàn trong cây thừa kế khi có đa hình (lúc thực thi/runtime).
  3. `const_cast`: Loại bỏ tính hằng (`const`) của biến.
  4. `reinterpret_cast`: Ép kiểu con trỏ mức độ thấp (nguy hiểm, tùy thuộc phần cứng).

```c
// C
double pi = 3.14159;
int int_pi = (int)pi; // C-style cast
```

```cpp
// C++
double pi = 3.14159;
int int_pi = static_cast<int>(pi); // Rõ ràng và an toàn hơn
```

---


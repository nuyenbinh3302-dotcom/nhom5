# PHÂN CÔNG NHIỆM VỤ NHÓM 5:

1-3: Nguyễn Huyền Trang

4-6: Nguyễn Nam Khánh

7-9: Phạm Bách Minh

10-12: Vũ Đức Bình

Tổng Hợp ND: Lục Bình Nguyên




---

## Mục lục

1. [Chú thích (Comments)](#1-chú-thích-comments)
2. [Nhập/Xuất dữ liệu (Input/Output)](#2-nhậpxuất-dữ-liệu-inputoutput)
3. [Chuyển đổi kiểu dữ liệu (Type Casting)](#3-chuyển-đổi-kiểu-dữ-liệu-type-casting)
4. [Vị trí khai báo biến (Variable Declarations)](#4-vị-trí-khai-báo-biến-variable-declarations)
5. [Kiểu cấu trúc (`struct`)](#5-kiểu-cấu-trúc-struct)
6. [Toán tử phạm vi (Scope Resolution Operator `::`)](#6-toán-tử-phạm-vi-scope-resolution-operator-)
7. [Cấp phát và giải phóng bộ nhớ (`new` / `delete`)](#7-cấp-phát-và-giải-phóng-bộ-nhớ-new--delete)
8. [Hàm Inline (Inline Functions)](#8-hàm-inline-inline-functions)
9. [Tham số giá trị mặc định (Default Arguments)](#9-tham-số-giá-trị-mặc-định-default-arguments)
10. [Biến tham chiếu (Reference Variables)](#10-biến-tham-chiếu-reference-variables)
11. [Nạp chồng hàm (Function Overloading)](#11-nạp-chồng-hàm-function-overloading)
12. [Nạp chồng toán tử (Operator Overloading)](#12-nạp-chồng-toán-tử-operator-overloading)
13. [Bảng tổng hợp nhanh](#bảng-tổng-hợp-nhanh)

---

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

## 4. Vị trí khai báo biến (Variable Declarations)

* **Trong C (C89):** Tất cả biến phải được khai báo ở **ngay đầu khối lệnh** (block `{}`) trước khi thực hiện bất kỳ câu lệnh nào khác.
* **Trong C++:** Có thể khai báo biến ở **bất kỳ vị trí nào** trong chương trình, miễn là trước khi biến đó được sử dụng.

```c
// C (C89)
void func() {
    int i; // Bắt buộc khai báo ở đầu khối
    int sum = 0;
    
    for (i = 0; i < 10; i++) {
        sum += i;
    }
}
```

```cpp
// C++
void func() {
    int sum = 0;
    // Khai báo ngay trong vòng lặp for
    for (int i = 0; i < 10; i++) {
        sum += i;
    }
}
```

---

## 5. Kiểu cấu trúc (`struct`)

* **Trong C:** `struct` chỉ chứa các biến dữ liệu. Khi khai báo biến kiểu `struct`, phải giữ lại từ khóa `struct` (trừ khi dùng `typedef`).
* **Trong C++:** 
  * `struct` có thể chứa cả **phương thức (hàm)**, **constructor**, **destructor** và các từ khóa truy cập (`public`, `private`, `protected`).
  * Không cần từ khóa `struct` khi khai báo biến.

```c
// C
struct Point {
    int x;
    int y;
};

struct Point p1; // Phải có từ khóa struct
```

```cpp
// C++
struct Point {
    int x;
    int y;
    
    // Thêm hàm vào trong struct
    void print() {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};

Point p1; // Khai báo trực tiếp không cần từ khóa struct
p1.print();
```

---

## 6. Toán tử phạm vi (Scope Resolution Operator `::`)

* **Trong C:** Không có toán tử này. Nếu biến cục bộ trùng tên với biến toàn cục, biến toàn cục sẽ bị che khuất và không thể truy cập trong phạm vi cục bộ.
* **Trong C++:** Sử dụng `::` để:
  1. Truy cập biến toàn cục bị che khuất.
  2. Định nghĩa hàm thuộc Lớp (Class) bên ngoài phạm vi khai báo.
  3. Định danh vùng không gian tên (Namespace).

```cpp
#include <iostream>
using namespace std;

int x = 100; // Biến toàn cục

int main() {
    int x = 10; // Biến cục bộ trùng tên
    
    cout << "Biến cục bộ x = " << x << endl;    // In ra 10
    cout << "Biến toàn cục x = " << ::x << endl; // In ra 100 bằng toán tử ::
    return 0;
}
```

---

## 7. Cấp phát và giải phóng bộ nhớ (`new` / `delete`)

* **Trong C:** Sử dụng các hàm thư viện `malloc()`, `calloc()` và `free()` trong `<stdlib.h>`. Cần tính dung lượng bộ nhớ (`sizeof`) và ép kiểu con trỏ. Không tự động gọi Constructor/Destructor.
* **Trong C++:** Sử dụng toán tử `new` và `delete` (hoặc `delete[]` cho mảng).
  * Tự động xác định kích thước và trả về đúng kiểu con trỏ.
  * Tự động gọi **Constructor** khi tạo và **Destructor** khi giải phóng.

```c
// C
int *arr = (int*)malloc(10 * sizeof(int));
free(arr);
```

```cpp
// C++
int *arr = new int[10]; // Cấp phát mảng
delete[] arr;           // Giải phóng mảng
```

---

## 8. Hàm Inline (Inline Functions)

* **Trong C:** Thường sử dụng tiền xử lý `#define` (macro) để thay thế mã nguồn, nhưng dễ gây lỗi logic do không có kiểm tra kiểu dữ liệu và thứ tự thực thi.
* **Trong C++:** Sử dụng từ khóa `inline` trước khai báo hàm. Trình biên dịch sẽ chèn trực tiếp mã hàm vào nơi gọi hàm để tránh chi phí gọi hàm (function call overhead), đồng thời vẫn đảm bảo tính an toàn kiểu dữ liệu.

```c
// C - Dùng Macro
#define SQUARE(x) ((x) * (x))
```

```cpp
// C++ - Dùng inline function
inline int square(int x) {
    return x * x;
}
```

---

## 9. Tham số giá trị mặc định (Default Arguments)

* **Trong C:** Bắt buộc phải truyền đủ tất cả đối số khi gọi hàm.
* **Trong C++:** Cho phép gán giá trị mặc định cho các tham số trong khai báo hàm. Nếu người dùng không truyền giá trị, hàm sẽ sử dụng giá trị mặc định.

```cpp
#include <iostream>
using namespace std;

// Height có giá trị mặc định là 10
void displayBox(int width, int height = 10) {
    cout << "Width: " << width << ", Height: " << height << endl;
}

int main() {
    displayBox(5);     // In ra: Width: 5, Height: 10
    displayBox(5, 20); // In ra: Width: 5, Height: 20
    return 0;
}
```

---

## 10. Biến tham chiếu (Reference Variables)

* **Trong C:** Để thay đổi giá trị của biến ngoài hàm, bắt buộc phải dùng **Con trỏ (Pointers)** với các cú pháp phức tạp `*` và `&`.
* **Trong C++:** Giới thiệu **Biến tham chiếu** (kí hiệu `&`), hoạt động như một bí danh (alias) của biến gốc. Cú pháp truyền tham chiếu gọn gàng và an toàn hơn con trỏ.

```c
// C - Truyền bằng con trỏ
void swapC(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}
```

```cpp
// C++ - Truyền bằng tham chiếu
void swapCPP(int &a, int &b) {
    int temp = a;
    a = b;
    b = temp;
}
```

---

## 11. Nạp chồng hàm (Function Overloading)

* **Trong C:** Mỗi hàm phải có một tên duy nhất. Không thể tạo hai hàm cùng tên ngay cả khi tham số khác nhau.
* **Trong C++:** Cho phép nhiều hàm có **cùng tên**, miễn là chúng khác nhau về **số lượng tham số** hoặc **kiểu dữ liệu tham số**. Trình biên dịch sẽ tự chọn hàm phù hợp.

```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

int add(int a, int b, int c) {
    return a + b + c;
}
```

---

## 12. Nạp chồng toán tử (Operator Overloading)

* **Trong C:** Các toán tử (`+`, `-`, `*`, `==`, ...) chỉ hoạt động trên kiểu dữ liệu nguyên thủy (`int`, `float`, ...).
* **Trong C++:** Cho phép định nghĩa lại cách các toán tử hoạt động đối với các kiểu dữ liệu do người dùng tự định nghĩa (Class / Struct).

```cpp
#include <iostream>
using namespace std;

struct Complex {
    double real, imag;

    // Nạp chồng toán tử +
    Complex operator + (const Complex& other) {
        return {real + other.real, imag + other.imag};
    }
};

int main() {
    Complex c1 = {1.2, 2.3};
    Complex c2 = {3.4, 4.5};
    
    Complex c3 = c1 + c2; // Sử dụng toán tử + tự định nghĩa
    cout << "Kết quả: " << c3.real << " + " << c3.imag << "i" << endl;
    return 0;
}
```

---

## 📊 Bảng tổng hợp nhanh

| Tính năng | Ngôn ngữ C | Ngôn ngữ C++ |
| :--- | :--- | :--- |
| **Chú thích dòng đơn** | Ban đầu không có (thêm từ C99) | Hỗ trợ cú pháp `//` |
| **Nhập / Xuất** | `printf`, `scanf` trong `<stdio.h>` | `cout`, `cin` trong `<iostream>` |
| **Ép kiểu** | Ép kiểu C `(type)val` | `static_cast`, `dynamic_cast`,... |
| **Vị trí khai báo biến** | Đầu khối lệnh (C89) | Bất kỳ vị trí nào |
| **Thành phần trong `struct`** | Chỉ chứa biến dữ liệu | Chứa biến, phương thức, constructor |
| **Toán tử phạm vi `::`** | Không hỗ trợ | Hỗ trợ truy cập phạm vi toàn cục/lớp |
| **Quản lý bộ nhớ** | `malloc()`, `free()` | `new`, `delete` (gọi Constructor/Destructor) |
| **Tối ưu hàm ngắn** | `#define` macro | Từ khóa `inline` |
| **Giá trị mặc định cho tham số** | Không hỗ trợ | Hỗ trợ gán trực tiếp tại khai báo |
| **Biến tham chiếu (`&`)** | Không có (chỉ có con trỏ) | Hỗ trợ biến tham chiếu ( bí danh ) |
| **Nạp chồng hàm (Overloading)** | Không hỗ trợ | Hỗ trợ nạp chồng theo kiểu/số tham số |
| **Nạp chồng toán tử** | Không hỗ trợ | Hỗ trợ định nghĩa lại toán tử cho Class/Struct |

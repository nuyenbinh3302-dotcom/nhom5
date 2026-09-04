
10. [Biến tham chiếu (Reference Variables)](#10-biến-tham-chiếu-reference-variables)
11. [Nạp chồng hàm (Function Overloading)](#11-nạp-chồng-hàm-function-overloading)
12. [Nạp chồng toán tử (Operator Overloading)](#12-nạp-chồng-toán-tử-operator-overloading)

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


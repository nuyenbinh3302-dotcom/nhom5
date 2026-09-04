---

## Mục lục
4. [Vị trí khai báo biến (Variable Declarations)](#4-vị-trí-khai-báo-biến-variable-declarations)
5. [Kiểu cấu trúc (`struct`)](#5-kiểu-cấu-trúc-struct)
6. [Toán tử phạm vi (Scope Resolution Operator `::`)](#6-toán-tử-phạm-vi-scope-resolution-operator-)
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

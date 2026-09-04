 Các Mở Rộng Của C++ So Với C

Tài liệu hướng dẫn và so sánh chi tiết 12 nâng cấp cốt lõi của **C++** so với **C truyền thống**. Các mở rộng này không chỉ giúp viết mã nguồn ngắn gọn, an toàn hơn mà còn đặt nền móng cho phương pháp **Lập trình hướng đối tượng (OOP)**.

---

##  Mục lục

7. [Cấp phát và giải phóng bộ nhớ (`new` / `delete`)](#7-cấp-phát-và-giải-phóng-bộ-nhớ-new--delete)
8. [Hàm Inline (Inline Functions)](#8-hàm-inline-inline-functions)
9. [Tham số giá trị mặc định (Default Arguments)](#9-tham-số-giá-trị-mặc-định-default-arguments)

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


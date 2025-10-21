## 🔹 1️⃣ Không mã hóa (No Encryption)

**Cấu hình:**

* ❌ Không tick “Precompile during publishing” (ở màn hình trước)
* Không mở hộp thoại này

👉 Kết quả:
File `.cs`, `.aspx`, `.cshtml`... vẫn giữ nguyên → ai cũng đọc được source code.

---

## 🔹 2️⃣ Mã hóa **một phần** (Partial Encryption – chỉ mã hóa code-behind)

**Cấu hình trong hình bạn gửi** là **đúng cho trường hợp này** ✅

* ✅ Tick “Precompile during publishing”
* ✅ “Allow precompiled site to be updatable”
* 🔘 “Do not merge” (hoặc “Merge each individual folder output to its own assembly” nếu muốn gọn DLL hơn)

👉 Kết quả:

* Toàn bộ file `.cs` (code-behind) sẽ bị compile thành DLL → **ẩn toàn bộ logic code**
* Các file giao diện `.aspx`, `.ascx`, `.cshtml` vẫn đọc/sửa được
  → Đây là **mã hóa một phần** (Partial Encryption)

---

## 🔹 3️⃣ Mã hóa **toàn phần** (Full Encryption)

**Cấu hình:**

* ✅ Tick “Precompile during publishing”
* ❌ Bỏ tick “Allow precompiled site to be updatable”
* 🔘 Chọn “Merge all outputs to a single assembly” (tùy chọn, nhưng nên chọn để gộp toàn bộ code vào 1 DLL)

👉 Kết quả:

* Cả file `.cs` và `.aspx` đều được compile → chỉ còn DLL, không còn code/markup rõ ràng.
* Khi mở web folder publish, chỉ thấy `.dll` và file cấu hình, **source code hoàn toàn bị ẩn**.

---

## 🔧 Gợi ý thêm:

| Profile name     | Tùy chọn                                | Mức độ mã hóa                |
| ---------------- | --------------------------------------- | ---------------------------- |
| `NoEncrypt`      | Không bật “Precompile”                  | Giữ nguyên code              |
| `PartialEncrypt` | Bật “Precompile” + “Allow updatable”    | Mã hóa `.cs`                 |
| `FullEncrypt`    | Bật “Precompile” + bỏ “Allow updatable” | Mã hóa toàn bộ code + markup |

---
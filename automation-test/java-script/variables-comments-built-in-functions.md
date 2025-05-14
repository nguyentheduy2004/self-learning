## Biến (Variables), Comments, Built-in Functions

### A. Khai báo biến (Variable Declaration)

#### `var` (Variable):
- **Scope**: Phạm vi biến được khai báo bằng `var` là **function scope** hoặc **global scope**, không có **block scope**.
- **Hoisting**: Biến `var` được **hoisted** và khởi tạo với giá trị `undefined`.
- **Redeclaration**: Có thể khai báo lại biến trong cùng một scope.

**Ví dụ**:
```javascript
var x = 10;
var x = 20; // Không lỗi
```
### `let`:

- **Scope**: Có `block scope`.
- **Hoisting**: Được hoisted nhưng nằm trong **Temporal Dead Zone (TDZ)**.
- **Redeclaration**: Không thể khai báo lại trong cùng một scope.

**Ví dụ:**
```javascript
let y = 50;
// let y = 60; // Lỗi: Identifier 'y' has already been declared
```
### `const`:

- **Scope**: Giống `let`, có **block scope**.
- **Hoisting**: Được hoisted nhưng **không thể sử dụng trước khi khai báo**.
- **Reassignment**: **Không thể gán lại** giá trị cho `const`.
- **Initialization**: **Phải gán giá trị ngay khi khai báo**.

**Ví dụ:**
```javascript
const z = 3.14;
// z = 3.14159; // Lỗi: Assignment to constant variable
```
## B. Kiểu dữ liệu cơ bản (Primitive Data Types)

- **`string`**: Chuỗi văn bản.
- **`number`**: Số nguyên và số thực.
- **`boolean`**: Chỉ nhận hai giá trị: `true` hoặc `false`.
- **`null`**: Đại diện cho "vô giá trị" hoặc không có đối tượng.
- **`undefined`**: Biến được khai báo nhưng chưa được gán giá trị.
- **`symbol`**: Kiểu dữ liệu bất biến, thường dùng làm khóa cho các thuộc tính trong đối tượng.
- **`bigint`**: Dùng để biểu diễn các số nguyên rất lớn vượt quá giới hạn của `number`.

**Ví dụ:**
```javascript
console.log(typeof "Hello");  // string
console.log(typeof 123);      // number
```
## C. Chú thích (Comments)

### Single-line comments:
Dùng `//` để viết chú thích một dòng.

```javascript
// Đây là một chú thích
```
### Multi-line comments:
Dùng `/* ... */` để viết chú thích nhiều dòng.

```javascript
/*
  Đây là một chú thích
  trên nhiều dòng.
*/
```
## D. Hàm tích hợp sẵn (Built-in Functions)

### `console.log()`

- **Công dụng**: In giá trị ra console.
- **Ứng dụng**: Dùng để kiểm tra giá trị biến, debug hoặc theo dõi luồng thực thi chương trình.

**Ví dụ:**
```javascript
let name = "Alice";
console.log(name);  // In ra: Alice
```

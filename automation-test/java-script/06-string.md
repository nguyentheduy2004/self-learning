
### String trong JavaScript

1. **Khai Báo và Tạo String**:
   - String có thể được tạo bằng dấu nháy đơn ('...'), dấu nháy kép ("..."), hoặc dấu backticks (`...` - còn gọi là template literals).
   - **Ví dụ**:
     ```javascript
     let singleQuoteStr = 'Đây là một String với nháy đơn.';
     let doubleQuoteStr = "Đây là một String với nháy kép.";
     let name = "Alice";
     let age = 30;
     let templateStr = `Tên tôi là ${name} và tôi ${age} tuổi.
     Đây là dòng thứ hai.`;

     console.log(singleQuoteStr);
     console.log(doubleQuoteStr);
     console.log(templateStr);
     /*
     Output:
     Đây là một String với nháy đơn.
     Đây là một String với nháy kép.
     Tên tôi là Alice và tôi 30 tuổi.
     Đây là dòng thứ hai.
     */
     ```

2. **Ký Tự Escape (Escape Characters)**:
   - Nếu bạn cần sử dụng ký tự nháy trong String, bạn cần "escape" nó bằng dấu gạch chéo ngược (\).
   - **Ví dụ**:
     ```javascript
     let quoteInString = 'She said, "Hello!"'; // OK: nháy kép trong String nháy đơn
     let anotherQuote = "He replied, 'Hi there!'"; // OK: nháy đơn trong String nháy kép
     let escapedQuote = 'It\'s a beautiful day.'; // Escape nháy đơn
     let escapedDouble = "This is a \"quoted\" word."; // Escape nháy kép
     let newLine = "Dòng 1\n Dòng 2"; // : ký tự xuống dòng
     let tabChar = "Cột 1\tCột 2"; // 	: ký tự tab

     console.log(escapedQuote); // Output: It's a beautiful day.
     console.log(newLine);
     /*
     Output:
     Dòng 1
     Dòng 2
     */
     ```

3. **Thuộc Tính và Phương Thức String Phổ Biến**:
   - **length Property**: Trả về độ dài của String.
     ```javascript
     let message = "Hello, World!";
     console.log(message.length); // Output: 13
     let emptyStr = "";
     console.log(emptyStr.length); // Output: 0
     ```
   - **Truy Cập Ký Tự**: Truy cập ký tự trong String bằng `[]` hoặc `charAt(index)`.
     ```javascript
     let text = "JavaScript";
     console.log(text[0]);      // Output: "J"
     console.log(text[4]);      // Output: "S"
     console.log(text.charAt(1)); // Output: "a"
     ```

4. **Thay Đổi Kiểu Chữ**:
   - **toUpperCase()**: Chuyển đổi thành chữ hoa.
   - **toLowerCase()**: Chuyển đổi thành chữ thường.
     ```javascript
     let greeting = "Welcome to My Page";
     console.log(greeting.toUpperCase()); // Output: WELCOME TO MY PAGE
     console.log(greeting.toLowerCase()); // Output: welcome to my page
     ```

5. **Trích Xuất Phần String**:
   - **slice(startIndex, endIndex)**: Trích xuất một phần của String.
     ```javascript
     let str = "Apple, Banana, Kiwi";
     let part1 = str.slice(7, 13); 
     console.log(part1);          // Output: "Banana"
     ```
   - **substring(startIndex, endIndex)**: Giống `slice()` nhưng không chấp nhận chỉ số âm.
     ```javascript
     let strSub = "JavaScript";
     console.log(strSub.substring(0, 4)); // Output: "Java"
     console.log(strSub.substring(4));    // Output: "Script"
     ```

6. **Thay Thế Nội Dung String**:
   - **replace(searchValue, newValue)**: Thay thế lần xuất hiện đầu tiên của `searchValue`.
     ```javascript
     let textToReplace = "Please visit Microsoft! Microsoft is great.";
     let newText = textToReplace.replace("Microsoft", "W3Schools");
     console.log(newText); // Output: "Please visit W3Schools! Microsoft is great."
     ```

7. **Nối String**:
   - **Toán tử +**: Nối các String.
     ```javascript
     let firstName = "John";
     let lastName = "Doe";
     let fullName = firstName + " " + lastName;
     console.log(fullName); // Output: "John Doe"
     ```
   - **concat()**: Nối một hoặc nhiều String vào String hiện tại.
     ```javascript
     let str1 = "Hello";
     let str2 = " ";
     let str3 = "World";
     let combined = str1.concat(str2, str3, "!");
     console.log(combined); // Output: "Hello World!"
     ```

8. **Cắt Bỏ Khoảng Trắng**:
   - **trim()**: Loại bỏ khoảng trắng từ cả hai đầu của String.
     ```javascript
     let paddedText = "   Hello World!   ";
     console.log(`'${paddedText.trim()}'`); // Output: "'Hello World!'"
     ```

9. **Chuyển Đổi String Thành Mảng**:
   - **split(separator)**: Chia một String thành mảng.
     ```javascript
     let csvData = "apple,banana,orange,grape";
     let fruitsArray = csvData.split(",");
     console.log(fruitsArray); // Output: ["apple", "banana", "orange", "grape"]
     ```

10. **Tìm Kiếm và So Sánh String**:
    - **indexOf(searchValue)**: Tìm vị trí xuất hiện đầu tiên của `searchValue`.
      ```javascript
      let mainString = "Hello world, welcome to the world of JavaScript.";
      console.log(mainString.indexOf("world")); // Output: 6
      console.log(mainString.indexOf("Hello")); // Output: 0
      ```
    - **includes(searchValue)**: Kiểm tra String có chứa `searchValue` không.
      ```javascript
      let textForIncludes = "This is a test string.";
      console.log(textForIncludes.includes("test")); // Output: true
      console.log(textForIncludes.includes("hello")); // Output: false
      ```

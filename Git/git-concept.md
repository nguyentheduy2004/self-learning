# **Git là gì**

Git là một hệ thống kiểm soát giúp quản lý mã nguồn trong các dự án phần mềm. Cơ bản, Git bao gồm ba vùng chính:
![](./Image/git-area.png)
### 1. **Working Directory**:
   - Chứa các file mới hoặc file có thay đổi.

### 2. **Staging Area**:
   - Chứa các file đưa vào chuẩn bị commit (để tạo ra các phiên bản).

### 3. **Repository**:
   - Chứa các commits (hay là các phiên bản của mã nguồn).

---

### **Một số khái niệm trong Git**:
- **Repository (Repo)**: Là nơi lưu trữ các file và lịch sử thay đổi của chúng. Có thể là một repo cục bộ (local repository) trên máy tính và một repo từ xa (remote repository) trên dịch vụ như GitHub.
  
- **Commit**: Một snapshot của mã nguồn tại một thời điểm nhất định, chứa thông tin về thay đổi đã thực hiện.

- **Branch**: Một dòng phát triển riêng biệt trong Git, giúp phát triển tính năng mới mà không ảnh hưởng đến nhánh chính (master).

- **Merge**: Hợp nhất hai nhánh lại với nhau.

- **Clone**: Sao chép một repository từ GitHub về máy.

---

### **Mục tiêu của Git**:
- **Theo dõi và quản lý lịch sử các versions**.
- **Giúp làm việc giữa nhiều người**:
   - Phân nhánh để phát triển đồng thời.
   - Đồng bộ mã nguồn giữa các máy tính.

---

### **Các thao tác cơ bản với Git**:

- `git init`: Khởi tạo một repository Git mới.
  
- `git clone <url>`: Sao chép một repository từ xa về máy tính của bạn.
  
- `git status`: Kiểm tra trạng thái của repository (thêm, thay đổi hay xóa file nào).
  
- `git add .`: Thêm tất cả các file vào staging area (khu vực chuẩn bị commit).
  
- `git add <file>`: Thêm file vào staging area (khu vực chuẩn bị commit).
  
- `git commit -m "message"`: Ghi lại các thay đổi vào lịch sử của repo.
  
- `git commit --amend -m "New commit message"`: Sửa commit gần nhất. Không nên sử dụng lệnh này nếu commit đã được push lên remote repository vì nó có thể gây conflict khi đồng bộ với người khác.

---

### **Xem lịch sử commit**:

- `git log`: Xem lịch sử các commit.

- `git log --oneline`: Hiển thị mỗi commit trên một dòng.

- `git log --graph`: Hiển thị biểu đồ nhánh.
![](./Image/kazSy.png)
- `git log --author=<user.name>`: Filter các commit theo tên tác giả.

---

### **Khôi phục thay đổi**:

- `git restore <file_name>`: Khôi phục một file về trạng thái của commit cuối.

- `git restore`: Khôi phục toàn bộ file về trạng thái của commit cuối.

- `git restore --staged <file_name>`: Khôi phục file từ vùng Staging về Working Directory.

---

### **Hủy commit cuối**:

- `git reset HEAD~1`: Hủy bỏ commit nhưng giữ lại các thay đổi trong working directory.

- `git reset --soft HEAD~1`: Chỉ thay đổi HEAD về commit trước và giữ lại các thay đổi trong staging area.

- `git reset --hard HEAD~1`: Không chỉ thay đổi HEAD về commit trước, mà còn loại bỏ tất cả các thay đổi trong working directory và staging area.

---

### **Quản lý nhánh (Branching and Merging)**:

- `git branch <branch_name>`: Tạo một nhánh mới.

- `git checkout <branch>`: Chuyển sang nhánh khác.

- `git checkout -b <branch_name>`: Tạo nhánh mới và chuyển sang nhánh mới.

- `git merge <branch>`: Hợp nhất nhánh vào nhánh hiện tại.

- `git rebase`: Di chuyển hoặc tái cấu trúc các commit, dùng khi muốn tái tạo lịch sử của các nhánh để dễ dàng hợp nhất hơn.

- `git pull <remote_name> <branch_name>`: Tải các thay đổi từ remote repository về máy của bạn.

- `git push`: Đẩy các thay đổi từ local repository lên remote repository.

- `git fetch`: Tải các thay đổi từ remote về mà không áp dụng chúng vào nhánh hiện tại.

---

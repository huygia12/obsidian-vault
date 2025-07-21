---
created: 2024-03-03T22:36
updated: 2024-05-02T14:08
tags:
  - Todo
  - Git
---
## Definition:
- HEAD: con trỏ chỉ đến commit hiện tại.
- Commit cơ sở: commit trước khi thực hiện tách branch, chính là commit chung của 2 hay nhiều branch.

## Config command: 
-  Kiểm tra version hiện tại của git trong máy tính:
```git
git version
```

- Đặt tên username. email cho toàn bộ repository trên máy tính:
```git
git config --global user.name "ten_account"
git config --global user.email "email_address"
```

-  Hiển thị thông tin đã config 
```git
git config --list
```

## Init a repository: 
- Khởi tạo local repository tại thư mục hiện tại.
```git
git init
```

- Link local repository tới remote repository:
```git
git remote add origin <url>
```

## Thao tác với local repository: 
+ Clone remote repository về máy thành 1 folder:
```git
git clone URL <folder-name>
```

- Fetch những thay đổi mới nhất từ remote xuống local:
```git
git fetch
```

- Cập nhật thay đổi của các nhánh khác đồng thời merge vào nhánh hiện tại(= git fetch + git merge):
```git
git pull 
```

## Trình tự thực hiện 1 commit cơ bản:
-  Chuyển file vào Staging area (. nếu muốn stag all file):
```git
git add file
```

- Commit file vào local:
```git
git commit -m "message"
```

- Đẩy toàn bộ thay đổi lên nhánh được chỉ định trên remote:
```git
git push origin branch_name
```

## Một số câu lệnh khác
+ Check trạng thái trong thư mục đang làm việc:
```git
git status
```

- Bỏ file đã thực hiện thay đổi trong working area:
```git
git restore <file-name>
git restore . // Chọn all file
```

- Thay đổi (sửa tên hoặc thêm file) message mới cho commit:
```git
git commit --amend -m "newMessage"
git commit --amend --no-edit // Thêm file mà không thay đổi commit 
```

- Xem những thay đổi giữa các commit với nhau:
```git
git diff <id-commit1> <id-commit2>
```

- Liệt kê hết tất cả các commit trên nhánh hiện tại (thêm option `-<n>` để giới hạn số commit hiển thị):
```git
git log --oneline
```

#### Lưu tạm thời thay đổi hiện tại trong wk theo dạng Stack:
```git
git stash
git stash list // Hiển thị stack
git stash pop // Lấy ra stash ở trên đầu stack
git stash apply <stash-version> // Back version cụ thể 
git stash drop <stash-version> // Drop version đã stash
```

#### Thao tác với branch:
```git
git branch
git branch <branch-name> // Tạo mới q branch lấy bracnh hiện tại làm gốc
git branch -d <branch-name> // Xóa branch, dùng -D nếu muốn xóa cả thay đôi trong wd
git checkout <bracnh-name> // Di chuyen sang 1 bracnh khác
git branch -m <new-name> // Đổi tên branch
```

#### Thực hiện di chuyển HEAD đến 1 commit cụ thể trong lịch sử.
- `--hard`: di chuyển HEAD trỏ đến commit đã chỉ định, đặt lại working directory để trạng thái của bạn trở về trạng thái của commit đã chỉ định. **Các thay đổi chưa được commit sẽ mất.**
- `--soft`: di chuyển HEAD trỏ đến commit đã chỉ định, nhưng không thay đổi working directory.
```git
git reset --hard|soft HEAD -> Di chuyển con trỏ đến commit hiện tại
git reset --hard|soft HEAD~n -> Quay về trước n commit so với HEAD.
```

#### Thực hiện gộp branch:
- Gộp commit theo trình tự thời gian.
- 3 commit được đem ra so sánh là commit cơ sở cuối, commit cuối của branch-1 và branch-2. 
```git
git merge <branch-name> // Gộp branch được chỉ định vào branch hiện tại
```

- Gộp tất cả commit của một nhánh vào thành commit cơ sở của nhánh còn lại, viết lại lịch sử commit. 
- Không thực hiện nếu đã đẩy commit lên remote vì sẽ làm thay đổi lịch sử commit trên nhánh.
- Cần thực hiện checkout ra nhánh cần `rebase` trước,
```git
git rebase <branch-name>
git rebase --continue // Tiếp tục rebase kể cả khi có xung đột
git rebase --abort // Hủy rebase
```

## Lưu ý:  
- Trước khi tách 1 branch để làm việc, chúng ta cần commit main branch cho git biết master branch là gì, nếu không thì sẽ gặp lỗi. 

## Question:
- Làm sao để tạo nhiều PR liên tiếp

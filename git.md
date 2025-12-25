### 1. Git là gì?, Git khác SVN ở điểm nào

Trả lời
```
- Git là hệ thống quản lí phiên bản phân tán (Distributed Version Control System)
- Mỗi developer có full history của repo ở local
- Không phụ thuộc server khi thực hiện commit, xem log, tạo branch
- Git mạnh ở branch rẻ, merge nhanh, làm việc song song tốt

* Git khác SVN ở điểm sau
- Git là phân tán còn SVN là tập chung
- Git branch rất nhẹ còn SVN branch nặng
- Git commit offline, còn SVN phụ thuộc server
- Git merge tốt còn SVN dễ conflict

* Bài toàn thực tế:
Team 10 người, mỗi người làm 1 feature // với nhau

- Git
+ Git tạo branch riêng
+ Merge xong sau khi xử lý
+ Code review sau khi merge
- SVN
+ Phải chờ nhau commit
+ Dễ conflict

* SVN vẫn dùng được nhưng cân môi trương phù hợp
- Phần quyền chi tiết đến từng module
- Xử lý file lớn bảo mật cao
- Hệ thống đang chạy tốt vs SVN chưa cần thay đổi sang Git

```

### 2.Working Tree, Staging Area, Reposiotory là gì

Trả lời

```
* Git có 3 vùng làm việc chính
- Working Tree: File bạn đang thực hiện sửa
- Staging area (Index): File bạn đã thực hiện git add và chuẩn bị commit
- Repository (.git): Nơi lưu trữ commit lại local

* Bài toán thực tế: 
Bạn sửa 3 file: A.kt,B.kt,readme.md
và chỉ muốn commit file A

- Dùng lệnh sau để đưa file A vào staging area: git add A.kt
- Dùng lệnh sau để commit: git commit -m "message commit"
- Chỉ add những file bạn muốn

* Bài toàn thực tế:
Làm sao để commit từng phần của file

- Trong android studio vào phần diff file, nếu đoạn code nào muốn đẩy lên ta tick vào, còn không thì untick nó
- Còn dùng command thì dùng git commit -p tên file, git đi qua từng block thay file của file và hỏi xem mình muốn xử lý nó không, sử dụng y,n,s,e,q để xử lý từng block code
+ y, là đồng ý commit block này
+ n -> không đồng ý
+ s: split => tách block ra nếu có chồng lấn
+ e: edit nếu muốn sửa code gì đó
+ q: quit 

```

### 3.Git fetch và gill pull khác nhau như thế nào?

Trả lời

```
* git featch
- git fetch chỉ tải code về 
- không ảnh hưởng đến branch hiện tại
* git pull
- lấy code về rồi merge luôn vào brach hiện tại hoặc rebase tùy trường hợp

* Bài toàn thực tế:
Bạn đang sửa code, sợ pull về bị conflict code 

- git featch origin => lấy code mới nhất brach về trước
- git log HEAD..origin/develop => xem có code gì mới và quyết định xem nên merge không
- không bao giờ git pull khi có code chưa commit

```
# Hệ Thống Quản Lý Công Việc

Hệ thống quản lý công việc được xây dựng dựa trên Django và React, cho phép quản lý dự án, phân công và theo dõi công việc một cách hiệu quả.

## Công Nghệ Sử Dụng

### Backend
- Python 3.8+
- Django 4.x
- Django REST Framework
- PostgreSQL/SQLite
- Celery (cho xử lý email và thông báo)
- JWT Authentication

### Frontend (Đang phát triển)
- React
- TailwindCSS
- Axios

## Tính Năng Chính

1. Quản lý người dùng và phân quyền:
   - Đăng ký/đăng nhập
   - Phân quyền RBAC (Role Based Access Control)
   - Quản lý nhóm làm việc

2. Quản lý dự án:
   - Tạo/sửa/xóa dự án
   - Phân công người tham gia
   - Theo dõi tiến độ

3. Quản lý công việc:
   - Tạo/cập nhật/xóa task
   - Phân loại độ ưu tiên
   - Workflow trạng thái công việc
   - Gán người thực hiện
   - Comment và trao đổi
   - Upload file đính kèm

4. Dashboard và báo cáo:
   - Thống kê công việc
   - Biểu đồ tiến độ
   - Báo cáo định kỳ

## Cài Đặt Môi Trường Development

1. Clone repository:
   ```bash
   git clone <repository-url>
   cd task-management
   ```

2. Tạo và kích hoạt môi trường ảo:
   ```bash
   python -m venv venv
   # Windows
   .\venv\Scripts\activate
   # Linux/Mac
   source venv/bin/activate
   ```

3. Cài đặt các dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Thiết lập biến môi trường:
   Tạo file `.env` trong thư mục gốc:
   ```
   DEBUG=True
   SECRET_KEY=your-secret-key
   DATABASE_URL=postgres://user:password@localhost:5432/dbname
   EMAIL_HOST_USER=your-email@gmail.com
   EMAIL_HOST_PASSWORD=your-email-password
   ```

5. Thực hiện migrations:
   ```bash
   python manage.py migrate
   ```

6. Tạo superuser:
   ```bash
   python manage.py createsuperuser
   ```

7. Khởi động Redis server (cho Celery):
   ```bash
   redis-server
   ```

8. Khởi động Celery worker:
   ```bash
   celery -A config worker -l info
   ```

9. Khởi động development server:
   ```bash
   python manage.py runserver
   ```

## API Endpoints

### Authentication
- POST `/api/token/` - Lấy access token
- POST `/api/token/refresh/` - Làm mới access token

### Users & Teams
- GET/POST `/api/accounts/users/` - Danh sách và tạo người dùng
- GET/PUT/DELETE `/api/accounts/users/{id}/` - Chi tiết người dùng
- GET/POST `/api/accounts/teams/` - Danh sách và tạo nhóm
- GET/PUT/DELETE `/api/accounts/teams/{id}/` - Chi tiết nhóm

### Projects
- GET/POST `/api/projects/` - Danh sách và tạo dự án
- GET/PUT/DELETE `/api/projects/{id}/` - Chi tiết dự án
- POST `/api/projects/{id}/add_member/` - Thêm thành viên
- POST `/api/projects/{id}/remove_member/` - Xóa thành viên

### Tasks
- GET/POST `/api/tasks/` - Danh sách và tạo công việc
- GET/PUT/DELETE `/api/tasks/{id}/` - Chi tiết công việc
- PATCH `/api/tasks/{id}/update_status/` - Cập nhật trạng thái
- GET/POST `/api/tasks/{id}/comments/` - Bình luận
- GET/POST `/api/tasks/{id}/attachments/` - Tập tin đính kèm

## Contributing

1. Fork repository
2. Tạo branch mới (`git checkout -b feature/AmazingFeature`)
3. Commit thay đổi (`git commit -m 'Add some AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Tạo Pull Request

## License

Distributed under the MIT License. See `LICENSE` for more information.
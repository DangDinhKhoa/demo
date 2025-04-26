## HỆ THỐNG TẠO BANNER QUẢNG CÁO TỰ ĐỘNG SỬ DỤNG TRÍ TUỆ NHÂN TẠO (AI)

### I. Giới thiệu
Dự án này ứng dụng trí tuệ nhân tạo (AI) để tự động tạo banner quảng cáo, giúp đơn giản hóa quá trình thiết kế và nâng cao hiệu quả truyền thông trong giáo dục, đặc biệt trong chuyên ngành đồ họa và mỹ thuật.

Hệ thống có khả năng:
- Tạo banner theo các phong cách thiết kế đa dạng: cổ điển, hiện đại, tối giản, hoặc anime.
- Tạo banner phù hợp với mục đích cụ thể, như quảng bá sự kiện, dự án học sinh, hoặc chiến dịch sáng tạo.
- Hỗ trợ giáo viên và học sinh trong việc xây dựng các sản phẩm trực quan chất lượng cao, tiết kiệm thời gian thiết kế thủ công.

### II. Cấu trúc thư mục
```bash
root/
├── laravel-app/         # Giao diện người dùng và kết nối với cơ sở dữ liệu
└── api_public_base/     # API hỗ trợ tạo câu hỏi
```

### III. Cấu hình

#### 1. Cơ sở dữ liệu
- File `create_banner_using_ai.sql` chứa cấu trúc và dữ liệu mẫu cho hệ thống.
- Chỉ cần import file này vào hệ quản trị cơ sở dữ liệu (MySQL hoặc tương đương) để sử dụng ngay.

#### 2. Thiết lập laravel-app
**2.1. Di chuyển vào thư mục dự án**
```bash
cd laravel-app
```
**2.2. Tải các package**
```bash
npm install
composer install
npm run build
```
**2.3. Cấu hình file môi trường**
```bash
cp .env.example .env
```
Sau đó, thêm dòng sau vào file .env:
- Cấu hình fast api:
```bash
FASTAPI_KEY= # Đúng với API_KEY trong file .env của thư mục api_public_base
FASTAPI_URL= # URL endpoint
```
- Cấu hình queue:
```bash
QUEUE_CONNECTION=database
```
- Cấu hình broadcasting với pusher:
```bash
BROADCAST_CONNECTION=pusher
BROADCAST_DRIVER=pusher
PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_APP_CLUSTER=
PUSHER_HOST=
PUSHER_PORT=
PUSHER_SCHEME=

VITE_APP_NAME="${APP_NAME}"
VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_HOST="${PUSHER_HOST}"
VITE_PUSHER_PORT="${PUSHER_PORT}"
VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
```
- Cấu hình mail:
```bash
MAIL_MAILER=smtp
MAIL_SCHEME=null
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=""
MAIL_FROM_NAME="${APP_NAME}"
```
**2.4. Khởi chạy lại sau khi chỉnh sửa file .env**
```bash
npm run build
```
**2.5. Khởi chạy ứng dụng Laravel**
```bash
php artisan serve
php artisan queue:work
```
### 3. Thiết lập api_public_base
**3.1. Di chuyển vào thư mục dự án**
```bash
cd api_public_base
```
**3.2. Cài đặt các thư viện cần thiết**
```bash
pip install -r requirements.txt
```
**3.3. Cấu hình file .envTạo file .env trong thư mục api_public_base và thêm các dòng sau:**
```bash
API_KEY =                   # API key của api
KEY_API_GOOGLE =            # API key của Gemini
OPENROUTER_XAI_API_KEY=     # API key của OpenRouter
LLM_NAME = "xai"            # Tên LLM được dùng
GOOGLE_LLM =                # Tên model của Gemini
OPENROUTER_XAI_LLM =        # Tên model của XAI, dùng thông qua OpenRouter
```
**3.4. Khởi chạy API**
```bash
python run_api.py
```
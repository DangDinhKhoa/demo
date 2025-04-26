HỆ THỐNG TẠO BANNER QUẢNG CÁO TỰ ĐỘNG SỬ DỤNG TRÍ TUỆ NHÂN TẠO (AI)
I. Giới thiệu
Dự án này ứng dụng trí tuệ nhân tạo (AI) để tự động tạo banner quảng cáo, giúp đơn giản hóa quá trình thiết kế và nâng cao hiệu quả truyền thông trong giáo dục, đặc biệt trong chuyên ngành đồ họa và mỹ thuật.

Hệ thống có khả năng:

Tạo banner theo các phong cách thiết kế đa dạng: cổ điển, hiện đại, tối giản, hoặc anime.
Tạo banner phù hợp với mục đích cụ thể, như quảng bá sự kiện, dự án học sinh, hoặc chiến dịch sáng tạo.
Hỗ trợ giáo viên và học sinh trong việc xây dựng các sản phẩm trực quan chất lượng cao, tiết kiệm thời gian thiết kế thủ công.
Hỗ trợ giáo viên và giảng viên trong việc xây dựng ngân hàng đề thi chất lượng cao.
II. Cấu trúc thư mục
root/
├── laravel-app/         # Giao diện người dùng và kết nối với cơ sở dữ liệu
└── api_public_base/     # API hỗ trợ tạo câu hỏi
III. Cấu hình
1. Cơ sở dữ liệu
File create_banner_using_ai.sql chứa cấu trúc và dữ liệu mẫu cho hệ thống.
Chỉ cần import file này vào hệ quản trị cơ sở dữ liệu (MySQL hoặc tương đương) để sử dụng ngay.
2. Thiết lập laravel-app
2.1. Di chuyển vào thư mục dự án
cd laravel-app
2.2. Tải các package
npm install
composer install
npm run build
2.3. Cấu hình file môi trường
cp .env.example .env
Sau đó, thêm dòng sau vào file .env:


FASTAPI_KEY= # Đúng với API_KEY trong file .env của thư mục api_public_base
FASTAPI_URL= # URL endpoint
2.4. Khởi chạy ứng dụng Laravel
php artisan serve
php artisan queue:work
3. Thiết lập api_public_base
3.1. Di chuyển vào thư mục dự án
cd api_public_base
3.2. Cài đặt các thư viện cần thiết
pip install -r requirements.txt
3.3. Cấu hình file .env
Tạo file .env trong thư mục api_public_base và thêm các dòng sau:


API_KEY=                    # trùng với PYTHON_API_KEY trong laravel-app

KEY_API_GEMINI=            # API key của Gemini
GEMINI_LLM_MODEL=          # Tên model của Gemini

KEY_API_GPT=               # API key của OpenAI
OPENAI_LLM_MODEL=          # Tên model của OpenAI
LLM_NAME=openai

KEY_API_GROK=xai-          # API key của Grok
GROK_LLM_MODEL=            # Tên model của Grok

KEYWORD_REMEMBER=          # Từ khóa cho cấp độ Nhớ
KEYWORD_UNDERSTAND=        # Từ khóa cho cấp độ Hiểu
KEYWORD_APPLY=             # Từ khóa cho cấp độ Áp dụng
KEYWORD_ANALYZE=           # Từ khóa cho cấp độ Phân tích
KEYWORD_EVALUATE=          # Từ khóa cho cấp độ Đánh giá
KEYWORD_CREATE=            # Từ khóa cho cấp độ Sáng tạo
3.4. Khởi chạy API
python run_api.py
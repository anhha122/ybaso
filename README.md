
# Y Bạ Số – Hệ thống quản lý khám chữa bệnh Đông y

**C# | .NET 8 | Blazor Server | DevExpress XAF | SQL Server**

## Giới thiệu

Y Bạ Số là ứng dụng web hỗ trợ số hóa quy trình quản lý khám chữa bệnh Đông y, tập trung vào quản lý hồ sơ bệnh nhân, ca khám, kết quả đánh giá, đơn thuốc, kho dược liệu và hóa đơn.

Dự án được phát triển trên nền tảng ASP.NET Core Blazor Server, kết hợp DevExpress eXpressApp Framework (XAF) để xây dựng ứng dụng quản lý có phân quyền.

## Chức năng chính

### 1. Quản lý bệnh nhân
- Quản lý thông tin và hồ sơ bệnh nhân.
- Liên kết hồ sơ với tài khoản đăng nhập.
- Phân quyền truy cập dữ liệu bệnh nhân.

### 2. Quản lý khám chữa bệnh
- Quản lý ca khám, bác sĩ, thời gian và trạng thái.
- Ghi nhận dữ liệu số đo phục vụ khám Đông y.
- Tổ chức kết quả chẩn đoán, bệnh chứng, ngũ tà và pháp trị.
- Hỗ trợ xem trước thông tin phiếu khám.

### 3. Quản lý đơn thuốc
- Quản lý đơn thuốc và chi tiết đơn thuốc.
- Quản lý danh mục thuốc và thành phần dược liệu.
- Liên kết thông tin thuốc với nghiệp vụ kho.

### 4. Quản lý kho dược liệu
- Quản lý danh mục dược liệu.
- Quản lý tồn kho, phiếu nhập và phiếu xuất.
- Kiểm tra số lượng dược liệu trước khi tạo tồn thuốc.
- Thông báo khi số lượng dược liệu không đáp ứng nhu cầu.

### 5. Quản lý hóa đơn
- Quản lý hóa đơn bệnh nhân.
- Quản lý các mục chi tiết hóa đơn.

### 6. Phân quyền người dùng
Hệ thống được tổ chức theo bốn vai trò:
- Admin: Quản trị hệ thống.
- Bác sĩ: Thực hiện các nghiệp vụ khám, chẩn đoán và đơn thuốc.
- Nhân viên: Quản lý hồ sơ và các nghiệp vụ vận hành được cấp quyền.
- Bệnh nhân: Truy cập thông tin cá nhân và dữ liệu khám chữa bệnh thuộc tài khoản của mình.

## Công nghệ sử dụng

| Thành phần | Công nghệ |
|---|---|
| Ngôn ngữ | C# |
| Nền tảng | .NET 8 |
| Web Framework | ASP.NET Core Blazor Server |
| Application Framework | DevExpress XAF |
| ORM | DevExpress XPO |
| Database | Microsoft SQL Server |
| Excel Processing | ClosedXML |
| Version Control | Git, GitHub |

## Cấu trúc dự án

```text
ybaso/
├── ybaso.slnx
├── .editorconfig
├── .gitignore
└── ybaso/
    ├── ybaso.Blazor.Server/
    │   ├── Program.cs
    │   ├── Startup.cs
    │   └── Services/
    └── ybaso.Module/
        ├── BusinessObjects/
        ├── Controllers/
        └── DatabaseUpdate/
```

**ybaso.Blazor.Server:** Chứa ứng dụng web, cấu hình Blazor, xác thực và các dịch vụ.

**ybaso.Module:** Chứa đối tượng dữ liệu, bộ điều khiển và logic nghiệp vụ.

**DatabaseUpdate:** Xử lý cập nhật cơ sở dữ liệu và khởi tạo một số dữ liệu ban đầu.

## Cài đặt và chạy dự án

### Yêu cầu
- .NET SDK 8
- Visual Studio hoặc môi trường phát triển .NET tương thích
- SQL Server LocalDB hoặc SQL Server
- Các package và quyền sử dụng DevExpress phù hợp với phiên bản dự án

### Bước 1. Clone repository

```powershell
git clone https://github.com/anhha122/ybaso.git
cd ybaso
```

### Bước 2. Cấu hình cơ sở dữ liệu

Kiểm tra cấu hình ConnectionStrings tại:

`ybaso/ybaso.Blazor.Server/appsettings.json`

Cấu hình mẫu sử dụng SQL Server LocalDB với database `ybaso`.

Không đưa mật khẩu, khóa API hoặc thông tin kết nối nhạy cảm vào repository.

### Bước 3. Khôi phục dependencies

```powershell
dotnet restore ybaso/ybaso.Blazor.Server/ybaso.Blazor.Server.csproj
```

### Bước 4. Chạy ứng dụng

```powershell
dotnet run --project ybaso/ybaso.Blazor.Server/ybaso.Blazor.Server.csproj
```

Truy cập địa chỉ localhost được hiển thị trong terminal.

**Lưu ý:** Các bước trên cần được kiểm thử với môi trường đã cài đặt đầy đủ DevExpress và cấu hình cơ sở dữ liệu tương ứng.

## Điểm nổi bật về kỹ thuật

- Tổ chức ứng dụng theo module và các đối tượng nghiệp vụ.
- Sử dụng hệ thống phân quyền XAF Security theo vai trò và dữ liệu.
- Tùy chỉnh giao diện danh sách ca khám bằng Controller.
- Kiểm tra điều kiện tồn kho trước khi thực hiện nghiệp vụ tạo thuốc.
- Hỗ trợ dữ liệu khởi tạo và nhập danh mục Đông y từ Excel.

## Lưu ý

Dự án phục vụ mục đích giới thiệu mã nguồn và quá trình phát triển phần mềm.

Các chức năng phân tích, chẩn đoán chỉ mang tính hỗ trợ và không thay thế đánh giá chuyên môn của bác sĩ.

Không sử dụng dữ liệu bệnh nhân thật hoặc thông tin xác thực mặc định trong môi trường công khai.

## Thông tin dự án

**Repository:** https://github.com/anhha122/ybaso

### PHẦN 1: *PHÂN TÍCH VI PHẠM 5 QUY TẮC VÀNG TRONG TƯ DUY DATABASE*
Bảng tính hiện tại đang vi phạm 3 quy tắc vàng quan trọng sau:

1. Vi phạm Quy tắc không Merge Cell (Không gộp ô trong vùng dữ liệu / hàng tiêu đề):

Nguyên nhân & Hậu quả: Việc gộp ô (Merge Cells) ở hàng tiêu đề khiến Excel không thể định vị chính xác vị trí bắt đầu và kết thúc của các cột. Điều này làm gián đoạn tính năng AutoFilter, gây lỗi khi sắp xếp (Sort), trích xuất dữ liệu hoặc viết công thức.

2. Vi phạm Quy tắc Dữ liệu liên tục (Không chứa hàng/cột trống hoàn toàn ngắt quãng):

Nguyên nhân & Hậu quả: Bảng dữ liệu có một hàng trống hoàn toàn nằm ở giữa. Khi bấm phím tắt Ctrl + Shift + L, Excel sẽ tự động xác định vùng dữ liệu liên tục xung quanh ô đang chọn. Hàng trống này hoạt động như một "vách ngăn", làm cho AutoFilter bị đứt đoạn và không nhận diện được phần dữ liệu phía sau hàng trống.

3. Vi phạm Quy tắc Tính chuẩn hóa & Chuẩn mực dữ liệu (Data Integrity / Clean Data):

Nguyên nhân & Hậu quả: Nhập liệu chứa khoảng trắng dư thừa (khoảng trắng vô hình ở đầu/cuối chuỗi như " hỏng", "hỏng "). Dù nhìn bằng mắt thường thấy giống hệt nhau, Excel lại hiểu đây là các giá trị văn bản khác nhau, dẫn đến việc AutoFilter tách thành nhiều nhóm riêng biệt khi gom nhóm/lọc dữ liệu.

### PHẦN 2: *HƯỚNG DẪN HOÀN THIỆN & LÀM SẠCH DỮ LIỆU*
Bước 1: Gỡ bỏ Merge Cells ở hàng tiêu đề
- Bôi đen toàn bộ hàng tiêu đề đang bị gộp ô.
- Tại tab Home --> nhóm Alignment, chọn Merge & Center (hoặc nhấn chuột phải --> Format Cells --> tab Alignment --> bỏ tích Merge cells).\
- Đặt lại tên tiêu đề rõ ràng cho từng cột đơn lẻ (mỗi cột chứa đúng 1 loại thuộc tính).
Bước2: Xóa bỏ các hàng trống ngắt quãng
- Bôi đen toàn bộ vùng dữ liệu (hoặc cột chứa mã thiết bị).
- Nhấn phím F5 (hoặc Ctrl + G) --> chọn Special...
- Tích chọn Blanks --> nhấn OK (Excel sẽ tự động bôi đen tất cả các ô/hàng trống).\
- hấn chuột phải vào một ô trống vừa được chọn $\rightarrow$ chọn Delete... --> chọn Shift cells up hoặc Entire row để xóa sạch các hàng trống.
Bước 3: Làm sạch cột "Trạng thái" bằng hàm TRIM()
  1. Tạo cột phụ: Chèn thêm một cột tạm bên cạnh cột "Trạng thái" (ví dụ: cột "Trạng thái chuẩn").

  2. Áp dụng công thức: Tại ô đầu tiên của cột phụ (ví dụ E2), nhập công thức: =TRIM(D2)

  3. Copy công thức: Kéo copy công thức xuống toàn bộ các hàng còn lại trong cột.

  4. Ghi đè dữ liệu chuẩn:
     - Bôi đen toàn bộ cột dữ liệu vừa dùng hàm TRIM.
     - Nhấn Ctrl + C để copy.
     - Nhấp chuột phải vào cột "Trạng thái" ban đầu $\rightarrow$ chọn Paste Special $\rightarrow$ chọn Values (dán giá trị thuần để bỏ công thức).
     - Xóa cột phụ vừa tạo.
 Bước 4: Kích hoạt lại AutoFilter trên toàn bộ bảng dữ liệu
 - Click chọn một ô bất kỳ bên trong vùng dữ liệu đã được làm sạch.

 - Nhấn tổ hợp phím Ctrl + Shift + L để bật AutoFilter.

 - Nhấp vào mũi tên Filter tại cột "Trạng thái" để kiểm tra: Các thiết bị lỗi lúc này đã được gộp chuẩn xác thành một nhóm duy nhất (ví dụ: chỉ còn nhóm "hỏng").

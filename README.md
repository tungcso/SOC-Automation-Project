# SOC Automation Project

Dự án tự động hóa phản ứng với các mối đe dọa bảo mật (Security Orchestration, Automation, and Response - SOAR).

## 🎯 Tổng quan dự án
Dự án tập trung vào việc tự động hóa quy trình phản ứng bảo mật (Active Response) khi phát hiện các hành vi xâm nhập trái phép trên Endpoint thông qua việc tích hợp hệ thống Wazuh và nền tảng điều phối Shuffle.

## 🛠️ Luồng kỹ thuật (Workflow)
* **Phát hiện (Detection):** Sử dụng Sysmon để thu thập log trên Windows và cấu hình Wazuh để phát hiện hành vi Mimikatz (tactic T1003 - Credential Access).
* **Điều phối (Orchestration):** Sử dụng nền tảng Shuffle để điều phối log, xử lý logic xác thực API và tự động hóa tác vụ.
* **Phản ứng (Response):** Thực hiện lệnh `firewall-drop` qua Wazuh API để cô lập máy bị nhiễm ngay lập tức khi phát hiện mối đe dọa, ngăn chặn hành vi đánh cắp thông tin.

## 🚀 Kết quả đạt được
* Thiết lập thành công luồng tự động hóa với kết nối API bảo mật (sử dụng Token xác thực).
* Đạt phản hồi `200 OK` từ hệ thống API của Wazuh trong các bài kiểm tra thực tế (Test Mimikatz).
* Tối ưu hóa kiến trúc truyền tải dữ liệu và xử lý lỗi (Fault-tolerant design) trong quá trình kết nối API.

## 📁 Cấu trúc thư mục
- `workflow.json`: File cấu hình luồng tự động hóa Shuffle (đã lược bỏ API Token vì lý do bảo mật).

## 💡 Hướng dẫn sử dụng
1. Import file `workflow.json` vào nền tảng Shuffle.
2. Cấu hình lại API Key của Wazuh trong phần Header của các Action.
3. Chạy kiểm tra bằng cách thực thi các hành vi mẫu (Mimikatz) trên máy Endpoint đã cài Wazuh Agent.

---
*Dự án được thực hiện nhằm mục đích học tập và nghiên cứu về SOC Automation.*
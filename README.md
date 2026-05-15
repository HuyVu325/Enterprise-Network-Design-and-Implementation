# Enterprise Network Design & Implementation (Mô phỏng Mạng Doanh Nghiệp)

## 📌 Giới thiệu dự án
[cite_start]Dự án này mô phỏng việc thiết kế và cấu hình hạ tầng mạng hoàn chỉnh cho một doanh nghiệp, bao gồm Hội sở chính (HQ) và một Chi nhánh (Branch)[cite: 7, 16]. Hệ thống được thiết kế để đảm bảo tính sẵn sàng cao, bảo mật chặt chẽ và khả năng giao tiếp xuyên suốt giữa các chi nhánh thông qua môi trường Internet.

## 🏢 Kiến trúc hệ thống

### 1. Hội sở chính (HQ)
Hội sở được chia thành 3 tòa nhà với cấu trúc phân cấp:
* [cite_start]**Building 1 (Trung tâm):** Đặt CoreSwitch quản lý lưu lượng chính và kết nối với 2 phòng ban thuộc khu vực VP TNTT[cite: 8, 10].
* [cite_start]**Building 2 & Building 3:** Mỗi tòa nhà trang bị 1 Distribution Switch kết nối về CoreSwitch, phục vụ lần lượt 3 và 2 phòng ban[cite: 9, 10].
* [cite_start]**Hệ thống Server:** * **Public Servers:** Web Server và Email Server cung cấp dịch vụ ra ngoài Internet[cite: 12].
    * [cite_start]**Internal Servers:** DHCP Server và DNS Server phục vụ mạng nội bộ[cite: 13].
* [cite_start]**Khu vực quản trị:** Cho phép người quản trị cấu hình từ xa qua Telnet/SSH[cite: 14].
* [cite_start]**Bảo mật:** Trang bị Firewall để bảo vệ mạng nội bộ khỏi các mối đe dọa từ bên ngoài[cite: 15].

### 2. Chi nhánh (Branch)
* [cite_start]Bao gồm 3 phòng ban và có hệ thống DHCP Server riêng cấp phát IP cho người dùng[cite: 17, 18].
* [cite_start]Được bảo vệ bởi Firewall riêng biệt[cite: 20].

## 🛠️ Công nghệ và Kỹ thuật áp dụng
Dự án áp dụng các kỹ thuật mạng cốt lõi (sử dụng Cisco Packet Tracer / GNS3):

* [cite_start]**Switching:** Cấu hình VLAN để phân chia broadcast domain, sử dụng VTP để đồng bộ VLAN và cấu hình đường Trunking giữa các Switch[cite: 24].
* [cite_start]**Routing:** Cấu hình định tuyến (Tĩnh/Động) đảm bảo các thiết bị trong mạng nội bộ giao tiếp được với nhau.
* **NAT (Network Address Translation):**
    * [cite_start]**NAT Overloading (PAT):** Cho phép người dùng nội bộ truy cập Internet[cite: 26].
    * [cite_start]**Static NAT:** Public Web Server (IP: `4.4.4.4`) và Email Server (IP: `5.5.5.5`) ra môi trường Internet[cite: 27].
* [cite_start]**VPN (Virtual Private Network):** Triển khai cấu hình **IPSec VPN Site-to-Site** kết nối an toàn giữa Branch và HQ, cho phép chi nhánh sử dụng các ứng dụng nội bộ đặt tại hội sở[cite: 19, 28].

## 🖼️ Sơ đồ mạng (Network Topology)
![Network Topology](images/topology.png)

## 🚀 Hướng dẫn cài đặt và kiểm tra
1. Tải phần mềm mô phỏng (ví dụ: Cisco Packet Tracer phiên bản x.x.x).
2. Mở file project: `[Tên_file_của_bạn].pkt`
3. Các kịch bản kiểm tra (Test cases):
   * Ping kiểm tra kết nối nội bộ giữa các phòng ban trong hệ thống.
   * Dùng PC ở ngoài Internet truy cập vào Web Server bằng IP public `4.4.4.4`.
   * Gửi gói tin từ Branch sang HQ qua đường hầm VPN Site-to-Site.

## 📝 Thông tin cá nhân
* Dự án môn học Lập trình / Quản trị mạng.
* [cite_start]IP Plan được thiết kế và tùy biến theo mã số sinh viên[cite: 3, 23].

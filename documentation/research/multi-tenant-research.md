# MULTI-TENANT

## Giải pháp thiết kế CSDL Multi Tenant

[Reference](https://rabiloo.com/vi/blog/giai-phap-thiet-ke-co-so-du-lieu-multi-tenant)

### Multi-tenant là gì?

- `Multi-tenant` là giải pháp thiết kế phần mềm với _cùng chỉ 1 phiên bản ứng dụng_ nhưng vẫn có _cơ sở dữ liệu phục vụ cho nhiều khách hàng cùng 1 lúc_

- Dữ liệu khách hàng _sẽ độc lập, tách biệt với nhau_

- **Example:**

- Những _hệ thống kiến trúc nhiều người thuê_ hay sử dụng multi-tenancy model: _Github, Hubspot, Salesforce, Slack, Jira, Office 365, ..._

### Ưu điểm sử dụng Multi Tenant

- Lưu trữ, quản lý đơn giản

- Bảo mật hệ thống tốt hơn

- Dễ dàng nâng cấp, đồng bộ cấu trúc hơn

### Nhược điểm sử dụng Multi Tenant

- Vấn đề back-up database cho từng tenant

- Dữ liệu dễ phình to -> scalable system consider

### Thiết kế CSDL

- Các vấn đề cần quan tâm:

  - Mức độ độc lập dữ liệu
  - Khả năng backup và sao lưu db của tenant

- Tùy vào nhu cầu, có thể có các cách triển khai cơ sở dữ liệu:

  - `Approach 1`: Mỗi tenant - mỗi db riêng biệt

  - `Approach 2`: Sử dụng chung database nhưng chia tách table hoặc schema cho từng tenant

  - `Approach 3`: Sử dụng chung cả database và schema

**Approach 1:**

- Hệ thống sẽ có 1 `DB chính` - lưu trữ tenants và các thông tin tenant, etc. và các `DB tenant` - có cấu trúc giống nhau

- Người dùng sẽ chỉ được truy cập vào `DB tenant` của họ

- _Ưu điểm:_

  - Mức độ an toàn dữ liệu cao nhất
  - DB độc lập hoàn toàn

- _Nhược điểm:_

  - Tốn kém, chỉ phù hợp với đối tượng có yêu cầu đặc biệt và chịu chi

**Approach 2:**

- Hệ thống sử dụng chung 1 `DB` - mỗi Tenant sử dụng 1 `Schema` - có cấu trúc table giống nhau

- Có schema chung để quản lý thông tin, danh sách các tenants

- 1 schema với cấu trúc table chuẩn để từ đó tạo ra tenant mới trong quá trình hoạt động hệ thống

- _Ưu điểm:_

  - Có thể phân quyền ở cấp Schema -> tăng tính bảo mật
  - Tiết kiệm chi phí

- _Nhược điểm:_

  - Do DBMS không hỗ trợ khôi phục Schema, nên back-up sẽ restore toàn bộ DB -> ảnh hưởng tới những tenants không liên quan
  - Số lượng schema trong 1 database là có giới hạn

**Approach 3:**

- Dữ liệu của tenant lưu trong Table - phân biệt thông qua cột định danh `tenant_id`

- _Ưu điểm:_

  - Thiết kế đơn giản
  - Hạn chế được vấn đề khi đồng bộ cấu trúc bảng hệ thống

- _Nhược điểm:_

  - Phân quyền trong DBMS thực sự là vấn đề lớn
  - Database của các tenant sẽ không độc lập, gây nguy cơ bảo mật
  - Bắt buộc phải backup, restore tất cả tenants
  - Database nhanh chóng phình to, scale hệ thống sẽ gặp nhiều khó khăn

- Dùng làm những hệ thống nhỏ, ít dữ liệu, phát sinh dữ liệu không lớn

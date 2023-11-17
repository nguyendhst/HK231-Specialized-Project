# BPMN Research

## BPMN (Business Process Modeling Notation) là gì?

- Được sử dụng để mô hình hóa các quy trình nghiệp vụ phức tạp bằng những hình vẽ tiêu chuẩn, để giúp cho việc trao đổi, truyền đạt, thiết kế, triển khai quy trình nghiệp vụ giữa các thành viên trong team, và giữa team với khách hàng được đồng nhất

- BPMN là một dạng sơ đồ áp dụng những tiêu chuẩn nhât định để mô tả quy trình nghiệp vụ

- BPMN sử dụng Biểu đồ luồng (Flow chart) cùng **tập hợp các ký hiệu chuẩn** để mô hình hóa quy trình doanh nghiệp

### Add-ons:

- _Nguồn gốc:_ được phát triển bởi tổ chức Business Process Management Initiative (BPMI) từ 2005 và được ứng dụng trong phát triển quy trình nghiệp vụ của nhiều tổ chức khác nhau và trở thành _cầu nối_ giữa mô hình kinh doanh và công nghệ thông tin.

- _Điểm mạnh:_ có thể dựa vào BPMN để tìm ra những phần chưa tối ưu trong quy trình hiện hành và đưa ra cả tiến

## Ký hiệu trong BPMN

### Pool và Lane

- `Pool:` đại diện cho tổ chức, phòng ban

- `Lane:` đại diện cho 1 cá thể trong tổ chưc, phòng ban mà pool đại diện

- 1 Pool sẽ có nhiều Lane

### Activity

- _Hình chữ nhật bo góc - có hình ảnh đại hiện hành động ở góc trái-trên và mô tả ở giữa_

- `Activity:` đại diện cho hoạt động của một cá thể `Lane`

  - `Đơn giản: ` (Task)
  - `Phức tạp: ` (Sub-process) - _có thêm một dấu cộng phía dưới môt tả_
  - Read more at [Reference 2](#references)

### Flow

- _Mũi tên thể hiện đường đi của quy trình_

- Cũng bao gồm nhiều loại flow khác nhau:

  - `Sequence Flow:` đường đi từ `task/sub-process` này tới `task/sub-process` kia
  - `Default Flow:` luồng đi mặc định của hệ thống nếu không có gì khác thường xảy ra
  - `Message Flow:` luồng thông tin trao đổi giữa các lane và các pool với nhau
  - `Conditional Flow:` khi đạt điều kiện cụ thể thì quy trình sẽ thực thi theo flow này

### Gateway

- _Hình thoi có các ký hiệu mô tả ở giữa để thể hiện loại của nó_

- Cũng bao gồm nhiều loại gateway khác nhau:

  - `Exclusive Gateway:` Khi đi qua gateway này chỉ được đi qua 1 flow kế tiếp
  - `Inclusive Gateway:` Có thể sau gateway đi qua 1 hoặc nhiều nhánh nhưng tới cuối phải merge
  - `Parallel Gateway:` Có thể sau gateway đi qua nhiều nhánh nhưng các nhánh phải hoàn thành mới được gộp lại
  - `Event-Based:` Tương tự Exclusive nhưng việc chọn nhánh là dựa vào sự kiện xảy ra trước đó

### Event

- _Các thể loại hình tròn với các border và mô tả khác nhau_

- Có 4 loại event quan trọng chính:

  - `Start:` Xảy ra lúc bắt đầu một quy trình
  - `Intermediate:` Xảy ra ở giữa của quy trình
  - `End:` Xảy ra khi kết thúc quy trình
  - `Boundary:` Event loại này được vẽ liền với hình chữ nhật của task và xảy ra gắn liền với task
  - Read more at [Reference 3](#references)

### Artifact

- thể hiện các đối tượng bên ngoài của quy trình hiện tại

- Artifact có 3 loại: đối tượng dữ liệu (data object), ghi chú (annotation) và nhóm (group)

## References

1. [BPMN](https://viblo.asia/p/cung-tim-hieu-ve-business-process-modeling-notation-bpmn-Qbq5Qm8m5D8)

2. [BPMN Activity](https://www.visual-paradigm.com/guide/bpmn/bpmn-activity-types-explained/)

3. [BPMN Event](https://www.visual-paradigm.com/guide/bpmn/bpmn-events/)

# BPMN more from References

## BPMN Task

### Service Task

- Có icon `bánh răng - setting`

- Liên quan tới các task sử dụng `Web Services`, các `Automated Application`, và các loại services khác để hoàn thành task

### Send Task

- Có icon `hộp thư - mail` (đen)

- Liên quan tới việc gửi một `Message` tới một pool khác. Task được tính là hoàn thiện khi `Message` được gửi đi

### Recieve Task

- Có icon `hộp thư - mail` (trắng)

- Thể hiện process đang chờ một `Message` để tiếp tục hoạt động. Task được tính là hoàn thành khi nhận được `Message`

### User Task

- Có `icon - human`

- Thể hiện task có người thực hiện task với _sự phục vụ của phần mềm_

### Manual Task

- Có `icon - hand`

- Thể hiện task được thực hiện hoàn toàn thủ công không có sự giúp đỡ của business engine hay application

### Business Rule Task

- Là một ký hiệu mới trong BPMN 2.0

- Có `icon - table`

### Script Task

- Có `icon - script`

- Được `thực hiện bởi business process engine` - định nghĩa một script để engine có thể hiểu và hiện thực

- Task bắt đầu - engine execute the script - task hoàn thiện khi script completion

## BPMN Subprocess

- Chia những _process phức tạp_ thành nhiều mức, cho phép tập trung vào những điểm quan trọng chính của sơ đồ

### Loop

### Multi-instance

### Compensation

### Ad-Hoc

### Compensation and Ad-Hoc

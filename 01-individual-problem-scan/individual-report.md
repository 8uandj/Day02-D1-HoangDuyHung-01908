Case **ETL pipeline optimization daily**

Nhân vật: Huy - một Junior Data Engineer với công việc hằng ngày là tối ưu hóa hiệu suất ETL pipeline và viết technical report cho Senior Data Engineer.

# 01 - Individual Problem Scan

## Scan rộng

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Hằng ngày Huy nhận các task tối ưu nhiều luồng ETL trong team, nhưng mỗi task vẫn phải tự đọc lại context pipeline, input/output và dependency trước khi bắt đầu | Huy, Senior Data Engineer, Data Team (DS, DA, BA) | Lặp lại hằng ngày; mất khoảng 15-30 phút để nắm context trước mỗi task |
| 2 | Tốn thời gian | Normalize data ở ingest stage khi data được ingest từ nhiều nguồn với nhiều định dạng khác nhau | Huy, Data Team (DA, DS, BA) | Tốn khoảng 90 phút/task; dễ sai mapping field hoặc type nếu source thay đổi |
| 3 | Lặp lại | Sau khi normalize data ở ingest stage, Huy phải chạy hoặc chỉnh script để automate việc load data vào database, data warehouse hoặc data mart | Huy, Senior Data Engineer, Data Team (DA, DS, BA) | Lặp lại hằng ngày; các bước tương tự nhưng vẫn cần kiểm tra thủ công theo từng source |
| 4 | Pain từ người khác | Các team DA/DS/BA phải đợi data pipeline thông suốt trước khi làm dashboard, analysis hoặc model training | Data Team, stakeholder dùng report/dashboard | Thường trễ deadline khi pipeline bị nghẽn; các team phải hỏi lại trạng thái pipeline |
| 5 | AI có thể tốt hơn | Huy mất thời gian đọc log lỗi ETL dài để xác định nguyên nhân gốc như schema mismatch, null spike, timeout hoặc data type conflict | Junior/Senior Data Engineer, DA/DS chờ data | Mỗi incident có thể mất 30-60 phút đọc log và trace nhiều job |
| 6 | AI có thể tốt hơn | Khi pipeline chạy chậm, Huy phải tự so sánh runtime nhiều ngày để đoán bước nào bị performance regression | Data Engineering team | Việc so sánh thủ công mất 20-40 phút/task, dễ bỏ sót pattern bất thường |
| 7 | Tốn thời gian | Viết technical report sau mỗi task optimization mất nhiều công vì phải gom context, before/after metric, nguyên nhân và hướng xử lý | Huy, Senior Data Engineer | Report gửi Senior thường cần chỉnh lại vì thiếu metric hoặc thiếu giải thích trade-off |
| 8 | Pain từ người khác | DA/DS không biết pipeline nào đang delay, delay ở stage nào và ETA khi nào data sẵn sàng | DA, DS, BA, stakeholder dùng dashboard | Hay phải hỏi lại qua chat khi dashboard/data mart chưa cập nhật đúng giờ |
| 9 | Lặp lại | Huy phải kiểm tra thủ công data quality sau ingest như duplicate, missing value, unexpected category trước khi load vào warehouse | Data Engineering team, downstream analytics users | Lặp lại theo từng source/table; nếu bỏ sót có thể làm sai dashboard hoặc model input |
| 10 | AI có thể tốt hơn | Khi nhận source data mới, Huy phải đọc schema/documentation và mapping field thủ công sang chuẩn nội bộ | Junior Data Engineer, Senior reviewer | Mất nhiều thời gian hiểu field name, business meaning và rule normalize; cần review lại nhiều lần |

## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | Đọc log lỗi ETL để tìm root cause | Actor rõ, bottleneck cụ thể, có thể đo thời gian triage, AI có thể hỗ trợ đọc/tóm tắt log nhưng vẫn cần người kiểm chứng | Chưa có log thật để đo chính xác baseline 45 phút; cần xác nhận các loại lỗi thường gặp |
| 2 | So sánh runtime để phát hiện performance regression | Có workflow rõ, có metric runtime trước/sau, có thể kết hợp rule phát hiện anomaly và AI giải thích pattern | Cần biết hệ thống hiện có lưu runtime history đầy đủ không |
| 3 | Viết technical report sau optimization task | Lặp lại sau mỗi task, tốn thời gian, output cần ngôn ngữ và cấu trúc nên AI có thể hỗ trợ tốt | Chất lượng report cần Senior đánh giá; metric "ít bị hỏi lại hơn" cần theo dõi thêm |

## Problem Card #1 - Đọc log lỗi ETL để tìm root cause

**Problem 1 câu:**  
Khi ETL pipeline lỗi, Huy mất khoảng 45 phút đọc log dài và trace nhiều job để tìm root cause trước khi biết nên sửa ở ingest, transform hay load stage.

**Actor:**  
Huy, Junior Data Engineer chịu trách nhiệm triage lỗi pipeline trước khi báo cáo hoặc nhờ Senior hỗ trợ.

**Thời điểm / bối cảnh:**  
Khi pipeline fail hoặc data không cập nhật đúng giờ trong daily ETL run.

**Current workflow:**

```text
1. Nhận alert pipeline fail
2. Mở log của job bị lỗi
3. Trace upstream/downstream dependency
4. Đọc log chi tiết để tìm error pattern
5. Đoán root cause và kiểm tra lại bằng query/script
6. Ghi chú nguyên nhân và hướng xử lý cho Senior
```

**Bottleneck:**  
Bước 4 - đọc log chi tiết và nối các error rời rạc thành root cause, ước lượng khoảng 45 phút/incident.

**Impact:**  
Pipeline khôi phục chậm làm DA/DS/BA phải chờ data; Senior mất thêm thời gian review nếu Huy báo cáo thiếu context.

**Success metric:**  
Giảm thời gian triage root cause từ khoảng 45 phút xuống dưới 15 phút/incident; không tăng số lần chẩn đoán sai nguyên nhân.

**Non-AI alternative:**  
Chuẩn hóa error code, dashboard alert theo stage, checklist triage cho các lỗi phổ biến.

**AI hypothesis:**  
AI có thể tóm tắt log, nhóm error pattern, gợi ý root cause và bước kiểm tra tiếp theo. Huy vẫn phải kiểm chứng bằng log/query thật trước khi sửa pipeline.

**Quick gut:**  
Workflow.

### Draft current workflow

```text
CURRENT STATE - 60 phút

[Nhận alert: 2']
-> [Mở log job fail: 5']
-> [Trace dependency: 8']
-> [Đọc log và tìm pattern: 30']  <-- bottleneck
-> [Kiểm chứng root cause: 10']
-> [Ghi chú/báo Senior: 5']
```

### Draft future workflow

```text
FUTURE STATE - 22 phút

[Nhận alert: 2']
-> [Rule gom log/job metadata: 2']
-> [AI tóm tắt error pattern và gợi ý root cause: 2']
-> [Huy kiểm chứng bằng query/log thật: 12']  <-- human boundary
-> [Huy ghi chú/báo Senior: 4']

Fallback: AI tóm tắt sai hoặc thiếu context -> Huy quay lại đọc log thủ công theo checklist triage.
```

## Problem Card #2 - So sánh runtime để phát hiện performance regression

**Problem 1 câu:**  
Khi ETL pipeline chạy chậm, Huy mất khoảng 30 phút so sánh runtime nhiều ngày và nhiều stage để tìm bước bị regress performance.

**Actor:**  
Huy và Senior Data Engineer theo dõi hiệu suất ETL pipeline.

**Thời điểm / bối cảnh:**  
Sau daily run, khi pipeline vượt SLA hoặc downstream team phản ánh data cập nhật trễ.

**Current workflow:**

```text
1. Kiểm tra pipeline run gần nhất
2. Lấy runtime từng stage
3. So sánh với các ngày trước
4. Tìm stage tăng thời gian bất thường
5. Kiểm tra data volume, query plan hoặc resource usage
6. Đề xuất hướng tối ưu
```

**Bottleneck:**  
Bước 3-4 - so sánh runtime thủ công và phát hiện stage bất thường, ước lượng khoảng 30 phút/task.

**Impact:**  
Performance regression bị phát hiện chậm khiến pipeline trễ SLA, ảnh hưởng dashboard/report/model downstream.

**Success metric:**  
Giảm thời gian tìm stage nghẽn từ 30 phút xuống dưới 10 phút; phát hiện đúng stage regression trong phần lớn incident được review.

**Non-AI alternative:**  
Rule cảnh báo nếu runtime tăng quá ngưỡng so với trung bình 7 ngày; dashboard trend theo stage.

**AI hypothesis:**  
Rule phát hiện anomaly; AI giải thích pattern runtime bằng ngôn ngữ dễ hiểu và gợi ý các bước kiểm tra tiếp theo. Huy/Senior vẫn quyết định nguyên nhân và cách tối ưu.

**Quick gut:**  
Rule + Workflow.

### Draft current workflow

```text
CURRENT STATE - 45 phút

[Nhận phản ánh pipeline chậm: 3']
-> [Lấy runtime từng stage: 7']
-> [So sánh nhiều ngày: 15']  <-- bottleneck
-> [Tìm stage bất thường: 10']
-> [Kiểm tra volume/resource/query: 8']
-> [Ghi hướng tối ưu: 2']
```

### Draft future workflow

```text
FUTURE STATE - 17 phút

[Rule tự tính runtime delta theo stage: 2']
-> [Dashboard highlight stage bất thường: 2']
-> [AI giải thích pattern và gợi ý kiểm tra: 2']
-> [Huy kiểm chứng volume/resource/query: 9']  <-- human boundary
-> [Ghi hướng tối ưu: 2']

Fallback: nếu rule/AI flag sai stage -> Huy dùng dashboard runtime gốc để so sánh thủ công.
```

## Problem Card #3 - Viết technical report sau optimization task

**Problem 1 câu:**  
Sau mỗi task optimization, Huy mất khoảng 40 phút viết technical report vì phải gom context, metric trước/sau, nguyên nhân và trade-off thành một bản rõ để Senior review.

**Actor:**  
Huy viết report cho Senior Data Engineer.

**Thời điểm / bối cảnh:**  
Sau khi hoàn thành một task tối ưu ETL pipeline hoặc xử lý incident performance.

**Current workflow:**

```text
1. Gom ticket/task context
2. Lấy metric before/after
3. Ghi nguyên nhân và cách xử lý
4. Viết technical report
5. Tự review format và số liệu
6. Gửi Senior review
7. Chỉnh lại nếu Senior hỏi thêm
```

**Bottleneck:**  
Bước 4 - biến raw note và metric thành report mạch lạc, ước lượng khoảng 40 phút/report.

**Impact:**  
Senior mất thêm thời gian hỏi lại nếu report thiếu metric, thiếu trade-off hoặc không rõ vì sao chọn hướng tối ưu.

**Success metric:**  
Giảm thời gian viết report từ khoảng 40 phút xuống dưới 15 phút/report; giảm số lần Senior phải hỏi lại vì thiếu context hoặc metric.

**Non-AI alternative:**  
Template report cố định gồm context, baseline, change, result, risk, next step.

**AI hypothesis:**  
AI draft report từ template và input có sẵn như metric before/after, log note, decision note. Huy phải kiểm tra số liệu, sửa technical conclusion và approve trước khi gửi.

**Quick gut:**  
Workflow.

### Draft current workflow

```text
CURRENT STATE - 55 phút

[Gom context task: 8']
-> [Lấy metric before/after: 10']
-> [Ghi nguyên nhân/cách xử lý: 7']
-> [Viết report: 20']  <-- bottleneck
-> [Review format/số liệu: 5']
-> [Gửi Senior: 2']
-> [Chỉnh theo feedback: 3']
```

### Draft future workflow

```text
FUTURE STATE - 24 phút

[Gom context + metric vào template: 8']
-> [AI draft report theo format chuẩn: 2']
-> [Huy kiểm số liệu và sửa conclusion: 10']  <-- human boundary
-> [Gửi Senior: 2']
-> [Chỉnh theo feedback: 2']

Fallback: AI draft nhạt hoặc sai số liệu -> Huy bỏ draft, dùng template thủ công.
```

## Card muốn pitch nhất

Card tôi muốn pitch nhất:

```text
Problem Card #1 - Đọc log lỗi ETL để tìm root cause.
```

Vì sao:

```text
Đây là problem có pain rõ, xảy ra khi pipeline fail nên impact trực tiếp tới nhiều team downstream. Workflow hiện tại vẽ được, bottleneck cụ thể là đọc log và trace root cause. AI có thể hỗ trợ tốt ở bước tóm tắt/nhóm lỗi/gợi ý hướng kiểm tra, nhưng boundary vẫn rõ: Huy phải kiểm chứng trước khi sửa production pipeline.
```

Câu hỏi tôi muốn nhóm challenge:

```text
Baseline 45 phút/incident có hợp lý không? Nếu chưa có log thật, nhóm nên validate bằng cách hỏi Senior hoặc xem lại 2-3 incident gần nhất trước khi chốt metric.
```

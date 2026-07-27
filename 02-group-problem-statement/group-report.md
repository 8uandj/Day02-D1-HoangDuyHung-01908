# Group Report - Day 02

Case nhóm chọn: **Thông tin học tập phân mảnh trên Vlearn, Codelabs và Discord**

## Thành viên nhóm

| STT | Họ và tên | Mã học viên |
|-----|-----------|-------------|
| 1 | Trà My | 2A202601290 |
| 2 | Thế Hưng | 2A202601822 |
| 3 | Thành Vinh | 2A202602021
| 4 | Hoàng Hưng | 2A202601908 |
| 5 | Mai Phương |2A202601418 |

---

# 01 - Group Convergence

## Candidates được pitch

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | Thành Vinh | Thông tin học tập phân mảnh | Học viên VinAI thực chiến | Phải tự nối Vlearn, Codelabs, Discord | Impact rộng, dễ validate |
| 2 | Trà My | Tóm tắt nội dung buổi họp | Người ghi biên bản | Tốn 30–45 phút sau mỗi buổi họp; thông tin phân công task dễ bị mơ hồ do xưng hô không rõ ràng trong lúc nói; thành viên thường không đọc kỹ recap dài. | Có thể dùng workflow review |
| 3 | Thế Hưng | Tư vấn FAQ và đặt lịch khám qua chat | Bệnh nhân/nhân viên phòng khám | Hỏi đáp lặp lại và đặt lịch thủ công | Có pain thật nhưng domain y tế rủi ro |
| 4 | Thế Hưng | Nhắc lịch tái khám và giảm trống lịch của Bác sĩ | CSKH, Lễ tân | Lọc danh sách hồ sơ đến hạn và nhắn tin/gọi điện thủ công từng người | Cần dữ liệu cá nhân, privacy cao |
| 5 | Trà My | Lên thực đơn theo mục tiêu | Người tự nấu ăn & người cần ăn uống theo chế độ | Phải tự tính món, nguyên liệu, calo | Dễ làm nhưng impact học tập thấp |
| 6 | Thành Vinh | Gợi ý mua nguyên liệu | Người nấu ăn | So sánh giá và khẩu phần | Dữ liệu giá thay đổi, scope rộng |
| 7 | Hoàng Hưng | So sánh runtime để phát hiện performance regression | Data Engineer, DA/DS | So sánh runtime thủ công và phát hiện stage bất thường |Workflow rõ nhưng nhóm không cùng domain |
| 8 | Hoàng Hưng | ETL fail/root cause | Data Engineer, DA/DS | Đọc log và trace lỗi thủ công | Workflow rõ nhưng nhóm không cùng domain |
| 9 | Mai Phương | Hệ thống chấm bài tự động hay báo lỗi chung chung  | Sinh viên CNTT, Học viên Online & Giảng viên  | Tự đọc từng dòng code mò lỗi không hỗ trợ (90 phút)  | F |
| 10 | Mai Phương | Tên môn học viết tắt gây khó hiểu trên Website  | Học viên mới (User chính), Đội ngũ Tư vấn viên/Sales (Actor phụ).  | Phải nhắn tư vấn viên giải thích lại (10 phút/khách  | Tên môn học/khóa học viết tắt hoặc ghi theo mã nội bộ trên website làm người dùng mới bối rối không biết môn học dạy nội dung gì, dẫn đến bỏ đi hoặc tốn thời gian hỏi bộ phận tư vấn.  |
| 11 | Thế Hưng | Tóm tắt ngữ cảnh & Gợi ý chuyên khoa | CSKH, Bệnh nhân | Bệnh nhân dừng nhắn 30-60 phút khiến CSKH phải lội lại lịch sử; bệnh nhân mô tả triệu chứng mơ hồ | Vướng rủi ro an toàn thông tin y tế và ranh giới tư vấn chuyên môn y khoa |
| 12 | Mai Phương | Học viên không tìm thấy tài liệu học  | Học viên (User chính), Trợ giảng/TA (Actor phụ xử lý câu hỏi).  | Lội tin nhắn & Nhắn hỏi TA (15 phút/lần)  | Học viên mất quá nhiều thời gian tìm tài liệu bị rải │ │ rác trên Zalo/Drive/LMS, gây trễ bài tập và quá tải cho TA.  |

## Gom trùng / cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| A - Học tập / tài liệu phân mảnh | Thông tin học tập phân mảnh, thiếu field bài nộp, tổng hợp deadline, tìm câu trả lời cũ trong Discord | Học viên phải tự tìm, đối chiếu và xác thực thông tin từ nhiều nguồn | Cluster sát bối cảnh lab nhất |
| B - FAQ / lịch hẹn | Tư vấn FAQ, đặt lịch khám, nhắc tái khám | Người dùng hỏi lặp lại và cần điều phối lịch | Có yếu tố y tế/privacy nên cần scope chặt |
| C - Planning cá nhân | Lên thực đơn, mua nguyên liệu | Gợi ý theo preference và constraint | Dễ prototype nhưng ít liên quan lab |
| D - Technical automation | Hệ thống chấm bài tự động, So sánh runtime để phát hiện performance regression, ETL fail | Đọc input kỹ thuật và đưa nhận định | Workflow rõ nhưng rủi ro quality hoặc domain |

## Shortlist

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| Thông tin học tập phân mảnh | Actor rõ, cả nhóm có trải nghiệm thật, dễ vẽ workflow trước/sau, có thể đo thời gian tìm tài liệu/deadline | Cần phân biệt bài toán tổ chức nguồn với bài toán AI search |
| Hệ thống chấm bài tự động | Giảm tải cho trợ giảng, workflow chấm bài rõ | Chất lượng chấm khó đo trong lab; nếu sai ảnh hưởng điểm học viên |
| Tư vấn FAQ và đặt lịch khám qua chat | Có pain lặp lại, có thể dùng rule/workflow | Domain y tế cần boundary và privacy nghiêm; nhóm ít bằng chứng trực tiếp |
| ETL fail/root cause | Bottleneck kỹ thuật rõ, metric thời gian tốt | Chỉ một vài thành viên hiểu domain; khó validate nhanh với cả nhóm |

## Shortlist và score

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Thông tin học tập phân mảnh | 5 | 4 | 4 | 5 | 4 | 5 | 4 | 31 |
| Hệ thống chấm bài tự động | 4 | 5 | 4 | 3 | 5 | 4 | 4 | 29 |
| Tư vấn FAQ và đặt lịch khám qua chat | 4 | 4 | 4 | 4 | 4 | 4 | 4 | 28 |
| Lên thực đơn | 4 | 4 | 3 | 4 | 5 | 4 | 4 | 28 |
| ETL fail/root cause | 4 | 5 | 3 | 5 | 5 | 3 | 3 | 28 |

Candidate nhóm chọn:

```text
Thông tin học tập phân mảnh trên Vlearn, Codelabs và Discord.
```

Vì sao chọn:

```text
Nhóm chọn candidate này vì cả nhóm đều hiểu workflow học tập hằng ngày, actor cụ thể là học viên VinAI thực chiến, pain có thể kiểm chứng nhanh bằng hỏi bạn học, và impact đo được bằng thời gian tìm đủ tài liệu/hướng dẫn/deadline. Bài toán cũng đủ tốt để so sánh No AI, Rule, Workflow và Agent mà không cần nhảy ngay sang agent phức tạp.
```

Vì sao không chọn các candidate còn lại:

```text
Hệ thống chấm bài tự động có impact nhưng rủi ro chất lượng cao vì điểm số ảnh hưởng trực tiếp tới học viên. Tư vấn khám bệnh có privacy và rủi ro domain y tế. Lên thực đơn dễ làm nhưng không sát bối cảnh lab. ETL fail có workflow rõ nhưng nhóm không có đủ bằng chứng/kinh nghiệm chung để validate trong thời gian lab.
```

---

# 02 - Quick Validation + Research

## Quick validation (expect)

Nhóm dùng quick interview/poll nhỏ với học viên quen biết. Các số liệu dưới đây là ước lượng ban đầu, cần kiểm chứng lại nếu triển khai thật.

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Quick interview | 100 học viên | 98/100 nói từng phải mở ít nhất 2-3 nguồn để tìm đủ lý thuyết, hướng dẫn thực hành, deadline hoặc câu trả lời cũ | 1 người nói đã tự bookmark link nên ít bị kẹt | Thu hẹp problem vào lúc học viên bắt đầu làm bài hoặc kiểm deadline, không nói chung chung "mọi thông tin học tập" |
| Mini poll trong lớp/nhóm chat | 80 phản hồi | 70/80 từng hỏi lại bạn/trợ giảng vì không chắc nguồn nào là mới nhất | Một số câu hỏi đến từ việc chưa đọc kỹ, không phải thiếu hệ thống | Thêm boundary: hệ thống chỉ tổng hợp nguồn chính thức, không thay học viên đọc nội dung |
| Quan sát chat/trao đổi lớp | Một số thread lặp lại | Có câu hỏi lặp về link bài, deadline, yêu cầu nộp, vị trí tài liệu | Chưa có log định lượng đầy đủ | Metric cần đo bằng số câu hỏi lặp lại trong pilot, không dùng claim quá mạnh |

Insight sau validation:

```text
Pain thật không chỉ là "có nhiều nền tảng". Pain nằm ở việc học viên không biết nguồn nào chứa thông tin chính thức, thông tin nào mới nhất, và phải tự đối chiếu Vlearn/Codelabs/Discord trước khi tiếp tục làm bài.
```

## Research giải pháp đã có

| Nguồn / tool / pattern | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Google Classroom - Classwork topics/materials | https://support.google.com/edu/classroom/answer/9093681 | Gom assignment/material theo topic | Có cấu trúc bài học, topic, due date, attachment | Không tự gom Discord/Vlearn/Codelabs hiện có của lớp | Rule/index theo topic là nền tảng tốt trước khi thêm AI |
| Google Classroom - assignments | https://support.google.com/edu/classroom/answer/6020265 | Assignment có instruction, due date, attachment, rubric | Giúp học viên thấy yêu cầu và deadline tại một chỗ | Chỉ tốt nếu toàn bộ lớp dùng Classroom làm nguồn chính | Nên chuẩn hóa metadata: bài học, deadline, link, rubric |
| Moodle resources | https://docs.moodle.org/500/en/Resources | Course có thể chứa file/link/resource theo bài | Phù hợp cho LMS và tài liệu chính thức | Không giải quyết tốt câu trả lời rải rác trong chat | Vlearn/Codelabs nên được index như resource chính thức |
| Discord Help Center / search pattern | https://support.discord.com/hc/en-us | Discord hỗ trợ tìm kiếm và help center | Tốt cho thảo luận và câu hỏi nhanh | Search theo keyword dễ bỏ sót context, thread cũ khó biết còn đúng không | Discord nên là nguồn bổ sung, không phải nguồn truth duy nhất |

Research takeaway:

```text
Không nên bắt đầu bằng một AI agent tự trả lời mọi câu hỏi học tập. Hướng hợp lý hơn là Workflow: chuẩn hóa nguồn chính thức và metadata bằng rule/process trước, sau đó dùng AI để tìm kiếm/tổng hợp trong phạm vi nguồn được phép, luôn kèm link nguồn để học viên kiểm tra.
```

---

# 03 - Workflow Before/After

## Current workflow bản nhóm

```text
CURRENT STATE - 7 bước, khoảng 25-40 phút khi bắt đầu làm bài mới

[1 Nhận thông tin có bài/buổi mới: 2']
-> [2 Mở Vlearn xem lý thuyết: 5']
-> [3 Mở Codelabs xem hướng dẫn thực hành: 8']
-> [4 Mở Discord tìm thông báo/câu trả lời: 10']
-> [5 Tự đối chiếu nguồn nào mới nhất: 8']  <-- bottleneck
-> [6 Hỏi bạn học/trợ giảng nếu chưa chắc: 5-10']
-> [7 Tiếp tục làm bài]
```

| Bước | Actor | Input | Output | Thời gian/tần suất | Ghi chú |
|---|---|---|---|---|---|
| 1 | Học viên | Thông báo có bài/buổi mới | Biết có việc cần làm | Mỗi buổi/bài | Có thể đến từ nhiều kênh |
| 2 | Học viên | Link Vlearn | Lý thuyết/nội dung bài | 5 phút | Nguồn học lý thuyết |
| 3 | Học viên | Link Codelabs | Hướng dẫn thực hành | 8 phút | Nguồn làm lab |
| 4 | Học viên | Discord channel/thread | Thông báo, Q&A, sửa lỗi | 10 phút | Search dễ lệch keyword |
| 5 | Học viên | Nội dung từ 3 nguồn | Kết luận về yêu cầu/deadline/source mới nhất | 8 phút | Bottleneck chính |
| 6 | Học viên, bạn học, trợ giảng | Câu hỏi chưa rõ | Câu trả lời bổ sung | 5-10 phút | Tạo câu hỏi lặp lại |
| 7 | Học viên | Thông tin đã đối chiếu | Bắt đầu/tiếp tục làm bài | - | Có thể vẫn thiếu thông tin |

Bottleneck chính:

```text
Học viên phải tự đối chiếu thông tin giữa Vlearn, Codelabs và Discord để biết nguồn nào là chính thức/mới nhất. Đây là bước tốn thời gian, gây chuyển đổi ngữ cảnh và tạo câu hỏi lặp lại cho trợ giảng.
```

## Future workflow bản nhóm

```text
FUTURE STATE - 6 bước, mục tiêu dưới 10-15 phút

[1 Giảng viên/trợ giảng xác nhận nguồn chính thức]
-> [2 Rule đồng bộ link + metadata vào trang tổng hợp]
-> [3 Học viên chọn môn/bài học]
-> [4 Xem tài liệu + hướng dẫn + deadline liên quan]
-> [5 AI hỗ trợ hỏi đáp trong nguồn được phép, kèm link nguồn]
-> [6 Học viên mở nguồn gốc để kiểm tra và làm bài]

Human boundary:
Giảng viên/trợ giảng là người quyết định tài liệu, yêu cầu và deadline chính thức.
AI không tự tạo deadline, không tự suy diễn yêu cầu bài, không trả lời nếu không tìm thấy nguồn.

Fallback:
Nếu không có nguồn hoặc các nguồn mâu thuẫn, hệ thống hiển thị cảnh báo và chuyển câu hỏi cho trợ giảng thay vì tự kết luận.
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Số bước | 7 | 6 | Không chỉ giảm bước, mà giảm chuyển đổi ngữ cảnh |
| Tổng thời gian tìm đủ thông tin | 25-40 phút | Dưới 10-15 phút | Đo bằng task tìm tài liệu + deadline của 1 bài |
| Số nền tảng phải mở ngay từ đầu | 3 | 1-2 | Trang tổng hợp là điểm bắt đầu, link gốc vẫn giữ |
| Câu hỏi lặp lại cho trợ giảng | Baseline đo trong 1 tuần | Giảm 30% trong pilot | Chỉ tính câu hỏi về link/deadline/yêu cầu bài |
| Bottleneck chính | Tự đối chiếu nhiều nguồn | Kiểm tra nguồn gốc khi có nghi ngờ | Human review vẫn tồn tại |
| Risk mới | Ít hallucination vì tự đọc nguồn | AI có thể tổng hợp sai hoặc dùng nguồn cũ | Bắt buộc kèm link nguồn và fallback |

---

# 04 - Problem Statement

## Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Học viên VinAI thực chiến, đặc biệt là học viên mới hoặc người chưa quen cấu trúc Vlearn/Codelabs/Discord. |
| **Workflow** | Khi bắt đầu làm bài, học viên mở Vlearn để đọc lý thuyết, Codelabs để xem hướng dẫn, Discord để tìm thông báo/câu trả lời, rồi tự đối chiếu nguồn nào mới nhất trước khi làm bài. |
| **Bottleneck** | Bước tự tìm và đối chiếu thông tin giữa nhiều nền tảng mất khoảng 25-40 phút/bài và dễ bỏ sót deadline hoặc hướng dẫn mới. |
| **Impact** | Học viên bị gián đoạn quá trình học, hỏi lại bạn/trợ giảng, có nguy cơ nộp thiếu yêu cầu hoặc dùng thông tin cũ. |
| **Success Metric** | Giảm thời gian tìm đủ tài liệu/hướng dẫn/deadline của một bài xuống dưới 10-15 phút; giảm 30% câu hỏi lặp lại về link/deadline/yêu cầu bài trong pilot; 100% câu trả lời tổng hợp có link nguồn chính thức. |
| **Boundary** | Không thay giảng viên/trợ giảng quyết định nội dung chính thức; không tự tạo deadline/yêu cầu bài; không trả lời nếu không tìm thấy nguồn; không dùng tin nhắn riêng tư hoặc dữ liệu ngoài phạm vi được phép. |

## Ma trận độ phù hợp với AI

Bài toán của nhóm nằm ở ô:

```text
Độ phức tạp cao, độ mơ hồ vừa đến cao.
```

Vì sao:

```text
Workflow có nhiều nguồn dữ liệu và nhiều bước: Vlearn, Codelabs, Discord, metadata bài học, deadline. Output có thể là câu trả lời/tóm tắt theo ngôn ngữ tự nhiên nên có độ mơ hồ. Tuy nhiên AI không cần tự lập kế hoạch dài hoặc tự quyết định hành động; vì vậy Workflow phù hợp hơn Agent ở scope pilot.
```

## Rule / Workflow / Agent

| Mức | Phương án cho bài toán nhóm | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **No AI / process fix** | Quy định một nguồn thông báo chính thức, checklist cho mỗi bài, naming convention thống nhất | Đủ nếu pain chủ yếu do thiếu quy ước | Vẫn phải tự search và đọc nhiều nguồn | Không chọn làm toàn bộ, nhưng cần làm nền |
| **Rule** | Trang index theo môn/bài với link Vlearn, Codelabs, deadline, rubric, Discord thread chính | Đủ nếu học viên chỉ cần link và deadline rõ | Không trả lời tốt câu hỏi tự nhiên như "bài này nộp gì?" hoặc "lỗi này xem thread nào?" | Dùng cho metadata/link chính thức |
| **Workflow** | Rule/index nguồn chính thức -> AI tìm trong nguồn được phép -> AI tổng hợp câu trả lời kèm link -> học viên kiểm tra nguồn | Hợp vì các bước rõ, AI chỉ hỗ trợ tìm/tổng hợp thông tin | AI có thể hiểu sai, dùng nguồn cũ hoặc tổng hợp thiếu | Chọn |
| **Agent** | Agent tự đọc nhiều nền tảng, tự quyết cần hỏi lại ai, tự cập nhật index/deadline | Chỉ cần nếu hệ thống phải tự điều phối nhiều tool và tự ra quyết định tiếp theo | Rủi ro permission, cập nhật sai thông tin chính thức, quá rộng cho lab | Chưa chọn |

Mức chọn:

```text
Workflow.
```

Vì sao chọn:

```text
Rule/index giải quyết phần nền là nguồn chính thức và metadata. AI hữu ích ở bước tìm kiếm bằng ngôn ngữ tự nhiên, tóm tắt nhiều nguồn và gợi ý link liên quan. Workflow giữ được boundary rõ: AI chỉ tổng hợp trong nguồn được phép, học viên kiểm tra link gốc, giảng viên/trợ giảng vẫn là owner của tài liệu và deadline.
```

Vì sao không chọn mức đơn giản hơn:

```text
No AI hoặc Rule có thể giảm nhiều pain nếu chỉ cần gom link, nhưng chưa hỗ trợ tốt các câu hỏi tự nhiên phát sinh khi học viên đang làm bài, ví dụ "deadline bài này ở đâu?", "yêu cầu nộp gồm những file nào?", hoặc "lỗi setup này đã có ai hỏi chưa?". Vì vậy nhóm chọn Workflow nhỏ, không chọn Agent.
```

## Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Học viên VinAI thực chiến, nhất là học viên mới bắt đầu làm bài hoặc cần kiểm tra lại hướng dẫn/deadline. |
| **Workflow** | Nhận bài mới -> mở Vlearn xem lý thuyết -> mở Codelabs xem hướng dẫn -> tìm Discord để đọc thông báo/Q&A -> tự đối chiếu nguồn mới nhất -> hỏi lại nếu chưa chắc -> làm bài. |
| **Bottleneck** | Tự đối chiếu thông tin giữa Vlearn, Codelabs và Discord mất khoảng 25-40 phút/bài, dễ bỏ sót hướng dẫn hoặc dùng thông tin cũ. |
| **Impact** | Học viên bị gián đoạn học tập, trợ giảng nhận câu hỏi lặp lại, deadline/yêu cầu nộp có nguy cơ bị hiểu sai. |
| **Success Metric** | Trong pilot 1-2 tuần, giảm thời gian tìm đủ tài liệu/hướng dẫn/deadline xuống dưới 10-15 phút/bài; giảm 30% câu hỏi lặp lại về link/deadline/yêu cầu; 100% câu trả lời AI có link nguồn chính thức. |
| **Boundary** | AI không tự tạo hoặc sửa deadline/yêu cầu bài; không trả lời ngoài nguồn được phép; không thay trợ giảng xác nhận thông tin mâu thuẫn; không đọc tin nhắn/private data không được cấp quyền. |
| **AI intervention point** | Sau khi link và metadata chính thức được chuẩn hóa, AI hỗ trợ search/tổng hợp câu trả lời từ Vlearn, Codelabs, Discord thread được chọn và luôn trả về link nguồn. |
| **Mức chọn** | Workflow: rule/index nguồn chính thức + AI Q&A/tóm tắt trong phạm vi nguồn được phép + học viên kiểm tra nguồn gốc. |
| **Rủi ro & người thật kiểm tra** | Risk: AI tổng hợp sai, dùng nguồn cũ, bỏ sót caveat. Người thật kiểm tra: học viên mở link nguồn; trợ giảng/giảng viên xác nhận metadata, deadline và xử lý trường hợp mâu thuẫn. |

---

# 05 - Final Decision

## Decision checklist

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | Yes | Actor là học viên VinAI; workflow trước/sau đã vẽ được |
| Baseline và success metric đã đo được chưa? | Not Yet | Có ước lượng 25-40 phút, cần đo thật trong pilot |
| Có data/input đủ dùng chưa? | Not Yet | Cần danh sách link Vlearn/Codelabs/Discord chính thức theo từng bài |
| Nếu AI sai, hậu quả có chấp nhận được không? | Yes, nếu có boundary | Vì AI chỉ gợi ý/tổng hợp, không tự quyết deadline hay yêu cầu bài |
| Có người review/owner vận hành không? | Yes | Giảng viên/trợ giảng owner metadata và thông tin chính thức |
| Có cách non-AI đơn giản hơn không? | Yes | Trang index/rule là bước đầu bắt buộc |

Decision:

```text
Go với scope nhỏ.
```

Lý do:

```text
Problem rõ, actor rõ, workflow hiện tại có bottleneck cụ thể và có metric đo được. Tuy nhiên nhóm không triển khai agent tự động toàn bộ. Pilot nên bắt đầu bằng index/rule cho nguồn chính thức, sau đó thêm AI Q&A/tóm tắt trong phạm vi nguồn được phép. Human boundary rõ nên rủi ro AI có thể kiểm soát.
```

Pilot nhỏ nhất:

```text
1. Chọn 1 môn hoặc 1 tuần học gần nhất.
2. Trợ giảng lập bảng metadata gồm: tên bài, link Vlearn, link Codelabs, deadline, yêu cầu nộp, Discord thread chính.
3. Cho 5-10 học viên thử tìm thông tin bằng workflow hiện tại và workflow mới.
4. Đo thời gian tìm đủ tài liệu/hướng dẫn/deadline.
5. Cho AI trả lời 5-10 câu hỏi thường gặp, bắt buộc kèm link nguồn.
6. Học viên/trợ giảng đánh dấu câu trả lời đúng, thiếu nguồn, dùng nguồn cũ hoặc cần escalate.
```

Exit / rollback:

```text
Nếu AI trả lời sai nguồn hoặc tự suy diễn deadline/yêu cầu bài quá 2 lần trong pilot, tắt phần AI Q&A và chỉ giữ trang index nguồn chính thức. Nếu học viên vẫn mất trên 20 phút để tìm thông tin sau pilot, cần sửa metadata/naming convention trước khi thêm AI.
```

Decision rationale:

- Bài toán không solution-first: bắt đầu từ actor, workflow, bottleneck và metric.
- Rule/process fix là nền tảng bắt buộc, AI chỉ thêm ở bước search/tổng hợp.
- Không chọn Agent vì chưa cần AI tự lập kế hoạch, tự cập nhật nguồn hoặc tự quyết thông tin chính thức.
- Boundary rõ: link/deadline/yêu cầu bài do giảng viên/trợ giảng xác nhận; AI luôn phải kèm nguồn.


# BÀI TẬP VẬN DỤNG CHUYÊN SÂU
## THIẾT KẾ GIẢI PHÁP PROMPTING ỨNG DỤNG THỰC TẾ CHO ỨNG DỤNG AI TRONG HỌC TẬP & NGHIÊN CỨU

**Họ và tên:** Võ Xuân Thịnh  
**Ngành:** Công nghệ thông tin  
**Lớp:** HCMKS26CNTT2  

---

# 1. Thiết kế giải pháp (Input/Output)

## 1.1. Tên giải pháp

**AI Study Assistant – Trợ lý AI hỗ trợ học tập và đánh giá bài làm.**

## 1.2. Mục đích

Xây dựng một giải pháp sử dụng AI để hỗ trợ sinh viên trong quá trình học tập và nghiên cứu. Hệ thống kết hợp Feynman Prompt và Rubric chấm bài tự động nhằm giúp sinh viên hiểu kiến thức, kiểm tra bài làm và cải thiện kết quả học tập.

Giải pháp gồm 2 chức năng chính:

- **Chức năng 1 – Feynman Prompt:** Giải thích kiến thức khó bằng ngôn ngữ đơn giản, có ví dụ thực tế và câu hỏi kiểm tra mức độ hiểu bài.
- **Chức năng 2 – Rubric chấm bài:** Phân tích bài làm, chấm điểm theo tiêu chí có sẵn, chỉ ra những phần còn thiếu và đề xuất cách cải thiện.

## 1.3. Input (Dữ liệu đầu vào)

Hệ thống cần nhận các thông tin sau:

| STT | Dữ liệu đầu vào | Mô tả |
|---|---|---|
| 1 | Môn học | Tên môn học cần hỗ trợ |
| 2 | Chủ đề | Kiến thức sinh viên muốn tìm hiểu |
| 3 | Câu hỏi | Nội dung cần AI giải thích |
| 4 | Bài làm | Nội dung bài tập sinh viên đã thực hiện |
| 5 | Đáp án hoặc tài liệu tham khảo | Dữ liệu dùng để đối chiếu nếu có |
| 6 | Rubric | Các tiêu chí và thang điểm đánh giá |
| 7 | Mức độ học tập | Cơ bản, trung bình hoặc nâng cao |

**Ví dụ Input:**

- Môn học: Nhập môn Công nghệ thông tin.
- Chủ đề: Trí tuệ nhân tạo (AI).
- Câu hỏi: AI là gì và được ứng dụng như thế nào trong cuộc sống?
- Bài làm: AI là công nghệ giúp máy tính thực hiện một số công việc cần trí thông minh của con người.
- Mức độ học tập: Cơ bản.

## 1.4. Output (Kết quả đầu ra)

Hệ thống cần trả về kết quả theo cấu trúc:

| STT | Kết quả | Nội dung |
|---|---|---|
| 1 | Giải thích kiến thức | Giải thích đơn giản, dễ hiểu |
| 2 | Ví dụ thực tế | Đưa ra ví dụ gần gũi |
| 3 | Câu hỏi kiểm tra | Kiểm tra mức độ hiểu bài |
| 4 | Điểm đánh giá | Điểm số theo Rubric |
| 5 | Nhận xét | Chỉ ra điểm tốt và điểm chưa tốt |
| 6 | Đề xuất cải thiện | Hướng dẫn sửa lỗi và bổ sung kiến thức |

---

# 2. Xây dựng Prompt hoàn chỉnh

## 2.1. Prompt 1 – Feynman Prompt gia sư

**Mục đích:** Giúp sinh viên hiểu kiến thức khó thông qua cách giải thích đơn giản.

**Prompt:**

Bạn là một gia sư AI có kinh nghiệm hướng dẫn sinh viên năm nhất ngành Công nghệ thông tin.

Nhiệm vụ của bạn là giải thích kiến thức theo phương pháp Feynman, nghĩa là sử dụng ngôn ngữ đơn giản, dễ hiểu để người mới bắt đầu cũng có thể tiếp thu.

**Thông tin đầu vào:**
- Môn học: [Tên môn học]
- Chủ đề: [Chủ đề cần học]
- Câu hỏi: [Câu hỏi của sinh viên]
- Trình độ: [Cơ bản/Trung bình/Nâng cao]

**Yêu cầu xử lý:**

1. Giải thích khái niệm bằng ngôn ngữ đơn giản.
2. Không sử dụng quá nhiều thuật ngữ chuyên ngành.
3. Nếu có thuật ngữ khó, phải giải thích ý nghĩa của thuật ngữ đó.
4. Đưa ra ít nhất một ví dụ thực tế.
5. Chỉ ra những lỗi hiểu sai thường gặp.
6. Đưa ra 3 câu hỏi ngắn để sinh viên tự kiểm tra kiến thức.

**Điều kiện xử lý lỗi:**

- Nếu thiếu tên môn học, hãy thông báo và yêu cầu bổ sung.
- Nếu thiếu chủ đề hoặc câu hỏi, không tự suy đoán mà yêu cầu sinh viên cung cấp.
- Nếu câu hỏi không rõ nghĩa, hãy hỏi lại để xác nhận.
- Nếu không chắc chắn về thông tin, phải nói rõ thay vì tự tạo ra câu trả lời.
- Nếu nội dung quá nâng cao, hãy chia nhỏ thành các phần dễ hiểu.

**Định dạng đầu ra:**

1. Khái niệm.
2. Giải thích dễ hiểu.
3. Ví dụ thực tế.
4. Lỗi thường gặp.
5. Ba câu hỏi kiểm tra kiến thức.

---

## 2.2. Prompt 2 – Rubric chấm bài tự động

**Mục đích:** Giúp sinh viên tự đánh giá bài làm trước khi nộp cho giảng viên.

**Prompt:**

Bạn là một trợ lý AI chuyên đánh giá bài tập học tập của sinh viên.

Nhiệm vụ của bạn là đọc bài làm và đánh giá dựa trên các tiêu chí Rubric được cung cấp. Không được chấm điểm theo cảm tính.

**Thông tin đầu vào:**
- Môn học: [Tên môn học]
- Đề bài: [Nội dung đề bài]
- Bài làm của sinh viên: [Nội dung bài làm]
- Rubric: [Các tiêu chí đánh giá]
- Tổng điểm: [Thang điểm]

**Tiêu chí đánh giá mặc định:**

| Tiêu chí | Điểm tối đa |
|---|---:|
| Đúng yêu cầu đề bài | 3 điểm |
| Nội dung chính xác | 3 điểm |
| Cách trình bày | 2 điểm |
| Ví dụ và tính ứng dụng | 2 điểm |
| **Tổng cộng** | **10 điểm** |

**Yêu cầu xử lý:**

1. Đọc và phân tích nội dung bài làm.
2. Đối chiếu từng tiêu chí trong Rubric.
3. Chấm điểm riêng cho từng tiêu chí.
4. Giải thích lý do đạt hoặc mất điểm.
5. Chỉ ra nội dung còn thiếu hoặc chưa chính xác.
6. Đề xuất cách sửa bài để đạt kết quả tốt hơn.

**Điều kiện xử lý lỗi:**

- Nếu bài làm bị trống, không được tự chấm điểm mà phải yêu cầu gửi lại.
- Nếu thiếu đề bài, thông báo chưa đủ dữ liệu để đánh giá chính xác.
- Nếu thiếu Rubric, sử dụng Rubric mặc định và thông báo rõ cho sinh viên.
- Nếu nội dung bài làm không liên quan đến đề bài, phải cảnh báo.
- Nếu dữ liệu bị sai định dạng, yêu cầu cung cấp lại.
- Không tự thêm thông tin để làm cho bài làm có vẻ đúng.
- Điểm số phải phù hợp với nhận xét và tiêu chí đánh giá.

**Định dạng đầu ra:**

1. Bảng điểm theo từng tiêu chí.
2. Tổng điểm.
3. Điểm mạnh của bài làm.
4. Những lỗi cần khắc phục.
5. Hướng dẫn cải thiện bài làm.

Lưu ý: Điểm do AI đưa ra chỉ mang tính tham khảo, giảng viên là người quyết định điểm chính thức.

---

# 3. Chạy thử Prompt và kết quả phản hồi của AI

## 3.1. Chạy thử Feynman Prompt

**Dữ liệu đầu vào:**

- Môn học: Nhập môn Công nghệ thông tin.
- Chủ đề: Trí tuệ nhân tạo (AI).
- Câu hỏi: AI là gì? Hãy giải thích và cho ví dụ thực tế.
- Trình độ: Cơ bản.

**Kết quả phản hồi của AI:**

### 1. Khái niệm

Trí tuệ nhân tạo (AI) là công nghệ giúp máy tính hoặc máy móc thực hiện những công việc thường cần đến trí thông minh của con người, chẳng hạn như nhận diện hình ảnh, hiểu ngôn ngữ và trả lời câu hỏi.

### 2. Giải thích dễ hiểu

Có thể hiểu đơn giản rằng AI giống như một người trợ lý thông minh. Khi chúng ta cung cấp dữ liệu và yêu cầu, AI có thể phân tích thông tin rồi đưa ra câu trả lời hoặc hỗ trợ thực hiện công việc.

### 3. Ví dụ thực tế

- ChatGPT: Hỗ trợ trả lời câu hỏi và giải thích kiến thức.
- Google Maps: Hỗ trợ tìm đường và lựa chọn tuyến đường.
- Nhận diện khuôn mặt: Giúp điện thoại nhận biết người dùng để mở khóa.

### 4. Lỗi thường gặp

Nhiều người nghĩ AI luôn đưa ra câu trả lời chính xác. Tuy nhiên, AI vẫn có thể hiểu sai câu hỏi hoặc tạo ra thông tin không chính xác. Vì vậy, người dùng cần kiểm tra lại thông tin quan trọng.

### 5. Câu hỏi kiểm tra kiến thức

1. AI là gì?
2. Hãy kể tên hai ứng dụng AI trong cuộc sống.
3. Vì sao chúng ta cần kiểm tra lại câu trả lời của AI?

---

## 3.2. Chạy thử Rubric chấm bài tự động

**Dữ liệu đầu vào:**

- Môn học: Nhập môn Công nghệ thông tin.
- Đề bài: Giải thích AI là gì và nêu các ứng dụng thực tế.
- Bài làm của sinh viên:

"AI là công nghệ giúp máy tính thực hiện những công việc thông minh giống con người. AI được ứng dụng trong ChatGPT để trả lời câu hỏi, Google Maps để tìm đường và nhận diện khuôn mặt để mở khóa điện thoại."

- Rubric: Sử dụng bảng tiêu chí mặc định gồm 4 tiêu chí, tổng 10 điểm.

**Kết quả phản hồi của AI:**

### 1. Bảng đánh giá

| Tiêu chí | Điểm tối đa | Điểm đạt |
|---|---:|---:|
| Đúng yêu cầu đề bài | 3 | 3 |
| Nội dung chính xác | 3 | 2.5 |
| Cách trình bày | 2 | 2 |
| Ví dụ và tính ứng dụng | 2 | 2 |
| **Tổng điểm** | **10** | **9.5** |

### 2. Điểm mạnh

- Bài làm trả lời đúng trọng tâm câu hỏi.
- Giải thích được khái niệm AI bằng ngôn ngữ đơn giản.
- Có các ví dụ thực tế và dễ hiểu.
- Trình bày ngắn gọn, không lan man.

### 3. Những điểm cần cải thiện

- Phần định nghĩa AI còn hơi đơn giản.
- Nên bổ sung ý AI có khả năng phân tích dữ liệu và học từ dữ liệu.
- Có thể giải thích rõ hơn cách AI hỗ trợ con người trong từng ứng dụng.

### 4. Đề xuất cải thiện

Sinh viên nên bổ sung thêm một câu giải thích về khả năng xử lý dữ liệu của AI để nội dung đầy đủ hơn.

**Kết quả đánh giá: 9.5/10 điểm.**

Lưu ý: Đây là điểm số mô phỏng theo Rubric đã cung cấp, không phải điểm chính thức của giảng viên.

---

# 4. Xử lý các trường hợp lỗi và dữ liệu không hợp lệ

| Trường hợp | Cách AI xử lý |
|---|---|
| Không nhập chủ đề | Yêu cầu sinh viên nhập chủ đề |
| Câu hỏi không rõ ràng | Đặt câu hỏi để xác nhận |
| Bài làm bị trống | Yêu cầu gửi lại bài làm |
| Thiếu đề bài | Thông báo chưa đủ dữ liệu để chấm |
| Thiếu Rubric | Sử dụng Rubric mặc định và thông báo |
| Bài làm sai chủ đề | Cảnh báo bài làm không đúng yêu cầu |
| Thông tin không chắc chắn | Nêu rõ mức độ chưa chắc chắn, không tự tạo dữ liệu |

**Ví dụ xử lý lỗi:**

Nếu sinh viên gửi yêu cầu chấm bài nhưng không có nội dung bài làm, AI sẽ phản hồi:

"Hiện tại bạn chưa cung cấp nội dung bài làm nên mình chưa thể đánh giá và chấm điểm. Vui lòng gửi bài làm để hệ thống có thể tiến hành phân tích."

---

# 5. Đánh giá hiệu quả giải pháp

| Tiêu chí | Hiệu quả mong đợi |
|---|---|
| Tiết kiệm thời gian | Giảm thời gian tìm hiểu và kiểm tra bài |
| Hỗ trợ học tập | Giúp sinh viên hiểu kiến thức dễ hơn |
| Tự đánh giá | Biết được điểm mạnh và điểm yếu của bài làm |
| Cải thiện kiến thức | Có hướng dẫn sửa lỗi cụ thể |
| Xử lý dữ liệu lỗi | Hạn chế việc AI trả lời khi thiếu thông tin |

**Ưu điểm:**
- Dễ sử dụng và phù hợp với sinh viên.
- Có thể áp dụng cho nhiều môn học.
- Kết hợp được học kiến thức và đánh giá bài tập.
- Có các điều kiện xử lý dữ liệu thiếu hoặc sai lệch.

**Hạn chế:**
- AI có thể đánh giá chưa chính xác trong một số trường hợp.
- Kết quả phụ thuộc vào chất lượng dữ liệu đầu vào.
- Cần có Rubric rõ ràng để việc chấm điểm khách quan hơn.
- Không nên sử dụng kết quả AI thay thế hoàn toàn đánh giá của giảng viên.

---

# 6. Kết quả đạt được

Thông qua bài tập, em đã xây dựng được giải pháp AI Study Assistant kết hợp Feynman Prompt và Rubric chấm bài tự động.

Giải pháp giúp sinh viên hiểu kiến thức khó bằng cách giải thích đơn giản, đồng thời hỗ trợ kiểm tra bài làm theo các tiêu chí cụ thể.

Qua quá trình thiết kế và chạy thử, em hiểu được cách xác định dữ liệu đầu vào, xây dựng cấu trúc đầu ra, viết Prompt có điều kiện xử lý lỗi và kiểm tra kết quả phản hồi của AI.


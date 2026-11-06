# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Trạng thái báo cáo: chưa hoàn tất. Notebook hiện có chưa chạy hết và chưa có output để xác nhận các số liệu cuối.

- **SEED:** 1866

## 1. Bằng chứng

| Tệp cần nộp trong `report/individual/` | Trạng thái |
| --- | --- |
| `2A202604076_DaoHongThang.md` — báo cáo cá nhân đã đổi tên | Có |
| `day01_lab.ipynb` — notebook đã chạy hết, còn output, đã điền câu trả lời | Chưa có trong thư mục |
| `lab1_report.json` — do ô “Báo cáo cuối” sinh ra | Chưa có |
| `hand_calc.jpg` — ảnh tính tay thấy rõ các bước | Chưa có |

Notebook làm việc hiện nằm ở `src/day01_spam_ml_dl_embedding_llm.ipynb`; cần chạy hoàn tất và đặt bản nộp vào `report/individual/`.

## 2. Kết quả chính

Chưa thể ghi bảng kết quả: notebook chưa chạy ô “Báo cáo cuối” và không có output kết quả để đối chiếu. Sau khi chạy notebook, chép số liệu thực tế vào bảng:

| Mô hình | F1 test | F1 SUB 40 | p95 ms/tin | USD/1k tin |
| --- | ---: | ---: | ---: | ---: |
| BoW + Logistic Regression | Chưa có | Chưa có | Chưa có | — |
| BoW + MLP | Chưa có | Chưa có | Chưa có | — |
| Embedding | Chưa có | Chưa có | Chưa có | — |
| LLM | Chưa có | Chưa có | Chưa có | Chưa có |

## 3. Dự đoán và thực tế

Chưa hoàn thành. Notebook chưa có đủ kết quả chạy để so sánh. Ghi lại ba dự đoán `predict(...)` lệch nhiều nhất sau khi chạy:

| Dự đoán | Kết quả thực tế | Vì sao lệch |
| --- | --- | --- |
| Cần bổ sung | Cần bổ sung | Cần phân tích |
| Cần bổ sung | Cần bổ sung | Cần phân tích |
| Cần bổ sung | Cần bổ sung | Cần phân tích |

## 4. Phân tích 50 case khó

Trong phần trả lời notebook, nhận xét rằng BoW và MLP giảm F1 nhiều hơn trên tập khó; các nhóm “Né từ khoá” và “Spam giọng tự nhiên” khó với BoW, còn “Prompt Injection” có thể đánh lừa LLM. Chuẩn hoá văn bản có thể giúp BoW nhận diện biến thể từ, nhưng cần cân nhắc độ trễ và nguy cơ nhận diện nhầm.

Phần chạy stress test chưa có output. Cần bổ sung số liệu theo từng nhóm và nêu hai tin nhắn cụ thể mà mô hình dự đoán sai cùng nguyên nhân; hiện chưa có cơ sở để khẳng định mô hình nào tụt nhiều nhất.

## 5. Thử thách cá nhân

Với SEED 1866, đề được chọn là **thử thách #1**: đổi ngưỡng quyết định của Logistic Regression từ 0.5 sang 0.2 và 0.8, báo precision/recall/F1 tại từng ngưỡng, rồi giải thích lựa chọn phù hợp nếu ngân hàng muốn tránh chặn nhầm tin OTP.

Ô code thử thách trong notebook đang để trống và chưa chạy. Cần bổ sung cách làm, kết quả thực tế và giải thích.

## 6. Phương án cho sản phẩm thật

Yêu cầu: lọc 10 triệu SMS/ngày với p95 < 50 ms/tin. Chưa chọn phương án vì bảng đo p95, F1 và chi phí của notebook chưa có kết quả. Sau khi chạy, chọn phương án dựa trên số liệu thực tế, nêu rõ đánh đổi về chất lượng, độ trễ và chi phí; nếu dùng LLM, ước tính chi phí tháng từ USD/1k tin.

## 7. AI log và điều đã học

| Phần | Bạn hỏi AI gì (prompt) | AI trả lời/viết gì | Bạn đã sửa / kiểm chứng gì |
| --- | --- | --- | --- |
| Hoàn thiện report | Đối chiếu báo cáo với hướng dẫn nộp và nội dung notebook | Sắp xếp báo cáo theo các mục yêu cầu, chỉ ra nội dung và tệp còn thiếu | Đối chiếu SEED và trạng thái các ô trong notebook; không tự điền số liệu khi chưa có output |

Điều đã học:

1. Nếu dữ liệu trùng lặp xuất hiện ở cả train và test, điểm đánh giá có thể cao hơn thực tế vì mô hình đã gặp những tin đó khi huấn luyện; đây là data leakage.
2. Với dữ liệu nhãn mất cân bằng, chỉ nhìn accuracy có thể gây hiểu nhầm; cần xem thêm precision, recall và F1 để hiểu rõ lỗi bỏ sót spam và chặn nhầm tin thường.

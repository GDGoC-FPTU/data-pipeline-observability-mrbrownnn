# Báo Cáo Thí Nghiệm: Tác Động Của Chất Lượng Dữ Liệu Đến AI Agent

**Student ID:** AI20K-XXXX
**Name:** (Điền tên của bạn)
**Date:** (Điền ngày thực hiện)

---

## 1. Kết Quả Thí Nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Phản hồi chính xác; sản phẩm và giá phù hợp với dữ liệu hợp lệ |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 2 | Outlier cực đoan (giá = 999999) khiến Agent đề xuất một sản phẩm vô lý |

---

## 2. Phân Tích & Nhận Xét (Phan tich & nhan xet)

### Tại Sao Agent Trả Lời Sai Khi Dùng Garbage Data? (Tai sao Agent tra loi sai?)

Khi sử dụng dữ liệu sạch (clean data), ETL pipeline đã loại bỏ các bản ghi có giá âm, giá bằng 0, và category rỗng. Kết quả là Agent chỉ làm việc với dữ liệu hợp lệ, đưa ra câu trả lời chính xác và có nghĩa.

Tuy nhiên, khi Agent nhận dữ liệu "rác" (garbage data), có nhiều vấn đề nghiêm trọng ảnh hưởng đến chất lượng phản hồi:

1. **Duplicate IDs**: Bản ghi có id=1 xuất hiện hai lần (Laptop và Banana), gây nhầm lẫn về tính duy nhất của dữ liệu.
2. **Wrong data types**: Trường `price` của "Broken Chair" có giá trị là chuỗi "ten dollars" thay vì số, khiến phép tính số học bị lỗi.
3. **Extreme outliers**: "Nuclear Reactor" có giá $999,999 - đây là giá trị bất thường quá mức, khiến Agent chọn nó là "best deal" dù không có ý nghĩa thực tế.
4. **Null values**: Bản ghi "Ghost Item" có id và category là None, gây lỗi khi xử lý.

Tất cả những vấn đề trên chứng minh rằng: dữ liệu kém chất lượng sẽ khiến AI Agent đưa ra kết quả sai lệch hoặc vô nghĩa, bất kể prompt có tốt đến đâu. Đây chính là nguyên nhân tại sao observability và data quality là nền tảng của bất kỳ hệ thống AI nào.

---

## 3. Kết Luận

**Quality Data > Quality Prompt?** - **Đồng ý.**

Dù có viết prompt tốt đến đâu, nếu dữ liệu đầu vào chứa đầy sai lệch, trùng lặp và outlier thì Agent vẫn cho ra kết quả sai. Pipeline ETL với validation chặt chẽ là bước không thể thiếu để bảo đảm độ chính xác của hệ thống AI. Data quality là nền tảng, prompt chỉ là công cụ bổ trợ.

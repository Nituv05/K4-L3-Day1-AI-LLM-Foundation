# K4 — Ngày 1: Bài Tập & Phản Ánh
## Khám Phá LLM API | Phiếu Thực Hành

**Thời lượng:** 4 tiếng
**Cách làm:** Trả lời từng câu ngay sau khi hoàn thành block tương ứng —
đừng để dồn hết về cuối buổi. Thay dòng `*Câu trả lời của bạn*` bằng câu
trả lời thật (chấm tự động sẽ đếm số câu đã trả lời).

---

## Block 1 — API Cơ Bản (trả lời sau Checkpoint 1)

### Câu 1.1 — Độ nhạy của temperature
Gọi `call_openai` với temperature 0.0, 0.5, 1.0 và 1.5 dùng prompt
**"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**


## Temperature = 0.0

```text
Here's a thinking process:

1. Analyze User Request:
   - User asks: "Hãy kể cho tôi một sự thật thú vị về Việt Nam."
     (Tell me an interesting fact about Vietnam.)
   - Language: Vietnamese
   - Goal: Provide one interesting, accurate, and engaging fact about Vietnam.

2. Identify Key Constraints:
   - Must be a "fact" (true, verifiable)
   - Should be "interesting" (engaging, surprising, culturally/naturally significant)
   - Language: Vietnamese
   - Format: Just tell the fact (no need for excessive structure, but should be clear)

3. Brainstorm Potential Facts About Vietnam:
   - Longest coastline in Southeast Asia? Actually, it's very long, but maybe not the longest.
   - World's largest pig producer? No, China is.
   - Oldest tree? Not particularly famous.
   - Bát Tràng pottery village? Good, but maybe not "wow" fact.
   - Vietnam has 8 UNESCO World Heritage Sites? Yes, that's good.
   - The country is shaped like an 'S'? Cliché.
   - Vietnam has the most diverse ecosystem in
```

## Temperature = 0.5

```text
Here's a thinking process:

1. Analyze User Request:
   - User asks: "Hãy kể cho tôi một sự thật thú vị về Việt Nam."
     (Tell me an interesting fact about Vietnam.)
   - Language: Vietnamese
   - Content: An interesting fact about Vietnam

2. Identify Key Constraints:
   - Must be a fact about Vietnam
   - Should be "thú vị" (interesting/curious)
   - Must be in Vietnamese (implied by the prompt language)
   - No specific format required, just a fact

3. Brainstorm Potential Facts About Vietnam:
   - Vietnam has the world's largest cave (Son Doong)
   - It's one of the few countries with a "flag language" or unique national flag symbolism
   - It has the most motorbikes per capita
   - The country is shaped like an 'S'
   - It has a very young population demographic
   - Vietnamese language has 6 tones (unique feature)
   - It's one of the world's largest rice exporters
   - The ancient town of Hoi An has a unique lighting tradition
   - Vietnam has a "water puppet theater" (unique art
```

## Temperature = 1.0

```text
Here's a thinking process:

1. Analyze User Request:
   - User asks: "Hãy kể cho tôi một sự thật thú vị về Việt Nam."
     (Tell me an interesting fact about Vietnam.)
   - Language: Vietnamese
   - Topic: Interesting fact about Vietnam
   - Goal: Provide a engaging, accurate, and interesting fact

2. Identify Key Information Needed:
   - Must be about Vietnam
   - Should be "thú vị" (interesting/fascinating)
   - Should be factual
   - Language should be Vietnamese

3. Brainstorm Potential Facts about Vietnam:
   - Longest cave system (Son Doong)
   - Rice terraces (Sapa, Hoàng Liên Son)
   - Ao dai & non la
   - Motorcycles per capita
   - Biodiversity (one of top 16)
   - Water puppetry
   - First country to adopt daylight saving time in Asia? (Maybe not well-known)
   - Bánh mì & pho origins
   - Vietnam has 54 ethnic groups
   - Oldest tree or temple
   - Motorbike traffic stats
   - First Southeast Asian country to... etc
```

## Temperature = 1.5

```text
Here's a thinking process:

1. Analyze User Request:
   - User wants a "fun/v fascinating fact about Vietnam"
     ("một sự thật thú vị về Việt Nam")
   - Language: Vietnamese
   - Need to provide an interesting, accurate fact

2. Identify Key Requirements:
   - Must be about Vietnam
   - Must be "thú vị" (fun/fascinating)
   - Must be accurate
   - Should be concise but engaging

3. Brainstorm Potential Facts About Vietnam:
   - Longest coastal line in Asia? Actually, Philippines has longer, Vietnam is up there.
   - Tet celebration, food, etc.
   - Mỹ Sơn, Halong Bay, etc.
   - Specific interesting facts:
     * Vietnam has a "Young" population median age ~32
     * It's one of the few countries where the morning sun rises in the east and sets in the west? No, that's everywhere.
     * The Imperial City of Hue was the capital of Nguyen Dynasty
     * Vietnam has 54 ethnic groups
     * It's the world's largest exporter of cashew nuts and pepper
     * The Nguyen Dynasty had complex royal customs
```


**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng từ 0.0 lên 1.5, nội dung phản hồi có xu hướng đa dạng hơn và xuất hiện nhiều ý tưởng khác nhau hơn. Ở temperature thấp, câu trả lời ổn định và tập trung hơn, còn ở temperature cao, model sáng tạo hơn nhưng cũng dễ đưa ra các ý kém chắc chắn hoặc lan man hơn.



### Câu 1.2 — Chọn temperature cho sản phẩm
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ chọn temperature khoảng **0.2–0.4** cho chatbot hỗ trợ khách hàng vì cần ưu tiên câu trả lời ổn định, nhất quán và ít bịa thông tin. Mức này vẫn giữ được một chút linh hoạt trong cách diễn đạt nhưng hạn chế việc model trả lời quá sáng tạo hoặc lệch khỏi nội dung hỗ trợ.



### Câu 1.3 — Đánh đổi chi phí
Kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người gọi API 3 lần,
mỗi lần trung bình ~350 token đầu ra.

> Với workload này, tổng lượng đầu ra là **10.500.000 token/ngày**. Theo bảng giá trong bài, GPT-4o tốn khoảng **105 USD/ngày**, còn GPT-4o-mini khoảng **6,3 USD/ngày**, nên GPT-4o đắt hơn khoảng **16,67 lần**.
GPT-4o xứng đáng với chi phí trong các tác vụ phức tạp cần chất lượng suy luận và độ chính xác cao, chẳng hạn phân tích tài liệu hoặc xử lý yêu cầu nhiều bước. GPT-4o-mini phù hợp hơn với các tác vụ đơn giản, khối lượng lớn như FAQ, phân loại hoặc chatbot hỗ trợ khách hàng cơ bản để tiết kiệm chi phí.

---

## Block 2 — System Prompt & Token (trả lời sau Checkpoint 2)

### Câu 2.1 — Sức mạnh của persona
Gọi `chat_with_system_prompt` hai lần với cùng câu hỏi
**"Giải thích blockchain là gì?"** nhưng hai system prompt khác nhau:
- "Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi."
- "Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật."

**Hai phản hồi khác nhau như thế nào (độ dài, từ vựng, ví dụ)? System prompt
ảnh hưởng đến hành vi model ra sao?** (3–4 câu)

Ở persona **giáo viên tiểu học**, model định hướng câu trả lời theo cách đơn giản, phù hợp với trẻ 8 tuổi. Cụ thể, phần output ghi:

> “Identify Key Concepts of Blockchain:
>
> * Digital ledger/book
> * Blocks of information
> * Linked together like a chain
> * Distributed/shared (many copies)
> * Secure/tamper-proof (hard to change)
> * No single owner/central authority (decentralized)
> * Often used for cryptocurrency, but can track other things”

Sau đó model còn chủ động chuyển các khái niệm này sang ví dụ gần gũi với trẻ em:

> “Translate to 8-Year-Old Concepts:
>
> * School notebook/lunchroom example
> * Sharing snacks/stickers
> * Drawing pictures that everyone has a copy of
> * Once written, can't easily erase/change without everyone noticing
> * Everyone keeps their own copy, and they all check each other”

Model bắt đầu xây dựng câu giải thích theo hướng:

> “Blockchain is like a digital notebook that lots of people have. When something new happens, it gets”

Trong khi đó, với persona **chuyên gia tài chính**, output không tạo được một phần giải thích blockchain có ý nghĩa mà bị lỗi generation với chuỗi lặp:

> “Here's a thinking process:
>
> 1. **Analyze Useruti deepseekells:**
>    ellsellsellsells-sells deep network affordells overtells where subject overtells'ells mill repr/dellsells of along thisellsellsellsellsellsellsells c overtellsellsellsellsellsellsellsellsellsellsellsellsells inellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsellsel


### Câu 2.2 — tiktoken vs đếm từ
Chọn một đoạn văn tiếng Việt ~100 từ. So sánh số token theo `count_tokens`
(tiktoken) với ước lượng `số từ / 0.75` mà Part 1 đã dùng.

> Với đoạn văn 119 từ, cách ước lượng `số từ / 0.75` cho khoảng **158.67 token**, trong khi `count_tokens` cho **135 token**, chênh lệch khoảng **14.92%**. Tiếng Việt thường tốn nhiều token hơn tiếng Anh cùng độ dài vì một từ tiếng Việt có thể được tách thành nhiều token nhỏ hơn do dấu thanh, ký tự Unicode và cách tokenizer được huấn luyện, trong khi nhiều từ tiếng Anh phổ biến thường được mã hóa gọn hơn.

---

## Block 3 — Streaming & Độ Bền (trả lời sau Checkpoint 3)

### Câu 3.1 — Trải nghiệm người dùng với streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì
non-streaming lại phù hợp hơn?** (1 đoạn văn)


```text
Giải thích machine learning là gì và cho tôi một ví dụ đơn giản.
**Machine Learning (Học máy)** là một nhánh của Trí tuệ nhân tạo (AI) cho phép máy tính **học từ dữ liệu** để đưa ra dự đoán hoặc ra quyết định, mà **không cần được lập trình theo từng bước cụ thể** cho mọi tình huống.

### 🔍 Khác nhau so với lập trình truyền thống

| Lập trình truyền thống | Học máy (Machine Learning) |
| :--- | :--- |
| Người viết **các quy tắc rõ ràng** (nếu A thì B) | Cung cấp **dữ liệu** cho máy, máy tự tìm ra quy tắc |
| Phù hợp khi logic rõ ràng, ít trường hợp | Phù hợp khi có nhiều dữ liệu, logic phức tạp hoặc không rõ ràng |
| Ví dụ: "Nếu email chứa từ 'miễn phí' → đánh rác" | Máy tự học: "Từ 'miễn phí' thường xuất hiện trong email rác, nhưng cũng có trong newsletter → cần xem thêm các từ khác" |

---

### 🌟 Ví dụ đơn giản: Dự đoán giá nhà

Giả sử bạn muốn máy tính **đoán giá một căn nhà** chỉ dựa trên diện tích (m²).

**Dữ liệu bạn đưa cho máy:**
| Diện tích (m²) | Giá (triệu đồng) |
| :--- | :--- |
| 50 | 10 |
| 100 | 20 |
| 150 | 30 |

**Thay vì ai đó viết công thức phức tạp**, bạn đưa các cặp số này vào thuật toán học máy. Máy sẽ tự nhận ra quy luật: *"Nhìn chung, mỗi tăng 1 m², giá nhà tăng khoảng 0,2 triệu"*.

**Khi có một ngôi nhà mới diện tích 200m²**, máy có thể **dự đoán** giá khoảng **40 triệu đồng** — chỉ dựa trên xu hướng đã "học" từ dữ liệu cũ, mà không ai đã từng ghi rõ "công thức giá = diện tích × 0,2".

---

### 📚 Một số loại học máy phổ biến (cắtgem)

1. **Học có giám sát (Supervised Learning):** Có dữ liệu có "đáp án đúng".  
   *Ví dụ:* Phát hiện thư rác (spam) – mỗi email đã được gắn nhãn "rác/không rác", máy học cách phân loại email mới.

2. **Học không giám sát (Unsupervised Learning):** Không có đáp án, máy tự tìm pattern.  
   *Ví dụ:* Phân nhóm khách hàng theo hành vi mua hàng giống nhau, mà không cần ai định nghĩa nhóm trước.

3. **Học tăng verstär (Reinforcement Learning):** Học bằng "thưởng/hình phạt".  
   *Ví dụ:* Trò chơi cờ AlphaGo, robot dây chuyền tự điều chỉnh.

---

### 💡 Tóm tắt dễ hiểu
Học máy giống như **dạy con nhậnbuah bằng ảnh minh họa** thay vì đọc quy tắc sách vở: bạn cho con thấy nhiều bức táo và cam, con tự học rằng "đỏ + tròn thường là táo", và sau đó con có thể nhận đúng táo ngay khi thấy một quả mới.

Bạn đang quan tâm đến lĩnh vực nào cụ thể (xử lý ngôn ngữ, nhận diện hình ảnh, phân tích dữ liệu...) để mình ví dụ sâu hơn?
```

**Nhận xét:**

> Streaming đặc biệt quan trọng với chatbot hoặc các phản hồi dài vì người dùng có thể thấy nội dung xuất hiện dần ngay khi model sinh ra, thay vì phải chờ toàn bộ phản hồi hoàn tất. Trong thử nghiệm trên, câu trả lời được hiển thị lần lượt từ phần định nghĩa, bảng so sánh, ví dụ dự đoán giá nhà đến phần phân loại và tóm tắt, nên trải nghiệm phản hồi nhanh và tự nhiên hơn. Ngược lại, non-streaming phù hợp hơn khi chương trình cần nhận toàn bộ response trước khi xử lý tiếp, chẳng hạn parse JSON, kiểm tra định dạng hoặc lưu kết quả hoàn chỉnh.



### Câu 3.2 — Vì sao backoff theo cấp số nhân?
>Exponential backoff giúp giảm tải cho API bằng cách tăng dần thời gian chờ sau mỗi lần thất bại, như kết quả của tôi: **0.1s → 0.2s → 0.4s → 0.8s**. So với delay cố định, cách này cho hệ thống thêm thời gian phục hồi và giảm số request retry dồn dập. Nếu hàng nghìn client cùng retry sau đúng một khoảng thời gian cố định, chúng có thể gửi lại request gần như đồng thời, tạo ra một đợt tải mới và khiến API tiếp tục quá tải.

---

## Block 4 — Mini-Project (trả lời sau Checkpoint 4)

### Câu 4.1 — Thiết kế persona
**Bạn chọn persona gì cho trợ lý của mình? Viết lại system prompt đó và giải
thích 1–2 lựa chọn từ ngữ quan trọng trong prompt (ví dụ: vì sao yêu cầu
"trả lời ngắn gọn", vì sao chỉ định ngôn ngữ...):**

**System prompt sử dụng:**

> `Bạn là trợ giảng thân thiện của khóa AI, trả lời ngắn gọn bằng tiếng Việt.`


```text
API (Application Programming Interface) là một bộ giao thức và quy tắc cho phép hai ứng dụng phần mềm giao tiếp với nhau. Nó đóng vai trò như một **"người trung gian"**: ứng dụng A gửi yêu cầu, API xử lý và trả kết quả cho ứng dụng B, mà không cần biết code bên trong nhau hoạt động ra sao.

Ví dụ đơn giản: khi bạn xem dự báo thời tiết trên điện thoại, API giúp ứng dụng "nhắn" cho dịch vụ dữ liệu thời tiết để lấy thông tin và hiện lên màn hình. Các trường hợp phổ biến khác: đăng nhập bằng Google/Facebook, thanh toán qua VNPay/GrabPay, hoặc kết nối app với dịchierelay.
```

**Nhận xét:**

> Tôi chọn persona **“trợ giảng thân thiện của khóa AI”** để model trả lời theo phong cách dễ hiểu và phù hợp với người đang học các khái niệm AI/API. Cụm **“trả lời ngắn gọn”** giúp hạn chế câu trả lời quá dài và tập trung vào ý chính, còn **“bằng tiếng Việt”** giúp duy trì ngôn ngữ thống nhất với người dùng. Kết quả thực nghiệm cho thấy model giải thích API bằng cách dùng hình ảnh **“người trung gian”** và đưa ra ví dụ thực tế như ứng dụng thời tiết, đăng nhập Google/Facebook và thanh toán điện tử.

### Câu 4.2 — Hạn chế & cải thiện
**Trợ lý của bạn hiện có hạn chế lớn nhất là gì (ví dụ: history chỉ 3 lượt,
không có bộ nhớ dài hạn, không kiểm duyệt nội dung...)? Đề xuất một cải
thiện cụ thể và mô tả ngắn cách triển khai:**

**Input thử nghiệm:**

```text
Lượt 1: Nhớ: BANANA.
Lượt 2: API?
Lượt 3: Token?
Lượt 4: AI?
Lượt 5: Từ khóa đầu tiên?
```

**Output thử nghiệm:**

```text
Lượt 1
Input: Nhớ: BANANA.
Output: Tôi nhớ chuối hôm qua.

Lượt 2
Input: API?
Output: Tôi hỗ trợ API.

Lượt 3
Input: Token?
Output: Tôi hỗ trợ token.

Lượt 4
Input: AI?
Output: Tôi là AI.

Lượt 5
Input: Từ khóa đầu tiên?
Output: Tôi là [AI
```

**Thống kê cuối phiên:**

```text
{
    'num_turns': 5,
    'total_tokens': 26,
    'total_cost': 0.00018500000000000002,
    'history': [
        {'role': 'user', 'content': 'Token?'},
        {'role': 'assistant', 'content': 'Tôi hỗ trợ token.'},
        {'role': 'user', 'content': 'AI?'},
        {'role': 'assistant', 'content': 'Tôi là AI.'},
        {'role': 'user', 'content': 'Từ khóa đầu tiên?'},
        {'role': 'assistant', 'content': 'Tôi là [AI'}
    ]
}
```
**Nhận xét**: 
> Hạn chế lớn nhất của trợ lý hiện tại là **chỉ giữ 3 lượt hội thoại gần nhất**, vì `history` bị cắt còn 6 message. Kết quả trên cho thấy input đầu tiên chứa từ khóa **“BANANA”** đã bị loại khỏi `history`; vì vậy đến lượt 5, khi hỏi lại **“Từ khóa đầu tiên?”**, model không còn đủ ngữ cảnh để trả lời chính xác và sinh ra câu sai `"Tôi là [AI"`. Một cải thiện cụ thể là **tóm tắt các lượt hội thoại cũ và giữ phần summary trong context** thay vì xóa hoàn toàn. Cách này giúp giảm số token nhưng vẫn bảo toàn các thông tin quan trọng cần nhớ lâu dài.

---

## Danh Sách Kiểm Tra Nộp Bài

- [ ] `python grade.py` — xem điểm tự động, mục tiêu ≥ 75/100
- [ ] Cả 4 checkpoint pytest đều pass
- [ ] Tất cả 9 câu trong file này đã được trả lời
- [ ] Đã copy bài làm vào folder `solution/`, push lên fork và dán link trên trang bài Lab ở VLearn trước 23:59 ngày 11/09/2026

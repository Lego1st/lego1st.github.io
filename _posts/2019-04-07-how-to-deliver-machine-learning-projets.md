---
layout: post
title:  "Hướng triển khai cho các project Machine Learning"
subtitle: "Định hướng vòng lặp ML Engineering"
date:   2019-04-07 14:00:00 +0700
categories: []
---

> Build only what you need to build, and do it fast

Với sự phát triển không ngừng của công nghệ, đâu đâu người ta cũng nhắc tới Cách mạng công nghiệp 4.0, thì có thể nói Học máy (Machine Learning) đã trở thành một cái tên không còn xa lạ trong giới công nghiệp. Cùng với nhu cầu ngày càng nhiều của xã hội, một ngành mới được ra đời, Kĩ sư Học máy (Machine Learning Engineers). 

Kĩ sư Học máy có tổ hợp kĩ năng về Học máy và kĩ thuật phần mềm (Software Engineering). Một Kĩ sư Học máy là người có thể sử dụng các kĩ năng của mình để tìm ra các mô hình học máy có hiệu suất cao đem vào ứng dụng và cũng là người xử lý các vấn đề từ cơ sở hạ tầng phục vụ huấn luyện cho đến tạo ra mô hình áp dụng thực tế. Có kha khá nguồn tài liệu trên mạng để một Kỹ sư phần mềm hay bất cứ ai học về Học máy. Tuy nhiên, trong thực tế, một đội ngũ làm Học máy sẽ phải đối mặt với một vấn đề: Làm sao để có thể quản lý các tiến trình của dự án như các dự án phần mềm truyền thống ? Sau đây là bài viết trả lời cho câu hỏi đó.

## The ML Engineering Loop 

Trong bài viết này, chúng mình sẽ cùng tìm hiều về khái niệm "OODA Loop" của Học máy: ML Engineering Loop, với khái niệm này chúng mình sẽ tuần tự theo các bước

1. Phân tích (Analyze)
2. Chọn phương pháp (Select an approach)
3. Thực thi (Implement)
4. Đo đạc (Measure)

để có thể tìm ra được mô hình học máy hiệu quả một cách nhanh chóng. Đối với mỗi giai đoạn sẽ có những lời khuyên mà tác giả nghĩ có thể giúp tối ưu được toàn bộ quá trình. 

![](https://cdn-images-1.medium.com/max/2400/1*OILsPq8hrosFVjXwnOoo-Q.png)

Một đội ngũ ML thành công khi triển khai được một mô hình có hiệu suất cao với những rằng buộc đã cho (ví dụ: đạt độ chính xác cao nhưng vẫn phải đảm bảo về bộ nhớ, thời gian chạy, etc). Hiệu suất (performance) được định nghĩa là đơn vị đo liên quan nhất tới thành công của sản phẩm cuối. Hiệu suất sẽ được dịch sang ngôn ngữ tương ứng của Học máy để quy về các độ đo. Trong ví dụ dưới đây, tác giả sẽ chọn "error rate" là đơn vị đo hiệu suất.

Khi mới bắt đầu, bạn nên định nghĩa ra tiêu chí cho thành công. Dưới góc nhìn về sản phẩm, theo bạn, hiệu suất như thế nào thì bắt đầu gọi là hữu dụng? Ví dụ như hệ thống của bạn gợi ý ra 5 bài báo liên quan, ít nhất bao nhiêu trong số đó cần phải thực sự liên quan, và thế nào là liên quan ?

ML Engineering Loop sẽ giúp bạn định hình được quá trình phát triển, đơn giản hóa quá trình quyết định để có thể tập trung hơn vào bước tiếp theo. Khi đã quen dần với vòng lặp này, bạn sẽ có thể nhanh chóng luân phiên giữa phân tích và thực thi. Vòng lặp này còn hữu ích kể cả khi bạn đã là chuyên gia, bạn sẽ không bị ngợp hay mông lung khi mô hình không đáp ứng yêu cầu hay đột nhiên mục tiêu của nhóm thay đổi.

## Bắt đầu nào 

Để có thế "kích" vòng lặp, hãy bắt đầu từ một phiên bản đơn giản. Mục đích của việc "kích" này là để có 1 con số cho chúng ta đánh giá, làm cơ sở cho việc đánh giá sau này. Nó sẽ bao gồm các việc sau:

1. Chuẩn bị dữ liệu training, development và testing.
2. Áp dụng một mô hình đơn giản chạy được.

Ví dụ, có thể sử dụng các dữ liệu tương tự có sẵn như một cuộc thi trên Kaggle cho huấn tập train, dữ liệu thu thập tay cho tập development và test. Về mô hình có thể chọn hồi quy tuyến tính (logistic regression) với dữ liệu gốc hay chạy một mô hình đã huấn luyện sắn (pre-trained network). Nên nhớ rằng, mục đích là chỉ cần chạy được, để khởi động cho vòng lặp.

**Lời khuyên**

Về tập test:

- Vì mục đích là làm tốt trên tập test, vậy nên tập test cần phản ánh chính xác mục đích sản phẩm hay thương mại của dự án. Ví dụ khi bạn đang xây dựng 1 ứng dụng chẩn đoán tình trạng của da người qua ảnh selfie, bạn có thể train trên bất cứ dữ liệu nào, nhưng hãy đảm bảm dữ liệu test sẽ chứa những ảnh ánh sánh yêu, chất lượng kém như ảnh selfie.

- Thay đổi tập test sẽ là thay đổi mục tiêu của nhóm, vậy nên nếu có thay đổi thì nên thay đổi sớm, và chỉ nên thay đổi khi có thay đổi về dự án, sản phẩm hay mục tiêu thương mại.

- Tập test và development cần phải đủ lớn để dữ liệu không bị nhiễu, đủ chính xác cho mục đích đánh giá, so sánh các mô hình.

- Cẩn thận với nhãn của dữ liệu, vì mỗi điểm dữ liệu sai sẽ tương ứng với một lỗi trong yêu cầu của sản phẩm (Product requirement)

- Nên biết hiệu suất của người hoặc các hệ thống đã có trên tập test. Đó sẽ là một giới hạn trên "error rate" giúp bạn xác định hiệu suất tốt nhất có thể đạt được.

- Đạt tới hiệu suất tương tự con người thường là mục tiêu dài hạn. Bởi cho đến cuối cùng, mục tiêu là tối ưu hiệu suất đến gần với chính con người nhất có thể.

Về tập development và train:

- Tập development đại diện cho tập test, được sử dụng để điều chỉnh các siêu tham số (hyper-parameters). Như vậy, tập này cần có phân phối dữ liệu gần với tập test, nhưng không được giống hệt, cùng một nhóm người dùng, đầu vào. Có một cách hay được sử dụng đó là xáo dữ liệu lên rồi chia ra tập development và test (sao cho phân phối hai tập tương đương).

- Nếu bạn nghĩ rằng dữ liệu sản phẩm có thể  bị nhiễu, hãy xử lý nó ở tập train bằng các phép gia tăng (augmentation) và giảm chất lượng (degradation) dữ liệu. Không thế kì vọng mô hình chỉ học ảnh sắc nét mà lại đoán tốt trên ảnh mờ được.

Một khi đã có một bản prototype, bạn có thể kiểm tra hiệu suất trên các tập dữ liệu. Đây cũng là bước cuối của vòng lặp. Đo đạc các biến động của khoảng cách giữa hiệu suất test và hiệu suất mong muốn đáp ứng tiêu chí hữu dụng của sản phẩm. Giờ là lúc bắt đầu vào chu trình của chúng mình.

![](https://cdn-images-1.medium.com/max/1600/1*rQD1-X6G5LuoKq-FEQwV3Q.png)

### Phân tích (Analyze)

### Chọn phương pháp (Select Approach)

### Thực thi (Implement)

### Đo đạc (Measure)

## Medium Article

[How to deliver on Machine Learning projects](https://blog.insightdatascience.com/how-to-deliver-on-machine-learning-projects-c8d82ce642b0?fbclid=IwAR2oax7e0w_SQEMSZqquYF5E6n2Txfjcd4ybG-w1N2jz1ye_cDbxIa-80FM)
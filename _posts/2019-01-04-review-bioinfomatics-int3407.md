---
published: true
layout: post
title: BioInformatics INT3407
subtitle: Ôn tập cho khóa học INT3407
date: '2019-01-04 11:00:00 +0700'
categories: null
---

### Nội dung ôn tập
```
- DNA (gien), RNA, protein, các thành tố cấu thành chuỗi gien, quá trình tổng hợp protein; các CSDL sinh học điển hình cho DNA và protein (v.d. NCBI, Protein databank, v.v.)
- Chuỗi tương đồng
- Gióng hàng 2 chuỗi, tìm kiếm CSDL với blast, các thông số trả về của blast.
- Gióng hàng đa chuỗi (sử dụng profile hoặc mô hình sum-of-pair, star model)
- Học máy (machine learning) trong tin sinh học (Mô hình Decision tree, Naive Bayesian model, etc., k-fold cross validation, v.v)
- Dữ liệu gene expression
```

### DNA (gien), RNA, protein, các thành tố cấu thành chuỗi gien, quá trình tổng hợp protein

Trình tự DNA, RNA, protein là một trong những chủ đề nghiên cứu chủ yếu của Sinh học phân tử, mà từ đó để tìm ra đặc điểm, phương thức tiến hóa và mối quan hệ giữa các loài.
Acid Nucleic là một loại đại phân tử sinh học mang thông tin mã hóa chức năng và các đặc điểm của sinh vật sống. Acid Nucleic gồm 2 loại là DNA (Deoxyribo Nucleic Acid) và RNA (Ribo Nucleic Acid). Thành phần cơ bản của AN là các phân tử hóa học nucleotide (DNA: A, T, G, C; RNA: A, U, G, C). Các nucleotide này kết hợp với nhau tạo thành cấu trúc xoắn kép gồm 2 sợi, các nucleotide ở mỗi sợ sẽ liên kết với nhau theo quy tắc A-T, G-C. Do vậy, thông tin trình tự DNA có thể lưu trữ bởi trình tự trên 1 sợi, theo dạng xâu kí tự như "ATAGCAT..."

Protein cũng thuộc những loại dữ liệu phổ biến và quan trọng trong tin sinh, nó quyết định chức năng, quá trình phát triển và bệnh tật của sinh vật sống. Protein được cấu tạo từ chuỗi các amino acid (20 loại), mỗi amino acid được cấu tạo từ 3 thành phần chính là nhóm amin (NH2), nhóm caboxyl (COOH) là nhóm R.

Mối quan hệ giữa DNA và Protein là: các đoạn DNA nhỏ trên chuỗi DNA sẽ mang thông tin hướng dẫn tạo ra Protein thông qua quá trình tổng hợp Protein, các đoạn DNA này được gọi là đoạn *gen*.

Quá trình tổng hợp Protein gồm 2 giai đoạn: phiên mã và dịch mã: ADN $\to$ ARN $\to$ Protein
- Phiên mã: đoạn gen trên DNA sẽ được biến đổi thành đoạn RNA mang thông tin tương ứng (T->U)
- Dịch mã: đoạn RNA này sẽ được dịch mã thành đoạn amino acid theo quy tắc *mỗi bộ 3 nucleotide tương ứng (codon) sẽ được mã hóa thành 1 loại acid amin tương ứng theo bộ quy tắc* (trong 64 bộ 3 chỉ có 61 bộ mã hóa, 3 bộ còn lại là tín hiệu kết thúc quá trình dịch mã)
### Chuỗi tương đồng
Hai chuỗi được gọi là tương đồng (trình tự tương đồng) nếu chúng tiến hóa từ một DNA tổ tiên chung. Nếu 2 chuỗi là tương đồng thì chúng sẽ tương đối giống nhau, không giống nhau hoàn toàn bởi có thể xảy ra đột biến trong quá trình tiến hóa (substitution, insertion, deletion), và cũng vì vậy mà chưa chắc 2 chuỗi giống nhau đã là tương đồng. Định nghĩa này cũng tương tự đối với Protein. 

### Các CSDL sinh học điển hình cho DNA và protein (v.d. NCBI, Protein databank, v.v.)
Mặc dù việc giải trình tự DNA, Protein diễn ra trên khắp thế giới nhưng gần như tất cả dữ liệu thu được đều được lưu trữ và chia sẻ tại một số trung tâm lớn như:
- Trung tâm thông tin Công nghệ Sinh học Quốc gia Hoa Kì (ncbi)
- Trung tâm thông tin Công nghệ Sinh học Châu Âu (ebi)
- Ngân hàng dữ liệu DNA của Nhật Bản (ddbj)

NCBI là trung tâm thông tin trực tuyến lưu trữ nhiều cơ sở dữ liệu và cung cấp hàng loạt công cụ tìm kiếm và phân tích dữ liệu trực tuyến. Cấu trúc cơ bản của NCBI gồm 5 CSDL:
- Nucleotide: lưu trữ dưới dạng các file văn bản, mỗi file gồm nhiều trường dữ liệu. Có hai cách để tìm kiếm dữ liệu thông qua máy tìm kiếm Entrez: đơn giản và nâng cao. Điểm khác nhau giữa hai cách này là số lượng trường thông tin phục vụ cho việc tìm kiếm. Với tìm kiếm cơ bản, thông tin chính chủ yếu là tên trình tự (locus name) và main keyword. Với tìm kiếm nâng cao, có thể xác định thêm một số trường thông tin như tên gen (gene name), tên sinh vật (organism), thuộc tính (properties) và điều kiện liên kết (and/or/not) giữa các trường.
  - Genbank: các trình tự do người dùng trực tiếp giải và chia sẻ lên
  - RefSeq: các trình tự đã được refined
- Structure: thông tin về cấu trúc bậc cao của các trình tự phân học sinh tử (chủ yếu là protein)
- Genome: lưu trữ nhiều hệ gien của các loài sinh vật khác nhau.
- Protein:
  - SwissProt/UniProtKB 
  - Protein Databank
- PubMed: lưu trữ các tài liệu (bài báo, tài liệu kĩ thuật, sách trực tuyến, ..) liên quan đến các chủ đề trong khoa học cuộc sống.

Một trong những định dạng dữ liệu chuẩn được các trung tâm thông tin sử dụng là FASTA, dùng để mô tả thông tin về một trình tự DNA (protein).
# Call Center Performance Analysis
## Project Overview
Proyek ini bertujuan untuk menganalisis performa call center dalam menangani panggilan masuk dan mengukur Key Metrics. Hasil analisis divisualisasikan melalui dashboard interaktif untuk memudahkan interpretasi dan pengambilan keputusan.

Beberapa Key Metrics yang ditinjau:
- Answered Calls
- Resolved Calls
- Average Handling Time
- Customer Satisfication Ratings
- Agent Performance
- Speed of Answered
- Topic Distribution
- Call Volume

## Data Source
Dataset yang digunakan mencakup 5000 entri panggilan yang diterima oleh call center dalam kurun waktu 3 bulan (01/01/2021 - 31/03/2021), berisi kolom-kolom berikut: `Call Id`,
`Agent`, `Date`, `Time`, `Topic`, `Answered (Y/N)`, `Resolved`, `Speed of answer in seconds`, `AvgTalkDuration`, `Satisfaction rating`. 

Berikut link yang dapat diakses [Call Center Dataset](https://www.kaggle.com/datasets/gayatriwagadre/pwc-call-centre-analysis/data).

## Tools
Microsoft Excel (Data Wrangling), Power BI (Data Visualization)

## Progress
### Data Understanding
- Mengkategorikan data berdasarkan kolom `Agent` untuk mengukur kinerja tiap agent.
- Mengidentifikasi kolom `Time` dapat digunakan untuk mengetahui waktu sibuk call center dalam melayani pelanggan.  
- Mengkategorikan data berdasarkan kolom `Topic` untuk mengetahui distrbusi panggilan berdasarkan topic permasalahan.
- Mengidentifikasi bahwa kolom `Speed answer in seconds` digunakan untuk menghitung panggilan yang berhasil direspon setidaknya dalam 30detik.
- Mengidentifikasi kolom `Avg Talk Duration` dapat digunakan untuk menghitung rata-rata durasi call center dalam menghandle panggilan.

### Data Processing
- Mengecek missing value dan data duplikat. Pada kasus kali ini missing values pada kolom `Resolved`, `Speed of answer`, `AvgTalkDuration`, dan `Satisfaction rating` yang berkaitan dengan panggilan yang tidak terjawab (kolom "Answered (Y/N)" yang bernilai "N") dibiarkan kosong.
- Menambahkan kolom `Answered` dan `Abandoned` yang bernilai biner (0/1), dikonversi dari kolom `Answered (Y/N)` menggunakan formula `=IF(Answered (Y/N)="Y", 1, 0)` dan `=IF(Answered (Y/N)="N", 1, 0)` untuk memudahkan dalam membuat visualisasi pada Power BI.
- Menambahkan kolom `Solved` dengan menggunakan formula `=IF(Answered (Y/N)="N", NA(), IF(Resolved="Y", 1, 0))`, dan kolom `Unsolved` dengan formula `=IF(Answered (Y/N)="N", NA(), IF(Resolved="N", 1, 0))`.
- Menambahkan kolom `Answered within 30s` menggunakan formula `=IF(Answered (Y/N)="N", NA(), IF(Speed answer in seconds<=30, "Yes", "No"))` untuk menentukan apakah panggilan dijawab dalam setidaknya 30 detik dan membiarkan kolom bernilai null jika panggilan tidak terjawab (kolom `Answered (Y/N)` bernilai "N").
- Dan menambahkan kolom `Handling time in seconds` berisi total waktu dalam detik yang digunakan untuk menjawab panggilan yang dikonversi dari kolom `AvgTalkDuration` dengan menggunakan formula `=IF(Answered (Y/N)="N", NA(), HOUR(AvgTalkDuration)*3600 + MINUTE(AvgTalkDuration)*60 + SECOND(AvgTalkDuration))`.

### Exploratory Data Analysis
Pada tahap ini pivot table digunakan untuk memberikan gambaran pola atau tren yang terdapat pada data sebelum divisualisasikan pada Power BI, berikut ini beberapa temuan yang didapatkan:

Average Handling Time

![Average Handling Time](https://github.com/user-attachments/assets/4dd84048-3603-48d7-b2a2-e69b9725db19)

Answered Calls:

![Answered Calls](https://github.com/user-attachments/assets/0cc3c4da-cecf-453c-97d7-163d669b9fa7)

Answered Calls per Agent

![Answered Calls per Agent](https://github.com/user-attachments/assets/8cb45b59-c637-43fd-8212-74d158871cbd)

Answered within 30s

![Answered within 30s](https://github.com/user-attachments/assets/91e80b9a-51a9-4d7d-93c7-18850ff9fee5)

Answered within 30s per Agent

![Answered within 30s per Agent](https://github.com/user-attachments/assets/0969bfb1-0873-47c2-bbe5-b93c00ba8772)

Resolved Calls

![Resolved Calls](https://github.com/user-attachments/assets/da28c705-247d-493f-ad1c-ed30b56c9150)

Resolved Calls per Agent

![Resolved Calls per Agent](https://github.com/user-attachments/assets/e701b69f-bdda-41c2-a444-4e095e380430)

Average of Satisfication ratings

![Average of Satisfication ratings](https://github.com/user-attachments/assets/c3525939-8110-402e-b4a6-71c889c1eea4)

Call Volume per Hour

![Call Volume per Hour](https://github.com/user-attachments/assets/81c03898-0723-4f86-9c8d-ead5b95d7dd1)

### Visualization
Visualisasi dibuat menggunakan Power BI, menampilkan Key Matrics yang telah disebutkan sebelumnya:
- Total jumlah panggilan yang masuk, total panggilan yang terjawab, total panggilan yang masalahnya berhasil terpecahkan, dan rata-rata waktu yang digunakan untuk menangani panggilan ditampilkan pada dashboard bagian kiri atas menggunakan card chart.
- Bar chart menunjukkan jumlah setiap satisfaction rating yang diberikan pelanggan setelah menerima pelayanan dari call center, rata-rata dari keseluruhan rating yang didapat divisualisasikan dengan gauge chart untuk memberikan informasi tambahan.
- Performa setiap agent ditampilkan melalui tabel yang berisi metrik-metrik penting seperti average of satisfaction rating, answered calls, solved calls, average speed of answer, dan average handling time.
- Pie chart memvisualisasikan jumlah panggilan yang berhasil direspon setidaknya dalam 30detik.
- Doughnut chart menampilkan distribusi panggilan berdasarkan topic permasalahan yang dialami pelanggan.
- Column chart menunjukkan jumlah banyaknya panggilan per jam operasional.

![Dashboard](https://github.com/user-attachments/assets/31916c10-e30b-4cdd-88c9-b78fed6b17da)

## Insights and Recommendation Actions
- Selama 3 bulan call center menerima panggilan sebanyak 5.000 panggilan.
- 81,08% dari jumlah tersebut yakni sebanyak 4.054 panggilan berhasil dijawab/direspon, ini merupakan performa yang bagus.
- Dari jumlah panggilan yang terjawab, sebanyak 89,94% (3.646) panggilan, permasalahannya berhasil terpecahkan.
- Dari seluruh panggilan yang terjawab, rata-rata waktu yang dihabiskan untuk menangani panggilan (Average Handle Time) adalah sekitar 4 menit yang mana ini cukup umum.
- Rating 3 adalah satisfication ratings yang paling banyak diterima, kemudian diikuti rating 4, kemudian rating 5. Ini performa yang cukup bagus, namun perlu ditingkatkan agar orang yang memberikan rating 3 yang mana bisa di asumsikan tidak terlalu puas dengan pelayanan yang diberikan bisa memberikan rating yang lebih tinggi, mungkin dengan meningkatkan pelayanannya agar dapat mencapai target rata-rata yang ditetapkan yakni 4,5 sedangkan saat ini rata-rata satisfication rating nya sebesar 3,4.
- Agent yang memiliki performa paling baik adalah Martha dengan rata-rata rating tertinggi sebesar 3,47, namun perbandingan antar agent memiliki selisih yang sedikit, ini menandakan persaingan antar agent yang cukup ketat. Namun mungkin bisa diusahakan untuk meningkatkan rating setiap agent untuk mencapai target dari rata-rata satisfication ratings.
- Dari seluruh panggilan, rata-rata kecepatan merespon panggilan adalah satu menit dan panggilan yang berhasil direspon 30 detik atau kurang hanya sebanyak 18,52% (751), ini mungkin terjadi pada jam-jam sibuk yang mana jumlah panggilan yang masuk melebihi kapasitas agen yang tersedia sehingga waktu tunggu meningkat. Ini perlu diperbaiki agar rata-rata kecepatan merespon panggilan setidaknya 30 detik, mungkin dengan menambahkan agent pada jam-jam sibuk.
- **11:00:00 AM - 01:59:59 PM** adalah jam-jam yang paling sibuk meskipun memiliki selisih yang tidak terlalu jauh dari jam lainnya.
- Topic yang dibahas dari seluruh panggilan cukup merata, hanya memiliki selisih yang sangat sedikit, namun topic yang paling banyak dibahas adalah 'Streaming' sekitar 20,44% dari total kesuluruhan panggilan, meskipun memiliki selisih hanya 0,92% dengan yang paling sedikit ('Contract related' 19,52%).

## Conclusion
Performa call center sudah cukup baik, namun untuk melestarikan pelayanan pelanggan yang optimal, penambahan agen pada jam-jam sibuk, manajemen kapasitas yang lebih baik, dan pelatihan agen tingkat lanjut mungkin perlu diterpakan.

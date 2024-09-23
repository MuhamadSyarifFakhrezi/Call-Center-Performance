# Call Center Performance
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
`Agent`, `Date`, `Time`, `Topic`, `Answered (Y/N)`, `Resolved`, `Speed of answer in seconds`, `Avg Talk Duration`, `Satisfaction rating`. 
Berikut link yang dapat diakses (Call Center Dataset)[https://www.kaggle.com/datasets/gayatriwagadre/pwc-call-centre-analysis/data].

## Tools
Microsoft Excel (Data Wrangling), Power BI (Data Visualization)

## Progress
### Data Understanding
- Mengkategorikan data berdasarkan kolom `Agent` untuk mengukur kinerja tiap agent.
- Mengidentifikasi kolom `Time` dapat digunakan untuk mengetahui waktu sibuk call center dalam melayani pelanggan.  
- Mengkategorikan data berdasarkan kolom `Topic` untuk mengetahui distrbusi panggilan berdasarkan topic permasalahan.
- Mengidentifikasi bahwa kolom `Speed answer in seconds` digunakan untuk menghitung panggilan yang berhasil direspon setidaknya dalam 30detik.
- Mengidentifikasi kolom `Avg Talk Duration` dapat digunakan untuk menghitung rata-rata durasi call center dalam menghandle panggilan.

### Data Wrangling

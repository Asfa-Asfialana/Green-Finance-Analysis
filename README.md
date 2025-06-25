# 🌱 Analisis Green Finance | Self-Learning Project

## Hai, Sobat ETL! 👋

Apa kabar hari ini? Semoga tetap semangat dan sehat selalu yaa 💪  
Selamat datang di repository ini — repositori ini dibuat sebagai bagian dari **self-learning journey** untuk memahami dan menganalisis **green finance**, atau gampangnya: _menganalisis cara keuangan yang digunakan untuk project peduli sama lingkungan_ 🌍💸

## 🎯 Tujuan

Tujuan dari proyek ini:
- Memahami konsep green finance dari sisi data
- Melihat analisis green finance berdampak terhadap lingkungan dan sosial yang terukur.
- Bagaimana kita dapat menggunakan data historis untuk memprediksi keberhasilan dan risiko proyek hijau.
- Membedah berbagai variabel dalam dataset yang relevan, mulai dari data finansial, lingkungan, hingga sosial-ekonomi.
  
----

## 1. Deskripsi Green Finance

**Green Finance** adalah pendekatan keuangan yang mengarahkan investasi dan pembiayaan ke proyek-proyek yang memiliki dampak positif terhadap lingkungan. Fokus utamanya adalah mendukung transisi menuju ekonomi rendah karbon dan berkelanjutan, termasuk pembiayaan untuk:

- Energi terbarukan (seperti PLTS dan PLTM)
- Pengelolaan limbah
- Transportasi ramah lingkungan
- Efisiensi energi
- Adaptasi dan mitigasi perubahan iklim

Komponen Utama Green Finance adalah **Investasi Hijau** yang merupakan proyek dengan dampak lingkungan positif, seperti mengurangi emisi, menghemat energi, atau konservasi alam. Dan **Instrumen Keuangan** yang terdiri dari Green Bond, Green Loan, dan ESG Fund (Environmental, Social, Governance).

Sedangkan untuk manfaat Green Finance adalah :

- Mengurangi risiko jangka panjang akibat perubahan iklim
- Mendorong transparansi lingkungan di sektor keuangan
- Memberikan insentif bagi investor dan penerbit yang peduli lingkungan (misalnya **greenium**: spread lebih rendah pada green bond)

### ⚖️ Regulasi Green Finance di Indonesia

#### 1. **Taksonomi Hijau Indonesia (THI) – OJK 2022**
Merupakan sistem klasifikasi untuk menilai apakah sebuah kegiatan ekonomi tergolong "hijau". THI menetapkan kriteria teknis dan sektor prioritas.

#### 2. **POJK No. 60/POJK.04/2017**
Mengatur penerbitan **Green Bond**, termasuk:
- Pelaporan dampak lingkungan
- Penilaian kelayakan proyek hijau

#### 3. **POJK No. 51/POJK.03/2017**
Mewajibkan lembaga keuangan menyusun:
- **Rencana Aksi Keuangan Berkelanjutan (RAKB)**
- Menilai portofolio berdasarkan prinsip keberlanjutan, termasuk analisis GNPV dan dampak ESG.

----

## 2. Analisis Field Dataset

### 2.1 Financial Dataset

#### 📊 Struktur Dataset

| Nama Field           | Deskripsi Singkat                             |
|----------------------|-----------------------------------------------|
| Investment_Amount    | Total investasi proyek (dalam rupiah).        |
| Loan_Interest_Rate   | Suku bunga tahunan (%)                        |
| Default_Risk_Score   | Skor risiko gagal bayar (0–100)               |
| Green_Bond_Spread    | Selisih imbal hasil (bps) vs obligasi biasa   |

#### 📐 Rumus Green Net Present Value (GNPV)

$$
GNPV = \sum_{t=1}^{N} \frac{(CF_t + E_t)}{(1 + r)^t} - I_0
$$

**Keterangan:**
- \( GNPV \): Green Net Present Value (nilai kini bersih hijau).
- \( CF_t \): Arus kas bersih konvensional pada tahun ke-\(t\).
- \( E_t \): Nilai eksternalitas lingkungan (misalnya pengurangan emisi CO₂, penghematan air) pada tahun ke-\(t\).
- \( r \): Tingkat diskonto (contoh: 0.05 untuk 5%).
- \( t \): Tahun ke-\(t\).
- \( N \): Umur proyek (dalam tahun).
- \( I_0 \): Investasi awal proyek.

✅ GNPV yang lebih tinggi menunjukkan proyek lebih layak secara finansial **dan** berkontribusi pada keberlanjutan lingkungan.
> Proyek dianggap layak jika GNPV > 0.

Analisis **GNVP** dari data berikut [Financial_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Financial_Dataset.csv) menunjukkan hasil sebagai berikut :

![financial-dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/financial-dataset.png)

Kesimpulan Hasil :

- Proyek dengan GNPV positif secara konsisten dianggap layak menurut kaidah evaluasi finansial dan dampak lingkungan.
- Dalam visualisasi, mayoritas proyek PLTS seperti PLTS-JABW-001, PLTS-JATIM-001, dan PLTS-NTB-001 menunjukkan GNPV tinggi → menandakan kombinasi arus kas dan dampak lingkungan yang menguntungkan.
- Beberapa PLTM juga menunjukkan kinerja baik, namun umumnya GNPV-nya lebih rendah dibandingkan PLTS.


### 2.2 Enviromental Dataset

**Environmental Dataset** adalah kumpulan data proyek energi hijau yang merekam dampak lingkungan dari masing-masing proyek. Dataset ini sangat penting dalam mendukung keputusan investasi berbasis lingkungan (green investment), khususnya dalam rangka transisi energi bersih dan kebijakan pembiayaan hijau.

#### 📊 Struktur Dataset

| Nama Kolom                 | Deskripsi Singkat                                                                 |
|---------------------------|------------------------------------------------------------------------------------|
| `Project_ID`              | Kode unik proyek (misal: PLTS-NTT-001)                                             |
| `CO2_Reduction`           | Estimasi pengurangan emisi karbon tahunan (dalam ton CO2e)                         |
| `Energy_Output`           | Produksi energi tahunan (dalam satuan kWh atau MWh)                                |
| `Environmental_Risk_Index`| Skor risiko lingkungan proyek (skala 0–100, makin tinggi makin berisiko)          |
| `Konteks_Lingkungan`      | Deskripsi singkat kondisi lingkungan atau ekologi setempat                        |
| `Peringkat_Dampak`        | Penilaian kualitatif terhadap dampak lingkungan (contoh: High / Medium / Low)      |

**Rumus** : 

**🌿 Carbon Return on Investment (CROI)** atau **CROI** adalah rumus untuk mengukur seberapa efisien investasi dalam proyek lingkungan dalam menghasilkan pengurangan emisi karbon.

$$
CROI = \frac{\sum_{t=1}^{N} (R_t \times P_C)}{I_0}
$$

**Keterangan:**
- \( CROI \): Carbon Return on Investment.
- \( R_t \): Emisi karbon yang berhasil dikurangi pada tahun ke-\(t\) (ton CO₂e).
- \( P_C \): Harga karbon per ton CO₂e (dalam Rupiah).
- \( I_0 \): Investasi awal proyek (dalam Rupiah).
- \( N \): Umur proyek (dalam tahun).

✅ Nilai CROI yang lebih tinggi menandakan efisiensi karbon yang lebih baik per unit investasi.

Analisis CROI dari data : [Environmental_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Environmental_Dataset.csv) menunjukkan hasil sebagai berikut :

![enviromental-dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/enviromental-dataset.png)

### 2.3 Social Dataset

Social Dataset adalah data yang digunakan untuk mengukur dampak proyek terhadap masyarakat, aspek krusial dalam kerangka ESG (*Environmental, Social, and Governance*).
Metode analisis dapat mencakup pengukuran SROI (Social Return on Investment) dan estimasi dampak berbasis data tenaga kerja dan sosial. Hasil ini membantu menilai apakah proyek memberikan manfaat berkelanjutan dan inklusif bagi masyarakat lokal.

#### 📊 Struktur Dataset

| Nama Field                  | Deskripsi Singkat                                                                 |
|----------------------------|------------------------------------------------------------------------------------|
| `Jobs_Created`             | Jumlah pekerjaan FTE yang dihasilkan proyek, mencerminkan manfaat ekonomi lokal.  |
| `Community_Engagement_Score` | Tingkat penerimaan dan partisipasi masyarakat, dinilai dari skor 0–100.           |
| `Access_to_Clean_Energy_Rate` | Persentase kenaikan akses masyarakat ke energi bersih, terutama wilayah 3T.       |
| `Gini_Coefficient_Impact`  | Efek proyek terhadap ketimpangan pendapatan; nilai negatif = ketimpangan menurun. |

**🤝 Rumus Social Return on Investment (SROI)**

$$
SROI = \frac{NPV_{social}}{I_0}
$$

**Keterangan:**
- \( SROI \): *Social Return on Investment*, menunjukkan berapa nilai sosial yang dihasilkan per rupiah investasi.
- \( NPV_{social} \): Nilai sekarang (Net Present Value) dari seluruh dampak sosial yang dimonetisasi (dalam rupiah).
- \( I_0 \): Investasi awal proyek (dalam rupiah).

Hasil analisis dari data [Social_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Social_Dataset.csv) menunjukkan hasil sebagai berikut :

![social-dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/social-dataset.png)

### 2.4 Economic Dataset

Dataset ini memberikan gambaran kondisi ekonomi tempat proyek dijalankan. Informasi ini penting untuk memahami risiko dan potensi keberhasilan proyek dari sisi ekonomi nasional.

#### 📊 Struktur Dataset

| Nama Field           | Deskripsi Singkat                                                             |
|----------------------|--------------------------------------------------------------------------------|
| `GDP_Growth`         | Laju pertumbuhan ekonomi. Tinggi = peluang pasar energi makin besar.          |
| `Inflation_Rate`     | Tingkat inflasi. Semakin tinggi, biaya proyek bisa naik.                      |
| `FDI_Inflows`        | Masuknya investasi asing. Mencerminkan kepercayaan terhadap iklim usaha.      |
| `Unemployment_Rate`  | Persentase pengangguran. Tinggi = proyek punya dampak sosial lebih besar.     |

**📉 Rumus Economic Risk Adjustment Factor (ERAF)**

$$
ERAF = w_1 \left( \frac{IR_t - IR_{base}}{IR_{base}} \right) + w_2 \left( \frac{UR_t - UR_{base}}{UR_{base}} \right) - w_3 \left( \frac{GDP_t - GDP_{base}}{GDP_{base}} \right)
$$

**Keterangan:**
- \( ERAF \): *Economic Risk Adjustment Factor*, skor penyesuaian risiko ekonomi (tanpa satuan).
- \( IR_t \): Tingkat inflasi saat ini (Inflation Rate).
- \( IR_{base} \): Inflasi dasar atau target bank sentral.
- \( UR_t \): Tingkat pengangguran saat ini.
- \( UR_{base} \): Pengangguran dasar (rata-rata historis).
- \( GDP_t \): Pertumbuhan Produk Domestik Bruto (PDB) saat ini.
- \( GDP_{base} \): Pertumbuhan PDB dasar (rata-rat_

Dari analisis [Economic_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Economic_Dataset.csv) menunjukkan hasil sebagai berikut :

![Grafik_ERAF_PLTS_PLTM](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/Grafik_ERAF_PLTS_PLTM.png)

### 2.5 Geospatial Dataset

Dataset ini menyajikan data lokasi proyek yang penting untuk menilai risiko lingkungan dan keberlanjutan proyek dari sisi spasial.

#### 📊 Struktur Dataset

| Nama Field                    | Deskripsi Singkat                                                  |
|-------------------------------|---------------------------------------------------------------------|
| `Latitude` / `Longitude`      | Titik koordinat lokasi proyek, untuk analisis peta dan risiko alam. |
| `Proximity_to_Protected_Area`| Jarak ke kawasan lindung. Dekat = potensi risiko regulasi tinggi.   |
| `Land_Use_Change`             | Perubahan fungsi lahan. Misalnya hutan jadi perkebunan = risiko naik.|

**Rumus 🌍 Geospatial Risk Index (GRI)**

$$
GRI = w_1 \cdot H + w_2 \cdot P + w_3 \cdot L
$$

**Keterangan:**

- \( GRI \): *Geospatial Risk Index*, skor risiko lokasi (0–1).
- \( H \): Skor risiko bencana alam, normalisasi dari data historis BNPB/BMKG.
- \( P \): Skor risiko kedekatan dengan kawasan lindung, dari *Proximity_to_Protected_Area*.
- \( L \): Skor risiko perubahan tutupan lahan (*Land_Use_Change*).
- \( w_1, w_2, w_3 \): Bobot faktor risiko (jumlahnya = 1), ditentukan melalui metode seperti *AHP*.

**Aturan Praktis:**
- GRI mendekati 1 → Risiko tinggi → perlu uji tuntas mendalam.
- Gunakan data spasial resmi (Ina-Geoportal, KLHK, BNPB).

Dari analisis data [Geospatial_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Geospatial_Dataset.csv) menunjukkan hasil sebagai berikut :

![geospatial-dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/geospatial-dataset.png)

---

### Kesimpulan 

Tentu, berikut adalah **kesimpulan proyek Green Finance** yang kamu kerjakan, berdasarkan kelima dimensi dataset—**finansial, lingkungan, sosial, ekonomi makro, dan geospasial**—disertai dengan **kalimat penutup hangat untuk Sobat ETL**, cocok untuk `README.md`, presentasi, atau laporan akhir:

---

## 📌 Kesimpulan

Analisis proyek *Green Finance* ini menunjukkan bahwa keberlanjutan proyek energi hijau tidak hanya ditentukan oleh aspek finansial, tetapi juga oleh faktor lingkungan, sosial, ekonomi makro, dan risiko spasial.

* 💰 **Financial Dataset** memperlihatkan bahwa proyek dengan arus kas stabil dan investasi efisien cenderung lebih layak secara ekonomi.
* 🌱 **Environmental Dataset** menegaskan pentingnya efisiensi emisi dan penghematan sumber daya sebagai indikator keberhasilan proyek hijau.
* 🧑‍🤝‍🧑 **Social Dataset** menyoroti kontribusi proyek terhadap penciptaan lapangan kerja, keterlibatan masyarakat, dan pengurangan ketimpangan.
* 📈 **Economic Dataset** memberi konteks penting dalam membaca dinamika risiko makro yang dapat mempengaruhi kelayakan jangka panjang proyek.
* 🗺️ **Geospatial Dataset** membantu mengidentifikasi potensi risiko lokasi seperti bencana alam, kedekatan dengan kawasan lindung, dan perubahan tutupan lahan.

Melalui integrasi kelima hal ini, pendekatan *Green Finance* mampu memberi pandangan yang lebih adil dan akurat dalam menilai proyek energi berkelanjutan, baik dari sisi dampak maupun risikonya.
Terima kasih sudah membaca repository ini, Semoga analisis ini menginspirasi kita semua untuk membuat keputusan berbasis data yang lebih hijau dan berkeadilan.
Sampai jumpa di repository berikutnya dan tetap semangat,Sobat ETL 🌿💡📊

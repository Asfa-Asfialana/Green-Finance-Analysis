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

## 📐 Rumus Green Net Present Value (GNPV)

GNPV digunakan untuk menilai kelayakan finansial dan lingkungan dari proyek hijau. Rumus lengkapnya:

```
GNPV = ∑ [(CFₜ + ENVₜ) / (1 + r)ᵗ] - I₀
```

**Keterangan:**

- **GNPV** : Green Net Present Value (dalam rupiah)
- **CFₜ** : Arus kas bersih proyek pada tahun ke-`t` (operasional - biaya - pajak)
- **ENVₜ** : Nilai ekonomi manfaat lingkungan (misalnya, pengurangan emisi CO₂ × harga karbon)
- **r** : Tingkat diskonto (dalam desimal, misal 0.05 untuk 5%)
- **t** : Tahun ke-`t`
- **T** : Umur proyek (tahun)
- **I₀** : Investasi awal proyek (dalam rupiah)

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
## 🌿 Carbon Return on Investment (CROI)

**CROI** mengukur seberapa efisien investasi dalam proyek lingkungan dalam menghasilkan pengurangan emisi karbon.

## 📊 Rumus Carbon Return on Investment (CROI)

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


### ⚠️ Catatan:

- Gunakan satuan **ton CO₂e** dan **rupiah** secara konsisten.
- Ambil nilai **harga karbon** dari pasar karbon atau *social cost of carbon* jika tersedia.

Menghitung **CROI** artinya mengukur seberapa efisien suatu proyek dalam menghasilkan manfaat lingkungan (pengurangan emisi karbon) dibandingkan dengan biaya investasi proyek tersebut.

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

Hasil analisis dari data 

![


### 2.4 Economic Dataset

Dataset ini memberikan gambaran kondisi ekonomi tempat proyek dijalankan. Informasi ini penting untuk memahami risiko dan potensi keberhasilan proyek dari sisi ekonomi nasional.

#### 📊 Struktur Dataset

| Nama Field           | Deskripsi Singkat                                                             |
|----------------------|--------------------------------------------------------------------------------|
| `GDP_Growth`         | Laju pertumbuhan ekonomi. Tinggi = peluang pasar energi makin besar.          |
| `Inflation_Rate`     | Tingkat inflasi. Semakin tinggi, biaya proyek bisa naik.                      |
| `FDI_Inflows`        | Masuknya investasi asing. Mencerminkan kepercayaan terhadap iklim usaha.      |
| `Unemployment_Rate`  | Persentase pengangguran. Tinggi = proyek punya dampak sosial lebih besar.     |

Hasil analisis 

![

### 2.5 Geospatial Dataset

Dataset ini menyajikan data lokasi proyek yang penting untuk menilai risiko lingkungan dan keberlanjutan proyek dari sisi spasial.

#### 📊 Struktur Dataset

| Nama Field                    | Deskripsi Singkat                                                  |
|-------------------------------|---------------------------------------------------------------------|
| `Latitude` / `Longitude`      | Titik koordinat lokasi proyek, untuk analisis peta dan risiko alam. |
| `Proximity_to_Protected_Area`| Jarak ke kawasan lindung. Dekat = potensi risiko regulasi tinggi.   |
| `Land_Use_Change`             | Perubahan fungsi lahan. Misalnya hutan jadi perkebunan = risiko naik.|





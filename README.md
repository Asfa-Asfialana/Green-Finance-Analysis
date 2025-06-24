# 🌱 Analisis Green Finance | Self-Learning Project

## Hai, Sobat ETL! 👋

Apa kabar hari ini? Semoga tetap semangat dan sehat selalu yaa 💪  
Selamat datang di repository ini — repositori ini dibuat sebagai bagian dari **self-learning journey** untuk memahami dan menganalisis **green finance**, atau gampangnya: _menganalisis cara keuangan yang digunakan untuk project peduli sama lingkungan_ 🌍💸

---

## 🎯 Tujuan

Tujuan dari proyek ini:
- Memahami konsep green finance dari sisi data
- Melihat analisis green finance berdampak terhadap lingkungan dan sosial yang terukur.
- Bagaimana kita dapat menggunakan data historis untuk memprediksi keberhasilan dan risiko proyek hijau.
- Membedah berbagai variabel dalam dataset yang relevan, mulai dari data finansial, lingkungan, hingga sosial-ekonomi, lengkap dengan regulasi dan acuan akademis.

----

## 1. Deskripsi Green Finance

**Green Finance** adalah pendekatan keuangan yang mengarahkan investasi dan pembiayaan ke proyek-proyek yang memiliki dampak positif terhadap lingkungan. Fokus utamanya adalah mendukung transisi menuju ekonomi rendah karbon dan berkelanjutan, termasuk pembiayaan untuk:

- Energi terbarukan (seperti PLTS dan PLTM)
- Pengelolaan limbah
- Transportasi ramah lingkungan
- Efisiensi energi
- Adaptasi dan mitigasi perubahan iklim

### 💡 Komponen Utama Green Finance

1. **Investasi Hijau**
   - Proyek dengan dampak lingkungan positif, seperti mengurangi emisi, menghemat energi, atau konservasi alam.

2. **Instrumen Keuangan**
   - Green Bond
   - Green Loan
   - ESG Fund (Environmental, Social, Governance)

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

### 🏦 Manfaat Green Finance

- Mengurangi risiko jangka panjang akibat perubahan iklim
- Mendorong transparansi lingkungan di sektor keuangan
- Memberikan insentif bagi investor dan penerbit yang peduli lingkungan (misalnya **greenium**: spread lebih rendah pada green bond)

----

## 2. Analisis Field Dataset

### 2.1 Financial Dataset

#### 📊 Struktur Dataset: Green Finance

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

Hasil analisis **GNVP** dari data berikut [Financial_Dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Data/Financial_Dataset.csv) menunjukkan hasil sebagai berikut :

![financial-dataset](https://github.com/Asfa-Asfialana/Green-Finance-Analysis/blob/main/Visualisasi/financial-dataset.png)

Keterangan :

- Proyek dengan GNPV positif secara konsisten dianggap layak menurut kaidah evaluasi finansial dan dampak lingkungan.
- Dalam visualisasi, mayoritas proyek PLTS seperti PLTS-JABW-001, PLTS-JATIM-001, dan PLTS-NTB-001 menunjukkan GNPV tinggi → menandakan kombinasi arus kas dan dampak lingkungan yang menguntungkan.
- Beberapa PLTM juga menunjukkan kinerja baik, namun umumnya GNPV-nya lebih rendah dibandingkan PLTS.


### 2.2 Enviromental Dataset

**Environmental Dataset** adalah kumpulan data proyek energi hijau yang merekam dampak lingkungan dari masing-masing proyek.

Dataset ini sangat penting dalam mendukung keputusan investasi berbasis lingkungan (green investment), khususnya dalam rangka transisi energi bersih dan kebijakan pembiayaan hijau.

### 📊 Struktur Data

| Nama Kolom                 | Deskripsi Singkat                                                                 |
|---------------------------|------------------------------------------------------------------------------------|
| `Project_ID`              | Kode unik proyek (misal: PLTS-NTT-001)                                             |
| `CO2_Reduction`           | Estimasi pengurangan emisi karbon tahunan (dalam ton CO2e)                         |
| `Energy_Output`           | Produksi energi tahunan (dalam satuan kWh atau MWh)                                |
| `Environmental_Risk_Index`| Skor risiko lingkungan proyek (skala 0–100, makin tinggi makin berisiko)          |
| `Konteks_Lingkungan`      | Deskripsi singkat kondisi lingkungan atau ekologi setempat                        |
| `Peringkat_Dampak`        | Penilaian kualitatif terhadap dampak lingkungan (contoh: High / Medium / Low)      |

**Rumus** : 
```


**CROI** mengukur seberapa efisien suatu proyek dalam menghasilkan manfaat lingkungan (pengurangan emisi karbon) dibandingkan dengan biaya investasi proyek tersebut.
---

### 🔍 Penjelasan Komponen

| Komponen            | Penjelasan                                                                 |
|---------------------|----------------------------------------------------------------------------|
| `CO2_Reduction`     | Jumlah emisi karbon yang dikurangi per tahun oleh proyek (dalam ton CO2e) |
| `Carbon_Price`      | Harga karbon per ton (Rp). Diambil dari pasar karbon atau estimasi sosial |
| `Project_Lifetime`  | Umur proyek dalam tahun                                                   |
| `Investment_Cost`   | Total biaya investasi proyek (dalam miliar rupiah)                        |
| `CROI`              | Rasio efisiensi karbon terhadap biaya. Makin tinggi makin baik            |


## 📈 Hasil Analisis dan Interpretasi

* Proyek dengan **CROI tertinggi** menunjukkan dampak pengurangan karbon yang paling efisien secara finansial.
* Proyek yang memiliki **CO2\_Reduction besar dan biaya investasi rendah** cenderung menghasilkan **CROI tinggi**.
* Proyek seperti `PLTS-JABW-001` atau `PLTS-JATIM-001` (misalnya) akan menjadi prioritas investasi ramah lingkungan.

---

## 📚 Referensi

* OJK - Taksonomi Hijau Indonesia (2022)
* POJK No. 60/POJK.04/2017 tentang Green Bond
* POJK No. 51/POJK.03/2017 tentang RAKB
* World Bank: Carbon Pricing Dashboard

```

---

Jika kamu ingin saya bantu buat README final dari *Green-Finance Project* kamu (dengan bagian GNPV, risiko, dll.), beri tahu saja. Saya siap bantu sampai jadi laporan lengkap.
```


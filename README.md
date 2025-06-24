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

# 🧩 XAI (Explainable AI) Audit Protocol

## 📌 Deskripsi
Repo ini berisi panduan teknis objektif untuk melakukan **audit transparansi dan akuntabilitas** pada model kecerdasan buatan berbasis *black-box*.  
Fokus utama protokol ini adalah verifikasi validitas metrik eksplanasi menggunakan instrumen *open‑source* yang sudah terstandarisasi.  
Tujuan: membuka "kotak hitam" machine learning agar keputusan model bisa dipahami, diaudit, dan diverifikasi.

---

## 1. Lingkup Metodologi & Alat Audit

Audit dilakukan menggunakan kombinasi framework eksternal untuk menguji apakah interpretasi yang dihasilkan model bersifat stabil dan valid.

| Aspek Audit | Metode Pengujian | Alat / Instrumen Riil |
| :--- | :--- | :--- |
| **[Atribusi Fitur](ca://s?q=Atribusi_fitur_dengan_SHAP_LIME)** | Mengukur kontribusi fitur global dan lokal secara kooperatif game‑theoretic. | `shap`, `lime` |
| **[Evaluasi Kausal](ca://s?q=Evaluasi_kausal_dengan_DiCE)** | Menguji skenario "bagaimana jika" untuk melihat ambang batas perubahan keputusan model. | `dice-ml` |
| **[Stabilitas Eksplanasi](ca://s?q=Stabilitas_eksplanasi_AI)** | Menguji sensitivitas nilai atribusi terhadap gangguan kecil (*noise*) pada input. | `captum`, `scikit-learn` |
| **[Kepatuhan Bias](ca://s?q=Audit_bias_dengan_aif360_fairlearn)** | Mengukur metrik keadilan (*fairness*) seperti *disparate impact* dan *equalized odds*. | `aif360`, `fairlearn` |

---

## 2. Struktur Repositori Minimum

```text
xai-audit-protocol/
├── README.md                  # Deskripsi utama repo
├── config/
│   └── threshold_limits.json  # Batas toleransi deviasi (misal: p-value, SHAP divergence)
├── modules/
│   ├── attribution_verify.py  # Integrasi pipeline SHAP/LIME
│   └── counterfactual_test.py # Pipeline pengujian stabilitas berbasis DiCE
├── examples/
│   └── shap_demo.py           # Contoh kode Python SHAP
├── notebooks/
│   └── audit_pipeline_demo.ipynb # Dokumentasi visual jalannya audit
├── docs/
│   └── lavender_audit.md      # Audit protocol Lavender dengan SHAP
└── visuals/
    └── shap_summary.png       # Contoh visualisasi SHAP
  

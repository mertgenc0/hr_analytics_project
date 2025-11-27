# IBM HR Analytics - Çalışan Ayrılma Tahmini Projesi

##  Proje Özeti

Bu proje, IBM HR Analytics veri seti kullanılarak çalışanların şirketten ayrılma (attrition) olasılığını tahmin etmeyi amaçlamaktadır. Makine öğrenmesi algoritmaları ile risk altındaki çalışanların belirlenmesi ve proaktif önlemler alınması hedeflenmiştir.

---

##  Proje Hedefleri

1. **Betimleyici Analitik:** Veri ~~setini keşfetmek ve anlamak~~
2. **Veri Temizleme:** Eksik değerler ve aykırı değerlerle başa çıkmak
3. **Tahminleyici Analitik:** 4 farklı ML algoritması ile model geliştirmek
4. **Model Karşılaştırma:** En iyi performans gösteren modeli belirlemek
5. **En İyi Modeli Değerlendirme** Sonuçları iş değerine dönüştürmek

---

##  Veri Seti Bilgileri

- **Kaynak:** [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Örnek Sayısı:** 1,470 çalışan
- **Özellik Sayısı:** 35 özellik
- **Hedef Degişken:** Attrition (Yes/No)
- **Problem Tipi:** İkili Sınıflandırma 
- **Dengesiz Veri:** %16.1 Evet, %83.9 Hayır

### Önemli Özellikler:
- **Demografik:** Yaş, Cinsiyet, Medeni Durum
- **İş Bilgileri:** Departman, Rol, Maaş, Fazla Mesai
- **Performans:** İş Memnuniyeti, Çalışma Yılı, Eğitim
- **Çalışma Koşulları:** İş-Yaşam Dengesi, Mesafe

---

##  Kullanılan Teknolojiler

### Veri İşleme ve Analiz
- **Python 3.11+**
- **Pandas:** Veri manipülasyonu
- **NumPy:** Sayısal hesaplamalar
- **Matplotlib & Seaborn:** Veri görselleştirme

### Makine Öğrenmesi
- **Scikit-learn:** ML algoritmaları ve metrikleri
- **XGBoost:** Gradient Boosting
- **Logistic Regression**
- **LightGBM:** Light Gradient Boosting
- **Random Forest Regressioın**
- **Imbalanced-learn:** SMOTE (Dengesiz veri işleme)

### Geliştirme Ortamı
- **PyCharm**
- **Jupyter Notebook:** İnteraktif analiz
- **Git:** Versiyon kontrolü

---

##  Proje Yapısı

```
hr-analytics-project/
│                     
│── WA_Fn-UseC_-HR-Employee-Attrition.csv
│── hr_processed.csv
│
│── veri_analizi.ipynb
│── onisleme_modelleme.ipynb
│
├── models/                           
│   ├── scaler.pkl
│   ├── random_forest_model.pkl
│   ├── xgboost_model.pkl
│   └── logistic_regression_model.pkl
│   └── random_forest_model.pkl
│                        
│── venv
├── requirements.txt                  
└── README.md
├── .gitignore                        
```

---


## 📈 Metodoloji

### 1. Keşifsel Veri Analizi (EDA)
- ✅ Veri setinin genel yapısını inceleme
- ✅ Eksik değer ve aykırı değer analizi
- ✅ Hedef değişken dağılımı analizi
- ✅ Sayısal ve kategorik değişken görselleştirmeleri
- ✅ Korelasyon analizi
- ✅ Feature'ların attrition ile ilişkisi

### 2. Veri Ön İşleme
- ✅ Sabit değerli sütunların kaldırılması
- ✅ Kategorik değişkenlerin encode edilmesi (Label Encoding & One-Hot Encoding)
- ✅ Özellik mühendisliği (Yaş grupları, Gelir seviyeleri, vb.)
- ✅ Veri ölçeklendirme (StandardScaler)
- ✅ SMOTE ile dengesiz veri dengeleme
- ✅ Train-Test split (%80-%20)

### 3. Model Geliştirme

1. **Logistic Regression** 
2. **Random Forest Classifier**
3. **XGBoost Classifier**
4. **SVM**

### 4. Model Değerlendirme Metrikleri

- **Accuracy:** Genel doğruluk oranı
- **Precision:** Pozitif tahminlerin doğruluğu
- **Recall:** Gerçek pozitifleri yakalama oranı
- **F1-Score:** Precision ve Recall'un harmonik ortalaması
- **ROC-AUC:** Model ayırt etme gücü
- **Confusion Matrix:** Sınıflandırma detayları
- **Cross-Validation:** Model genelleme performansı

---
              
## Sonuçlar

### Model Performans Karşılaştırması

| Model | Accuracy | F1-Score | ROC-AUC  |
|-------|-------|-------|----------|
| **Random Forest** | 0.843537 | 0.36  | 0.814497 |
| **XGBoost** | 0.846939 | 0.43  | 0.808252   | 
| **SVM** | 0.843537 | 0.50  | 0.771126   | 
| **Logistic Regression** | 0.58  | 0.53  | 0.847877  |

### En İyi Model: **Logistic Regression**

**Neden Random Forest?**
- En yüksek F1-Score (%58)
- Dengeli Precision-Recall performansı
- Güçlü ROC-AUC skoru (0.84)
- Stabil cross-validation sonuçları
- İyi yorumlanabilir (feature importance)

---

## İş Önerileri ve İçgörüler

### Yüksek Riskli Çalışan Profili

**Dikkat Edilmesi Gereken Özellikler:**
- ✅ Fazla mesai yapan çalışanlar (%30-40 daha yüksek risk)
- ✅ İlk 1-3 yılında olan çalışanlar
- ✅ Düşük maaşlı pozisyonlar (<5000)
- ✅ Bekar/Genç çalışanlar (25-35 yaş arası)
- ✅ İş memnuniyeti düşük olanlar
- ✅ Seyahat gerektiren roller (özellikle Frequent travelers)


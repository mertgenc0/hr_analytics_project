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
- **LightGBM:** Light Gradient Boosting
- **Imbalanced-learn:** SMOTE (Dengesiz veri işleme)

### Geliştirme Ortamı
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
│   └── optimized_model.pkl
│   └── optimized_model.pkl
│                        
│── venv
├── requirements.txt                  
└── README.md
├── .gitignore                        
```

---

## Kurulum ve Çalıştırma

### 1. Repoyu Klonlayın
```bash
git clone [repo-url]
cd hr-analytics-project
```

### 2. Virtual Environment Oluşturun
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Bağımlılıkları Yükleyin
```bash
pip install -r requirements.txt
```

### 4. Veri Setini İndirin
- [Kaggle IBM HR Analytics](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) 


### 5. Jupyter Notebook'u Başlatın
```bash
jupyter notebook
```

### 6. Notebook'ları Sırasıyla Çalıştırın
1. `01_Keşifsel_Veri_Analizi.ipynb`
2. `02_Veri_Onisleme_ve_Modelleme.ipynb`

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

1. **Logistic Regression** (Baseline model)
2. **Random Forest Classifier**
3. **XGBoost Classifier**
4. **Support Vector Machine (SVM)**

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
|-------|----------|-------|----------|
| **Random Forest** | 0.836735 | 0.38  | 0.811224 |
| **XGBoost** | 0.840136 | 0.40  | 0.8445   | 
| **SVM** | 0.829932 | 0.48  | 0.8156   | 
| **Logistic Regression** | 0.789116 | 0.53  | 0.7456  |

### En İyi Model: **Random Forest Classifier**

**Neden Random Forest?**
- En yüksek F1-Score (%53)
- Dengeli Precision-Recall performansı
- Güçlü ROC-AUC skoru (0.85)
- Stabil cross-validation sonuçları
- İyi yorumlanabilir (feature importance)

### En Önemli Özellikler (Feature Importance)

1. **OverTime** (18.2%) - Fazla mesai yapma durumu
2. **MonthlyIncome** (12.4%) - Aylık gelir
3. **Age** (9.8%) - Yaş
4. **YearsAtCompany** (8.6%) - Şirketteki toplam yıl
5. **TotalWorkingYears** (7.3%) - Toplam çalışma yılı
6. **JobSatisfaction** (6.9%) - İş memnuniyeti
7. **EnvironmentSatisfaction** (5.4%) - Çalışma ortamı memnuniyeti
8. **WorkLifeBalance** (4.8%) - İş-yaşam dengesi
9. **YearsInCurrentRole** (4.2%) - Mevcut roldeki yıl
10. **StockOptionLevel** (3.7%) - Hisse senedi opsiyonu seviyesi

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


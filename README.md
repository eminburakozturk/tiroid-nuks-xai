# Tiroid Kanseri Nüks Tahmini — Açıklanabilir Yapay Zeka

**Farklılaşmış tiroid kanseri (FTK) hastalarında nüks riskini tahmin eden ve kararlarını SHAP ile açıklayan makine öğrenmesi çalışması.**

📄 **Makale (yayınlanmamış):** [Tiroid_Nuks_XAI_Makale.pdf](docs/Tiroid_Nuks_XAI_Makale.pdf)  
📓 **Kod:** [tiroid_nuks_tahmini.ipynb](tiroid_nuks_tahmini.ipynb)

## Sonuçlar

| Ölçüt | XGBoost (en iyi model) |
|---|---|
| Doğruluk | **%98,7** |
| F1-skoru | 0,977 |
| ROC-AUC | 0,997 |
| Duyarlılık (Recall) | %95,5 |
| Yanlış pozitif | 0 |

SHAP analizine göre nükste en belirleyici üç faktör: **tedaviye yanıt**, **ATA risk grubu** ve **tümör evresi (T)**. Bu sonuç klinik kılavuzlarla uyumlu.

## Veri ve yöntem

- **Veri:** [UCI Differentiated Thyroid Cancer Recurrence](https://archive.ics.uci.edu/dataset/915/differentiated+thyroid+cancer+recurrence) (`Thyroid_Diff.csv`): 383 hasta, 17 klinik ve patolojik değişken. Veri anonim ve kamuya açıktır.
- **Ön işleme:** Label / One-Hot Encoding, StandardScaler, %80/%20 tabakalı bölme
- **Karşılaştırılan modeller:** Lojistik Regresyon, SVM, Random Forest, AdaBoost, Gradient Boosting, LightGBM, CatBoost, XGBoost
- **Açıklanabilirlik:** SHAP (küresel önem ve tekil hasta açıklamaları)

## Çalıştırma

```bash
pip install pandas numpy scikit-learn xgboost lightgbm catboost shap matplotlib seaborn
jupyter notebook tiroid_nuks_tahmini.ipynb
```

`Thyroid_Diff.csv` notebook ile aynı klasörde olmalıdır.

## Sınırlılıklar

Veri tek merkezli ve retrospektiftir, test kümesi küçüktür (77 hasta). Sonuçlar klinik karar yerine geçmez. Çok merkezli dış doğrulama gereklidir.

---
**Yazar:** [Emin Burak Öztürk](https://github.com/eminburakozturk) · Balıkesir Üniversitesi, Yapay Zeka Operatörlüğü

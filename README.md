# Market Basket Analysis (MBA)

## 📌 Pengantar
**Market Basket Analysis (MBA)** adalah teknik analisis data yang digunakan untuk memahami pola pembelian pelanggan dengan mencari asosiasi antara produk yang sering dibeli bersama. Teknik ini sering digunakan dalam dunia ritel, e-commerce, dan sistem rekomendasi.

## 🎯 Tujuan Market Basket Analysis
- Mengidentifikasi hubungan antar produk yang sering dibeli bersama.
- Meningkatkan strategi pemasaran dan cross-selling.
- Mengoptimalkan penataan produk di toko.
- Meningkatkan pengalaman pelanggan dengan rekomendasi produk yang lebih baik.

## 🔧 Metode yang Digunakan
Market Basket Analysis menggunakan **Association Rule Mining** yang biasanya menggunakan **Algoritma Apriori** atau **FP-Growth**. Beberapa metrik utama yang digunakan:

1. **Support**: Seberapa sering kombinasi produk muncul dalam transaksi.
   \[ Support(X) = (Jumlah transaksi yang mengandung X) / (Total transaksi) \]

2. **Confidence**: Seberapa sering produk Y dibeli ketika produk X dibeli.
   \[ Confidence(X → Y) = Support(X ∪ Y) / Support(X) \]

3. **Lift**: Seberapa besar peningkatan probabilitas membeli Y saat X sudah dibeli dibandingkan dengan probabilitas Y secara umum.
   \[ Lift(X → Y) = Confidence(X → Y) / Support(Y) \]

## 📊 Contoh Implementasi dengan Python
Berikut adalah contoh sederhana penerapan **Market Basket Analysis** menggunakan pustaka `mlxtend` di Python:

```python
import pandas as pd
from mlxtend.frequent_patterns import apriori, association_rules

# Contoh dataset transaksi
data = {'Milk': [1, 0, 1, 1, 0],
        'Bread': [1, 1, 1, 0, 1],
        'Butter': [0, 1, 1, 1, 1]}
df = pd.DataFrame(data)

# Mencari itemset yang sering muncul
frequent_itemsets = apriori(df, min_support=0.4, use_colnames=True)

# Membuat aturan asosiasi
rules = association_rules(frequent_itemsets, metric="lift", min_threshold=1.0)
print(rules[['antecedents', 'consequents', 'support', 'confidence', 'lift']])
```

## 📌 Kesimpulan
Market Basket Analysis adalah teknik yang sangat berguna dalam dunia bisnis untuk memahami perilaku pelanggan dan meningkatkan strategi pemasaran. Dengan menggunakan metode seperti Apriori atau FP-Growth, kita dapat menemukan hubungan menarik antara produk dan mengoptimalkan strategi penjualan.

---
📢 **Referensi & Dokumentasi**
- [Mlxtend Documentation](http://rasbt.github.io/mlxtend/)
- [Apriori Algorithm - Wikipedia](https://en.wikipedia.org/wiki/Apriori_algorithm)

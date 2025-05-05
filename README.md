📊 Data Mining Summary (Pre-UTS)

Repositori ini berisi ringkasan materi mata kuliah **Data Mining** sebelum Ujian Tengah Semester (UTS), termasuk penggunaan **pandas**, **matplotlib**, serta algoritma klasifikasi seperti **Naive Bayes** dan **Decision Tree**. Cocok untuk referensi belajar cepat dan bisa dijadikan portofolio pembelajaran berbasis data.

## 📚 Daftar Isi

1. [Pengolahan Data dengan Pandas dan Visualisasi dengan Matplotlib](pandas_matplotlib.md)
2. [Klasifikasi dengan Naive Bayes](naive_bayes.md)
3. [Klasifikasi dengan Decision Tree](decision_tree.md)
🧠 Disusun oleh: *[Rendy Wijaya]*  
🗓️ Terakhir diperbarui: Mei 2025
# 🐼 Pandas & 📈 Matplotlib: Data Processing dan Visualisasi

## 1. Pandas
Digunakan untuk membaca, mengelola, dan memproses data. Contoh umum:
```python
import pandas as pd

df = pd.read_csv('data.csv')
df.info()
df.describe()
df['kategori'].value_counts()
import matplotlib.pyplot as plt

df['umur'].hist(bins=10)
plt.title('Distribusi Umur')
plt.xlabel('Umur')
plt.ylabel('Jumlah')
plt.show()

## 📄 Contoh Isi File `naive_bayes.md`
```markdown
# 📘 Naive Bayes Classifier

## Apa itu?
Naive Bayes adalah algoritma klasifikasi berbasis probabilitas (Teorema Bayes) yang mengasumsikan bahwa tiap fitur saling independen.

## Rumus Teorema Bayes
\[
P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
\]

## Implementasi
```python
from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

X = df[['fitur1', 'fitur2']]
y = df['label']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

model = GaussianNB()
model.fit(X_train, y_train)
y_pred = model.predict(X_test)

print("Akurasi:", accuracy_score(y_test, y_pred))
## 📄 Contoh Isi File `decision_tree.md`
```markdown
# 🌳 Decision Tree Classifier

## Konsep
Model yang memetakan keputusan dalam bentuk struktur pohon (if-else berjenjang). Tujuan utamanya adalah membagi dataset menjadi subset berdasarkan fitur tertentu.

## Istilah Kunci
- Root Node: Awal pohon
- Leaf Node: Akhir (kelas/label)
- Gini Index / Entropy: Digunakan untuk menentukan split terbaik

## Contoh Kode
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.tree import plot_tree

model = DecisionTreeClassifier()
model.fit(X_train, y_train)

plt.figure(figsize=(12,8))
plot_tree(model, feature_names=X.columns, class_names=True, filled=True)
plt.show()

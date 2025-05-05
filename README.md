# 📊 Summary Materi Data Mining Sebelum UTS

Mata kuliah Data Mining mencakup proses pengolahan dan analisis data menggunakan berbagai teknik dan tools. Dalam materi sebelum UTS, fokus pembahasan mencakup proses persiapan data, eksplorasi visualisasi data, hingga penerapan dua algoritma klasifikasi: Naive Bayes dan Decision Tree. Semua penerapan menggunakan bahasa pemrograman Python dengan pustaka populer seperti `pandas`, `matplotlib`, dan `scikit-learn`.

---

## 1. 📁 Persiapan Data dengan Pandas

Pandas adalah pustaka Python yang dirancang untuk manipulasi dan analisis data. Ia menyediakan struktur data yang fleksibel dan mudah digunakan.

### a. Membaca Data:
Digunakan untuk mengimpor data dari file eksternal seperti `.csv`, `.xlsx`, atau sumber online.
```python
import pandas as pd 

# Membaca dataset CSV
data = pd.read_csv('data.csv')
data.head()  # Menampilkan 5 baris pertama
```

### b. Pembersihan Data:
Proses ini penting untuk memastikan bahwa data bebas dari nilai kosong, duplikat, atau tipe data yang salah.
```python
# Menghapus nilai kosong
data = data.dropna()

# Menghapus duplikat
data = data.drop_duplicates()

# Mengubah tipe data kolom tanggal
data['tanggal'] = pd.to_datetime(data['tanggal'])
```

### c. Transformasi Data:
Transformasi data dilakukan agar data dapat digunakan dalam model machine learning, seperti encoding untuk data kategorikal.
```python
from sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
data['kategori'] = le.fit_transform(data['kategori'])
```

📉 Catatan:
- Gunakan `LabelEncoder` jika fitur kategorikal hanya memiliki dua nilai atau bersifat ordinal.
- Gunakan `OneHotEncoder` jika fitur memiliki banyak kategori dan tidak ada urutan antar kategori.

### d. Analisis Deskriptif:
Digunakan untuk memahami sebaran data dan hubungan antar variabel.
```python
# Statistik deskriptif
data.describe()

# Korelasi antar variabel
data.corr()
```

---

## 2. 📈 Visualisasi Data dengan Matplotlib

Matplotlib adalah pustaka visualisasi yang umum digunakan untuk membuat grafik statis, animasi, dan interaktif dalam Python.

### a. Plot Dasar:
```python
import matplotlib.pyplot as plt

# Histogram
plt.hist(data['nilai'], bins=10)
plt.title('Distribusi Nilai')
plt.xlabel('Nilai')
plt.ylabel('Frekuensi')
plt.show()
```

### b. Scatter dan Line Plot:
```python
# Scatter plot
plt.scatter(data['x'], data['y'])
plt.title('Plot X vs Y')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()

# Line plot
plt.plot(data['tanggal'], data['nilai'])
plt.title('Perubahan Nilai per Tanggal')
plt.xticks(rotation=45)
plt.show()
```

### c. Boxplot:
Boxplot digunakan untuk melihat distribusi nilai dan outlier.
```python
plt.boxplot(data['nilai'])
plt.title('Boxplot Nilai')
plt.show()
```

📉 Tips Visualisasi:
- Gunakan histogram untuk melihat distribusi satu variabel.
- Gunakan scatter plot untuk melihat hubungan dua variabel numerik.
- Gunakan boxplot untuk mendeteksi nilai pencilan (outlier).

---

## 3. 🤖 Naive Bayes Classifier

Naive Bayes adalah algoritma klasifikasi probabilistik berdasarkan Teorema Bayes dengan asumsi bahwa fitur input saling bebas (independen). Keunggulan Naive Bayes adalah kecepatannya dan efisiensi pada data besar.

### a. Implementasi Model:
```python
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score, classification_report

# Pisahkan fitur dan target
X = data.drop('target', axis=1)
y = data['target']

# Bagi data menjadi data latih dan uji
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Melatih model
model = GaussianNB()
model.fit(X_train, y_train)

# Prediksi dan evaluasi
prediksi = model.predict(X_test)
print('Akurasi:', accuracy_score(y_test, prediksi))
print(classification_report(y_test, prediksi))
```

### b. Jenis Naive Bayes:
- `GaussianNB`: Untuk fitur numerik dan distribusi normal.
- `MultinomialNB`: Untuk data jumlah/frekuensi (teks).
- `BernoulliNB`: Untuk data biner (0/1).

📉 Tips:
Pastikan fitur numerik tidak memiliki skala yang sangat berbeda (normalisasi bisa diperlukan).

---

## 4. 🌳 Decision Tree Classifier

Decision Tree adalah algoritma klasifikasi berbasis pohon yang bekerja dengan membagi dataset menjadi subset berdasarkan fitur input. Decision Tree sangat mudah diinterpretasikan karena hasilnya dapat divisualisasikan.

### a. Visualisasi dan Evaluasi Model:
```python
from sklearn.tree import DecisionTreeClassifier, plot_tree

clf = DecisionTreeClassifier(random_state=42)
clf.fit(X_train, y_train)

# Visualisasi pohon keputusan
plt.figure(figsize=(12,8))
plot_tree(clf, filled=True, feature_names=X.columns, class_names=['0','1'])
plt.show()

# Evaluasi
pred_dt = clf.predict(X_test)
print('Akurasi Decision Tree:', accuracy_score(y_test, pred_dt))
print(classification_report(y_test, pred_dt))
```

### b. Hyperparameter Tuning:
Digunakan untuk menghindari overfitting dan meningkatkan akurasi model.
```python
# Maksimal kedalaman pohon
from sklearn.model_selection import GridSearchCV

param_grid = {'max_depth': [3, 5, 10], 'min_samples_split': [2, 5, 10]}
gs = GridSearchCV(DecisionTreeClassifier(), param_grid, cv=5)
gs.fit(X_train, y_train)
print('Best Parameters:', gs.best_params_)
```

### c. Parameter Penting:
- `max_depth`: Batas kedalaman pohon
- `min_samples_split`: Jumlah minimum sampel untuk membagi node
- `criterion`: 'gini' atau 'entropy' untuk pembagian

---

## 📚 Studi Kasus Mini (Opsional untuk Proyek)
Misalnya, klasifikasi pelanggan berdasarkan perilaku pembelian:

| umur | jenis_kelamin | frekuensi_transaksi | loyalitas |
|------|----------------|----------------------|------------|
| 25   | Pria           | 12                   | 1          |
| 45   | Wanita         | 3                    | 0          |

- **Input**: umur, jenis kelamin, total transaksi
- **Output**: loyalitas (loyal atau tidak)
- **Manfaat**: membantu perusahaan menentukan target promosi
- **Tools**: pandas, matplotlib, scikit-learn (Naive Bayes atau Decision Tree)

---

## ✨ Kesimpulan
- **Pandas** digunakan untuk manipulasi dan pembersihan data sebelum pemodelan.
- **Matplotlib** membantu mengeksplorasi data secara visual, memudahkan deteksi pola dan anomali.
- **Naive Bayes** cocok untuk klasifikasi sederhana dan cepat, namun tidak kuat jika fitur saling bergantung.
- **Decision Tree** menawarkan interpretasi visual dan fleksibilitas tinggi, cocok untuk eksplorasi awal dan presentasi hasil.

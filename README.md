# Ringkasan-UTS
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Ringkasan Materi UTS - Data Science</title>
  <style>
    body { font-family: Arial, sans-serif; line-height: 1.6; padding: 20px; max-width: 1000px; margin: auto; }
    h1, h2 { color: #2c3e50; }
    h3 { color: #34495e; }
    pre, code { background-color: #f4f4f4; padding: 10px; display: block; border-radius: 5px; overflow-x: auto; }
    .section { margin-bottom: 30px; }
  </style>
</head>
<body>
  <h1>📘 Ringkasan Materi UTS</h1>
  <p><strong>Mata Kuliah:</strong> Data Science / Pembelajaran Mesin Dasar</p>
  <p><strong>Topik:</strong> Pandas, Matplotlib, Naive Bayes, Decision Tree</p>

  <div class="section">
    <h2>1. Pandas</h2>
    <p><strong>Pandas</strong> adalah pustaka Python untuk manipulasi dan analisis data berbasis tabel (DataFrame).</p>
    <h3>Contoh Penggunaan:</h3>
    <pre><code>import pandas as pd

df = pd.read_csv('data.csv')
print(df.head())

df['total'] = df['harga'] * df['jumlah']
filtered = df[df['usia'] > 30]</code></pre>
  </div>

  <div class="section">
    <h2>2. Matplotlib</h2>
    <p><strong>Matplotlib</strong> digunakan untuk membuat visualisasi data seperti grafik garis, histogram, dan diagram batang.</p>
    <h3>Contoh:</h3>
    <pre><code>import matplotlib.pyplot as plt

plt.plot(df['tanggal'], df['penjualan'])
plt.title('Grafik Penjualan')
plt.xlabel('Tanggal')
plt.ylabel('Jumlah')
plt.show()

plt.hist(df['usia'], bins=10)
plt.title('Distribusi Usia')
plt.show()</code></pre>
  </div>

  <div class="section">
    <h2>3. Naive Bayes</h2>
    <p>Algoritma klasifikasi berbasis probabilitas. Cocok untuk prediksi seperti deteksi spam, klasifikasi teks, dll.</p>
    <h3>Contoh Penggunaan:</h3>
    <pre><code>from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

X = df[['fitur1', 'fitur2']]
y = df['label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

model = GaussianNB()
model.fit(X_train, y_train)

y_pred = model.predict(X_test)
print("Akurasi:", accuracy_score(y_test, y_pred))</code></pre>
  </div>

  <div class="section">
    <h2>4. Decision Tree</h2>
    <p>Model pembelajaran berbasis pohon yang digunakan untuk klasifikasi dan regresi.</p>
    <h3>Contoh Penggunaan:</h3>
    <pre><code>from sklearn.tree import DecisionTreeClassifier, plot_tree

model = DecisionTreeClassifier(criterion='entropy')
model.fit(X_train, y_train)

plt.figure(figsize=(10, 8))
plot_tree(model, filled=True, feature_names=['fitur1', 'fitur2'])
plt.show()</code></pre>
  </div>

  <div class="section">
    <h2>✅ Alur Analisis</h2>
    <ol>
      <li>Eksplorasi dan pembersihan data (Pandas)</li>
      <li>Visualisasi data (Matplotlib)</li>
      <li>Pelatihan model (Naive Bayes / Decision Tree)</li>
      <li>Evaluasi hasil dan pengambilan keputusan</li>
    </ol>
  </div>
</body>
</html>

# Ringkasan-UTS
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Ringkasan UTS</title>
  <style>
    body { font-family: Arial, sans-serif; max-width: 800px; margin: 40px auto; line-height: 1.6; }
    pre { background: #f4f4f4; padding: 10px; overflow-x: auto; }
    h1, h2 { color: #2c3e50; }
  </style>
</head>
<body>
  <h1>Ringkasan UTS: Pandas, Matplotlib, Naive Bayes, Decision Tree</h1>

  <h2>1. Pandas: Manipulasi Data</h2>
  <p>Pandas adalah pustaka Python untuk manipulasi dan analisis data. Struktur utamanya adalah DataFrame.</p>
  <pre><code>import pandas as pd
df = pd.read_csv('data.csv')
print(df.head())</code></pre>

  <h2>2. Matplotlib: Visualisasi</h2>
  <p>Digunakan untuk membuat grafik seperti histogram, bar, atau line chart.</p>
  <pre><code>import matplotlib.pyplot as plt
plt.hist(df['age'], bins=10)
plt.title('Distribusi Umur')</code></pre>

  <h2>3. Naive Bayes</h2>
  <p>Algoritma klasifikasi berdasarkan probabilitas. Cocok untuk teks seperti spam filter.</p>
  <pre><code>from sklearn.naive_bayes import GaussianNB
model = GaussianNB()
model.fit(X_train, y_train)</code></pre>

  <h2>4. Decision Tree</h2>
  <p>Algoritma pembelajaran mesin berbasis struktur pohon keputusan.</p>
  <pre><code>from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier()
model.fit(X_train, y_train)</code></pre>
</body>
</html>

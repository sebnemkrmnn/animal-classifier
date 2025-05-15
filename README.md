# 🧠 Yapay Zeka Destekli Hayvan Sınıflandırıcı Projesi

Bu proje, Erzurum Teknik Üniversitesi *Bulut Bilişim ve Yapay Zeka Teknolojileri* dersi kapsamında geliştirilmiştir. Amaç; farklı hayvan sınıflarına ait görüntüleri sınıflandırabilen, derin öğrenme temelli ve kullanıcı dostu bir yapay zeka sisteminin geliştirilmesidir.

Kullanıcı, Streamlit arayüzü üzerinden bir görsel yükleyerek anında hangi hayvana ait olduğunu öğrenebilir. Tüm sistem Python ve PyTorch kullanılarak sıfırdan oluşturulmuştur.

---

## 🎯 Proje Hedefleri

- Görüntü verilerini etkili biçimde işleyerek bir **CNN (Convolutional Neural Network)** modeli eğitmek  
- Eğitilen modeli `.pth` uzantılı formatta kaydetmek ve dışarıdan yeniden yüklenebilir hale getirmek  
- Modeli kullanıcı dostu bir **web arayüzü (Streamlit)** ile entegre etmek  
- Kullanıcının yüklediği görseli canlı olarak sınıflandırmak ve sonuçları net bir şekilde sunmak  

---

## 🧰 Kullanılan Teknolojiler

| Alan            | Araç / Kütüphane            |
|------------------|------------------------------|
| Derin Öğrenme     | PyTorch (`torch`, `torchvision`) |
| Görüntü İşleme    | Pillow (`PIL`) + `transforms`    |
| Arayüz            | Streamlit                    |
| Veri Seti         | [Animals-10 Dataset](https://www.kaggle.com/datasets/alessiocorrado99/animals10) |
| Yardımcılar       | tqdm, os, random_split        |

---

## 🧠 Model Mimarisi

Model mimarisi `SimpleCNN` adında bir sınıf olarak tanımlanmış olup şu katmanları içerir:

```python
Conv2D(3 → 32) → ReLU → MaxPool2d  
Conv2D(32 → 64) → ReLU → MaxPool2d  
Flatten → Linear(64×32×32 → 128) → ReLU → Linear(128 → 10)
```
Eğitim sonucunda oluşan ağırlıklar `.pth` dosyası olarak kaydedilmiştir.  
📌 **Not:** Model `.pth` dosyası GitHub'a yüklenmemiştir.  
💾 **Modeli eğitmek için `train_model.ipynb` dosyasını çalıştırınız.**

---

## 📦 Proje Dosya Yapısı

```
├── app.py                    # Streamlit arayüz kodu
├── model.py                  # Model sınıfı ayrı dosyada  tutulabilir
├── train_model.ipynb         # Modelin eğitildiği notebook
├── data_preprocess.ipynb     # Görsellerin dönüştürüldüğü notebook
├── rename_folders.ipynb      # Klasör isimleri İngilizceye çevriliyor
├── simple_cnn_animals.pth    # (İsteğe bağlı, yüklenmediyse eğitimle oluşturulur)
├── README.md                 # Projenin tanımı ve dökümantasyonu
```

---

## 🐾 Sınıflandırılan Hayvanlar

Model şu 10 sınıfı başarıyla ayırt edebilmektedir:

- 🐶 Dog  
- 🐱 Cat  
- 🐴 Horse  
- 🐘 Elephant  
- 🐄 Cow  
- 🐥 Chicken  
- 🐏 Sheep  
- 🐛 Butterfly  
- 🕷️ Spider  
- 🐿️ Squirrel

---

## 🧪 Model Eğitimi

Model, 80/20 oranında train-validation ayrımı yapılarak 10 epoch boyunca eğitilmiştir.  
Kullanılan loss fonksiyonu: `CrossEntropyLoss`  
Optimizer: `Adam (lr=0.001)`  
Batch Size: `32`

---

## 🚀 Uygulamanın Çalıştırılması

### Gerekli kütüphaneleri yükleyin:

```bash
pip install torch torchvision streamlit pillow tqdm
```

### Streamlit uygulamasını başlatın:

```bash
streamlit run app.py
```

Tarayıcınızda otomatik olarak arayüz açılır. Görsel yüklediğinizde model tahmin sonucunu anında gösterecektir.

---

## 📷 Arayüzden Örnek Ekran

> Uygulama, kullanıcıdan bir hayvan resmi alır ve tahmin edilen sınıfı ekranda gösterir.

```
🐾 Hayvan Sınıflandırıcı AI  
📷 Resim Yükle → 🧠 Tahmin: **DOG**
```

---

## 👤 Hazırlayan

- **Adı Soyadı:** Şebnem Karaman 
- **Üniversite:** Erzurum Teknik Üniversitesi  
- **Ders:** Bulut Bilişim ve Yapay Zeka Teknolojileri  
- **Yıl:** 2025

---

## 📌 Notlar

- Bu proje eğitsel amaçla geliştirilmiştir.
- Streamlit, yerel olarak tarayıcıda çalışır ve özel bir sunucu kurulumu gerektirmez.
- Veri seti Kaggle üzerinden temin edilmiştir.
- Modeli yeniden oluşturmak için `train_model.ipynb` dosyasını çalıştırmanız yeterlidir.



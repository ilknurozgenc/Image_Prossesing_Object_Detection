# 🚀 **GÖZLÜKLÜ VS GÖZLÜKSÜZ: Yüzde Gözlük Dedektörü\!** 🕶️

Bu proje Tech İstanbul ve Ecodation Akademi iş birliğinde yapılmış bir görüntü işleme bootcamp görevidir. Makinelerin görme gücünü kullanarak (yani **YOLOv8** ile\!) insanların gözlüklü mü yoksa gözlüksüz mü olduğunu anlık olarak tespit etmeyi amaçlayan  bir **Nesne Tespiti (Object Detection)** projesidir.\!

## 🎯 Projenin Amacı 

yapay zekayı kullanarak hızlı, isabetli ve canlı (webcam'den\!) çalışabilen bir model geliştirmek.

## Kullanılan Teknolojiler

| Teknoloji | Görev | Not |
| :--- | :--- | :--- |
| **YOLOv8** | Ana Nesne Tespit Modeli | Hız ve doğrulukta zirve\! |
| **Python** | Kodlama Dili | Her şeyin beyni. |
| **OpenCV** | Görüntü İşleme | Webcam ve kutu çizimleri için. |
| **Google Colab** | Eğitim Ortamı | GPU gücüyle modeli hızlıca eğittik. |


## 🖼️ Veri Seti

Modeli eğitmek için, bir miktar resim toplandı ve her bir yüze elle, makesense.ai ile tek tek **Bounding Box** (sınır kutusu) çizerek etiketlendi.

### Sınıflar (Modelle Konuştuğumuz Dil)

Model sadece iki şeyi ayırt etmeyi öğrendi:

  * **0: `glasses`** (Gözlüklü Kişi)
  * **1: `no_glasses`** (Gözlüksüz Kişi)

### Veri Hazırlık Süreci

Tüm resimler ve etiketler, **YOLO formatında** (merkez koordinatları ve normalize edilmiş boyutlar) hazırlandı ve modelin eğitimden önce hiç görmediği resimlerle test edilmesi için **Train, Val (Doğrulama) ve Test** olarak bölündü.


## 📈 Modelin Performansı

Model, **50 Epoch** boyunca eğitildikten sonra oldukça güçlü sonuçlar verdi.
<img width="1200" height="600" alt="Karışıklık_Matrisi_Confusion_Matrix" src="https://github.com/user-attachments/assets/11e15168-0072-41de-9fce-1bd3f3ca4d9d" />


## 📹 Nasıl Çalışır?

Eğitilmiş modelin en iyi ağırlık dosyası (`best.pt`) kullanılarak, ister bir resim dosyası, ister canlı webcam akışı üzerinde anlık tespit yapabiliriz.

### Canlı Tespit Kodu (Colab/Lokal)

Modeli yükleyip, her gelen video karesi üzerinde tahmin yapıyoruz ve tespit edilen kutuları (`x1, y1, x2, y2`) ve etiketi (`glasses` veya `no_glasses`) OpenCV ile çizdiriyoruz.

```python
# Model ağırlıklarını yüklüyoruz
model = YOLO('best.pt')

# Canlı döngüde
results = model(frame, conf=0.5) 

# Kutu çizimi ve etiketleme işlemi...
```


## 🧑‍💻 Katkıda Bulun\! (Gel, Birlikte Geliştirelim\!)

Proje hala geliştirilebilir\! Daha fazla veri, farklı YOLO modelleri (YOLOv8m, l, x gibi) veya daha iyi optimizasyonlar deneyerek performansı artırabiliriz.

Geliştirmeye katkıda bulunmak istersen, çekinme\!

1.  Bu repoyu **Fork** et.
2.  Yeni bir **Branch** oluştur.
3.  Değişikliklerini yap ve **Pull Request** gönder.

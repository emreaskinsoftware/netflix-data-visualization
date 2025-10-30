#  Netflix Veri Seti Analizi ve Görselleştirme Projesi

**Amaç:** Bu proje, Kaggle'dan alınan "Netflix Movies and TV Shows" veri setini kullanarak Keşifçi Veri Analizi (EDA) yapmayı, platformun içerik stratejisini anlamayı ve bulguları profesyonel bir şekilde görselleştirmeyi amaçlamaktadır.

**Portföydeki Etkisi:** Bu proje; veri temizleme, özellik mühendisliği, veri görselleştirme (Seaborn & Matplotlib) ve analiz bulgularını "hikayeleştirme" becerilerimi göstermektedir.

**Kullanılan Araçlar:**
* Python
* Pandas (Veri manipülasyonu ve temizliği için)
* Matplotlib & Seaborn (Veri görselleştirmesi için)
* Google Colab (Analiz ortamı olarak)

---

## 🧭 Analiz Adımları (Workflow)

Proje, bir veri bilimci yaklaşımıyla 3 ana adımda tamamlanmıştır:

1.  **Veri Yükleme ve Hazırlık:** Veri seti Kaggle API kullanılarak doğrudan Google Colab ortamına çekildi. İlk incelemede (`.info()`, `.head()`) eksik veriler ve yanlış veri tipleri tespit edildi.
2.  **Veri Temizleme:**
    * `director`, `cast`, `country` gibi çok fazla eksik veri içeren sütunlar "Unknown" ile dolduruldu.
    * `date_added`, `rating` gibi az sayıda eksik veri içeren satırlar veri setinden çıkarıldı.
    * `date_added` sütunundaki " " (boşluk) gibi gizli kirli veriler `.str.strip()` ile temizlendi ve `datetime` tipine dönüştürüldü.
    * `added_year` gibi analiz için yeni özellikler (`feature`) türetildi.
3.  **Keşifçi Veri Analizi (EDA) ve Görselleştirme:** Temizlenen veri seti, temel iş sorularını yanıtlamak için görselleştirildi.

---

## 📊 Bulgular ve İçgörüler (Analysis & Insights)

Analizden elde edilen temel bulgular ve stratejik yorumlar aşağıdadır.

### 1. İçerik Türü Dağılımı: Film Ağırlıklı Strateji

Platformdaki içeriklerin ezici çoğunluğu Filmlerden (Movies) oluşmaktadır. Katalogda, Dizi (TV Show) sayısının yaklaşık 2 katından fazla Film bulunmaktadır.

<img width="715" height="564" alt="film-dizi" src="https://github.com/user-attachments/assets/fb6ada80-edd9-4e86-91b1-3199874294ed" />


### 2. Yıllara Göre İçerik Artışı: 2019 Zirvesi

Netflix'in platforma içerik ekleme hızı, 2016'dan itibaren muazzam bir artış göstermiş ve **2019 yılında zirveye** ulaşmıştır.

* **İçgörü:** 2020 ve 2021'deki düşüş, Pandemi etkilerine ek olarak, bu veri setinin **Eylül 2021'de** oluşturulmuş olmasından kaynaklanmaktadır. Yani 2021 verisi tam bir yılı kapsamamaktadır.

<img width="1180" height="664" alt="içerik-yıl" src="https://github.com/user-attachments/assets/4d6afa15-9376-4474-aa50-d10b53133d63" />


* **Stratejik Farklılık:** Bu büyüme incelendiğinde, Dizi eklemelerinin her yıl **istikrarlı (stabil)** bir artış gösterdiği, ancak Film alımlarının 2017-2019 arasında çok daha **agresif ve dalgalı** olduğu görülmüştür. Bu, Netflix'in film kütüphanesini hızla büyütme stratejisini göstermektedir.

<img width="1335" height="741" alt="film-dizi-yıl" src="https://github.com/user-attachments/assets/539d110b-1bef-4e69-a6bb-ead4971aa085" />


### 3. İçerik Türleri (Genre): "Uluslararası" ve "Drama" Hakimiyeti

Platformdaki en popüler kategori **"International Movies" (Uluslararası Filmler)** olmuştur. Bu bulgu, Netflix'in küresel (global) pazara ne kadar önem verdiğini kanıtlamaktadır. Bunu "Dramalar" ve "Komediler" takip etmektedir.

<img width="1184" height="716" alt="pop-10-tür" src="https://github.com/user-attachments/assets/394bbe52-659c-4888-adbe-9d0e667de150" />


### 4. Film Süreleri: Klasik 100 Dakika Ortalaması

Film sürelerinin dağılımı incelendiğinde (Histogram), verilerin **simetrik bir dağılım** gösterdiği görülmüştür.

* **Ortalama Süre (Mean):** 100 Dakika
* **Medyan (Ortanca Değer):** 99 Dakika
* Ortalama ve Medyan'ın birbirine çok yakın olması, uç değerlere (min: 3 dk, max: 312 dk) rağmen veri yığılmasının merkezde toplandığını doğrulamaktadır.
* **İçgörü:** Filmlerin %75'i 114 dakikadan kısadır. Bu, platformun standart 90-120 dakikalık film formatına sadık kaldığını göstermektedir.

<img width="1015" height="636" alt="Film-süreleri" src="https://github.com/user-attachments/assets/07abe965-2e42-4c23-b6ea-997c370dd03e" />


### 5. Dizi Stratejisi: "Mini Dizi" ve "Tek Sezonluk" İçerik Patlaması

Dizi analizinde en çarpıcı bulgu, **1 Sezonluk** dizilerin, en yakın rakibi olan 2 sezonluk dizilerden bile **4 kat daha fazla** olmasıdır.

* **İçgörü (Hipotez):** Bu "uzun kuyruklu" dağılım, Netflix'in bir stratejisini yansıtmaktadır:
    1.  İzleyiciden düşük bağlılık (commitment) isteyen, hızlı tüketilebilir ("binge-watch") **Mini Dizilere** ağırlık verilmektedir.
    2.  Yüksek bütçeli ve çok sezonlu riskli yapımlar yerine, uluslararası pazarlardan daha çok sayıda tek sezonluk içerik alınmaktadır.

<img width="1079" height="636" alt="Dizi-sezon-sayısı" src="https://github.com/user-attachments/assets/9d7bd442-4753-493c-9479-3eca130db46f" />


### 6. Coğrafi Dağılım: ABD ve Hindistan Dominasyonu

İçeriklerin üretildiği ülkelere bakıldığında, beklendiği gibi Netflix'in anavatanı **Amerika Birleşik Devletleri (ABD)** açık ara zirvededir.

* **Stratejik İçgörü:** Asıl dikkat çekici nokta **Hindistan'ın** 2. sırada olmasıdır. Bu bulgu, "En Popüler Türler" analizindeki "International Movies" liderliğini ve "En Üretken Yönetmenler" listesindeki Hintli yönetmenlerin (örn: Rajiv Chilaka) varlığını desteklemektedir. Netflix, Hindistan pazarına ve Hint içeriğine devasa bir yatırım yapmaktadır.
* Türkiye, bu listede 14. sırada yer almaktadır.

<img width="1114" height="795" alt="Ülkeler" src="https://github.com/user-attachments/assets/3fd5220b-58f0-40dc-a9aa-ffb858943772" />


---

## 🎯 Proje Sonucu ve Değerlendirme

Bu analiz, Netflix'in içerik stratejisinin **"çeşitlilik"** ve **"küreselleşme"** üzerine kurulu olduğunu net bir şekilde ortaya koymuştur. Platform, ABD pazarındaki hakimiyetini korurken, Hindistan gibi dev pazarlarda yerel ve uluslararası içeriklerle agresif bir büyüme sergilemektedir. Film kütüphanesi klasik sürelere bağlı kalırken, dizi pazarında ise çabuk tüketilen, 1 sezonluk mini dizi formatı domine etmektedir.

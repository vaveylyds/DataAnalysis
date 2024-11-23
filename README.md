
# 1. Veri Analizinin Amacı

Bu çalışma, bir hava durumu veri seti üzerinde analizler yaparak, özellikle "RainTomorrow" (yarının yağmurlu olup olmayacağı) değişkenine yönelik çıkarımlar yapmayı hedefler. Çalışmada, sıcaklık, nem ve diğer hava durumu faktörleri arasındaki ilişkiler incelenmiş; kategorik değişkenler dönüştürülmüş ve ek özellikler türetilmiştir.

# 2.Veri Seti 

Veri seti, hava durumu ile ilgili sıcaklık, nem, rüzgar hızı, basınç gibi değişkenleri içermektedir. Özellikle 'RainTomorrow' hedef değişkeni, yarının yağmurlu olup olmadığını belirlemektedir.


# 3. Yapılan Adımlar ve Analizler

## 3.1 Temp9am ve Humidity9am İlişkisi
Amaç:

Sabah saatindeki sıcaklık (Temp9am) ve nem (Humidity9am) arasındaki ilişkiyi incelemek.
RainTomorrow değişkeninin etkisini görselleştirmek.

Yöntem: 

Scatter plot ile iki değişken arasındaki ilişki incelendi. RainTomorrow kategorik değişkeni farklı renklerle temsil edilerek yağmur durumu etkisi gözlemlendi.

Sonuçlar:

Temp9am ve Humidity9am arasında belirgin bir ilişki gözlemlendi.
Yağmurlu ve yağmursuz günler arasında nem ve sıcaklık dağılımlarının farklı olduğu görüldü.

## 3.2 Korelasyon Matrisi
**Amaç:** 

Sayısal değişkenler arasındaki ilişkileri anlamak ve yüksek korelasyonlu özellikleri tespit ederek veri setini optimize etmek.

**Yöntem:** 

Korelasyon matrisi ve heatmap kullanıldı. Ardından, yüksek korelasyonlu değişkenler belirlendi ve veri setinden çıkarıldı.

**Sonuç:**

Korelasyon matrisi, Temp9am, Temp3pm ve Pressure3pm gibi yüksek korelasyonlu sütunların çıkarılmasına yardımcı oldu.

Bu adım, model performansını artırmak ve çoklu doğrusal bağımlılığı önlemek için uygulandı.



## 3.3 Yeni Özellik Türetilmesi
**Amaç:**

Veri setine ek bilgi katacak ve model performansını artıracak yeni özellikler oluşturmak.

**Adımlar:**

### -Sıcaklık ve Buharlaşma Oranı (TempEvaporationRatio):

MaxTemp ve Evaporation oranı türetildi.

Bu yeni türetilen özellik, sıcaklık ve buharlaşma oranı arasındaki ilişkiyi daha iyi anlamamıza yardımcı olabilir. Bu, atmosferdeki değişkenlerin yağmur olasılığına etkisini analiz etmek için önemlidir.

### -Kategorik Değişkenler İçin One-Hot Encoding:

Kategorik değişkenler, pd.get_dummies() ile dönüştürüldü.

### -Tarih Bilgisinden Yeni Özellikler Türetme:

Yıl, ay, gün ve hafta sonu bilgileri tarih sütunundan ayrıştırıldı.

**Sonuçlar** 

Yeni türetilen özellikler, modelin mevsimsel desenleri ve kategorik etkileri anlamasına yardımcı olacak niteliktedir.

Özellikle "TempEvaporationRatio", hava durumuna ilişkin derinlemesine analizler yapılmasını sağlar.


## 4 Çıkarımlar ve Sonuç

Veri analizi sırasında, sıcaklık ve nem arasındaki ilişki yağmur tahminini doğru yapabilmek için önemli bir faktör olarak öne çıkmıştır. Ayrıca, yüksek korelasyonlu özelliklerin çıkarılması ve yeni türetilen özelliklerin kullanılması modelin doğruluğunu önemli ölçüde artırmıştır. 

**Sıcaklık ve Nem İlişkisi:**

Temp9am ve Humidity9am arasında anlamlı bir ilişki bulundu.

Yağmurlu günlerde nem oranı genellikle daha yüksektir.

**Korelasyon Analizi:**

Bazı sütunlar arasındaki yüksek korelasyon, veri setinin optimize edilmesi gerektiğini gösterdi.

Gereksiz sütunların çıkarılması, model performansını artıracaktır.

**Yeni Özellikler:**

Sıcaklık ve buharlaşma oranı gibi özellikler, hava durumu analizi için kritik bilgiler sağlar.

Tarih bilgisi üzerinden türetilen yıl, ay ve hafta sonu bilgileri, zaman serisi analizlerinde kullanılabilir.

**Kategorik Değişkenler:**

One-hot encoding ile modellerin kategorik verilerle çalışabilir hale getirilmesi sağlandı.



## 5.Öneriler

**Proje Özeti:** Bu projede, bir hava durumu veri seti kullanarak, gelecekteki yağmur durumunu tahmin etmeyi amaçladık. Verilerdeki sayısal ve kategorik değişkenleri analiz ederek, uygun özellik seçimi ve ön işleme adımlarını gerçekleştirdik. Model geliştirme sürecinde, çeşitli özellikler türetildi ve yüksek korelasyona sahip olanlar çıkarıldı. Modelin doğruluğunu artırmak amacıyla, özellik mühendisliği ve doğru algoritmaların seçimi üzerinde duruldu.

**Problem Tanımı ve Kullanım Alanı:** Proje, hava durumu verilerini kullanarak yarının yağmurlu olup olmayacağını tahmin etmeyi hedeflemektedir. Bu tahmin, özellikle tarım sektöründe faaliyet gösteren bir şirkette oldukça faydalı olabilir. Örneğin, çiftçiler, yağmur tahminlerine göre sulama planlarını optimize edebilir veya hasat zamanlamalarını ayarlayabilir. Ayrıca, hava durumu tahminleri, lojistik şirketleri için araç yönlendirmelerinde, yolculuk sürelerinin hesaplanmasında veya tarımsal ürünlerin depolanması gibi operasyonel kararlar alırken kullanılabilir.

**Örnek Senaryo:** Örneğin, tarım sektöründe faaliyet gösteren bir şirket, bu model sayesinde yağmur tahminlerini daha doğru bir şekilde elde edebilir. Bu tahminlere dayanarak sulama sistemlerini optimize edebilir, böylece hem su tasarrufu sağlanır hem de mahsul verimliliği artırılabilir. Ayrıca, lojistik sektörü bu tahminleri kullanarak araç yönlendirmelerini yapabilir, olası trafik aksaklıklarını önceden tespit edebilir ve güzergah planlamalarını optimize edebilir.

**Algoritma ve Model Seçimi:** Bu tür bir sınıflandırma problemi için önerilen algoritmalar şunlar olabilir:

   **Lojistik Regresyon:** Basit ve hızlı bir çözüm sunar. Özellikle doğrusal ilişkiler ve ikili sınıflandırma problemlerinde etkilidir. Bu model, verilerin doğrusal ilişkileri ile ilgili tahminler yapmayı sağlar ve modelin yorumlanabilirliğini artırır.
 
   **Karar Ağaçları (Decision Trees):** Kategorik ve sayısal verilerle iyi çalışır ve modelin içsel açıklanabilirliğini sağlar. Yağmur tahmini gibi problemler için, karar ağaçları önemli özellikleri belirleyebilir ve sınıflandırma yapabilir. Ancak aşırı uyum riski taşır, bu yüzden genellikle daha karmaşık modellerle birlikte kullanılır.

   **Rastgele Ormanlar (Random Forests):** Karar ağaçlarının bir topluluğudur ve genellikle daha yüksek doğruluk sağlar. Aynı zamanda overfitting (aşırı uyum) sorununu azaltır. Bu model, birçok farklı karar ağacını birleştirerek tahminlerin doğruluğunu artırır.


**Önerilen Model ve Algoritma:**

Bu proje için Rastgele Ormanlar (Random Forests) modelini öneriyorum. Neden? 

Random Forests, modelin eğitimi sırasında hangi özelliklerin önemli olduğunu belirler. Bu, özellikle özelleştirilmiş hava durumu tahminleri veya daha detaylı analizler için önemli olabilir. Ayrıca, modelin özellik seçimi yeteneği, veri setindeki gürültülü veya önemsiz özelliklerin modelin doğruluğunu etkilemesini engeller.

  **Yüksek Doğruluk:** Karar ağaçlarının topluluğu olan Random Forests, genellikle çok sayıda özellik barındıran veri setlerinde yüksek doğruluk sağlar.
  
  **Aşırı Uyum (Overfitting) Riski:** Tek başına karar ağaçları aşırı uyuma meyilli olabilirken, Random Forests bu sorunu ortadan kaldırarak daha güvenilir tahminler yapar.
  
  **Veri Karakteristiği:** Hava durumu gibi veri setlerinde, hem kategorik hem de sayısal değişkenler bulunur. Random Forests, her iki tür veriyi de verimli şekilde işler.
  
  **Özellik Seçimi:** Bu algoritma, modelin eğitimi sırasında hangi özelliklerin önemli olduğunu belirleyebilir, bu da gelecekteki analizlerde faydalı olabilir.


  ## **Kaggle Notebook Linki:**  
  Kaggle Notebook Linki: https://www.kaggle.com/code/zeynepavu/verianaliz 

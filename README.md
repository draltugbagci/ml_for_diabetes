# Diabet verisi üzerinde makine öğrenmesi

#### Bu notebook makine öğrenmesi için temel bir kalıp oluşturmak ve öğrenim amacıyla hazırlandı. 

### Makine Öğrenmesi için temel adımlar:
1. Veriyi indirme ve inceleme
2. Veri ön işleme
3. Model belirleme, eğitim ve hiperparametre ayarlama ve gerçek veri üzerinde test etme

NOT: import işlemi bağlantıları göz önünde tutmak için her bir adımda yapıldı

# 1. Veriyi indirme ve inceleme

  Bir makine öğrenmesinin en önemli aşaması belki de veri seti oluşturma olsa da bu çalışmada daha önceden oluşturulmuş veri ile çalışarak makine öğrenmesinin temelleri üzerinde yoğunlaşmak başlangıç için daha mantıklı. Veri setinini yükledikten sonra ilk aşamada veriyi anlamak gerek. Bu veri hangi özelliklerden oluşuyor, özellikler ne tip veriler içeriyor, bağımlı ve bağımsız değişkenler neler gibi soruların cevapları aranmalı.
  Veriyi anlamak için yapılması gerekenler:
    1. head() ya da tail() gibi bir metodla veriye ilk bakış
    2. info() ile verinin sayısı, özellkiler ve her bir özeeliğin ne türden veri içerdiği
    3. describe() ile ortalama, standart sapma gibi istatistiksel özellikler
    4. veri dağılımı ve özelliklerin birbirleriyle ilişkilerrini görselleştirmek için, seaborn kütüphanesinin pairplot(), heatmap(), kdeplot(), histplot() gibi metodları

# 2. Veri ön işleme

  Bu aşama verinin makine öğrenmesi modeliyle işlenmesi için yapılması gereken düzeltmeleri içerir.

  1. Eksik veri (missing value): veri setinde bazı örneklerde boşluklar veya yanlış veriler olabilir. Bunların uygun bir yöntemle doldurulması ya da bu örneklerin veri setinden çıkartılması
  2. Aykırı veri (outliers): aşırı değerli veriler bazı makine öğrenmesi modellerinin sonucunu bozabilir. Bu örneklerin de ya değiştirlmesi ya da veriden çıkartılması gerekir.
  3. Veri setindeki bağımlı değişken (modelin tahmin edeceği değişken) ile bağımsız değişkenlerin belirlenmesi
  4. Eğitim ve test verisi ayrımı: bir makine öğrenmesinin veriyi ezberlememesi (overfitting) için görmediği verilerle test yapılması gerekir. BU yüzden eğitim verisi ile test verisi ayrılır.
  5. Standardizasyon veya normalizasyon: sırasıyla ortalaması 0 standart sapması 1 olan bir dağılıma indirme ya da 0 ile 1 arası bir dağılıma indirme. Bazı makine öğrenmesi modelleri veriyi bu şekilde ister.

# 3. Modeli eğitme

  Makine öğrenmesi modelleri genellikle derin öğrenme modellerine göre daha hızlı çalışan modellerdir, bu bize istediğimiz modelleri test edebilme olanağı sunar. Tek bir model belirlemek zorunda değiliz, çok sayıda model çalıştırıp, en iyi sonuç verenler üzerinde devam edebiliriz. Ancak burada eğitim için  tek bir model belirleyerek başlayacağım:
  
  1. Model belirleme: karar ağacı ile başladım
  2. Eğitim: fit() ile bağımsız değişkenler ve bağımlı değişken ile bağlantı oluşturulur (bu yöntemde veri tek parça olarak işlenir), cross_val_score ile veri cv=10 örneğinde olduğu gibi 10 ayrı sete bölünerek eğitim yapılır, GridSearchCV ile de farklı parametrelerle model çalıştırılıp en iyi parametreler belirlenir.
  3. Hiperparametre ayarları: en iyi parametreler bulunduktan sonra bu parametreli model bizim gerçek veri ile test edeceğimiz modlimizdir
  4. Gerçek veriyle test etme: modelin tahmin yapabilmesi için örnek veri, eğitim yapılan veri gibi sunulmalıdır, standardize edilmiş veriyle eğitim yapılmışse sunulan da böyle olmalı.
  5. Birden fazla modeli test etmek için yaptığımız şey model listesi üzerinde bir for döngüsü kurmaktan ibaret, temel mantık değişmiyor.

# Sonsöz: 

  Bu temel bir yaklaşım olarak sunulsa da bazı yerlerde eksikler, yanlışlar olabilir. Bu yaklaşım her tür veriye uygun olmayabilir. Ancak bir yerden başlarsınız ve geliştirdikçe öğrenirsiniz. Bu paylaşım öğrenme sürecinin bir aşamasıdır ve geri dönüşler ilerleme için mutlak gereklidir.



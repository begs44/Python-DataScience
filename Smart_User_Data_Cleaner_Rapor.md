# Teknik Rapor: Smart User Data Cleaner

Ham ve hatalı kullanıcı verilerini Python'un string metodlarıyla temizleyip çıktılar üreten veri işleme projesi.

## 1.Giriş

### Projenin Amacı
Bu proje, gerçek hayatta sıkça karşılaşılan hatalı kullanıcı verilerini temizlemek için geliştirilmiştir. Form verisi temizleme, kullanıcı kayıt normalizasyonu gibi alanlarda kullanılabilir.

### Veri Temizlemenin Önemi
Gerçek hayatta sistemlere girilen veriler çoğunlukla tutarsız, eksik veya hatalı olabilmektedir. Büyük-küçük harf karmaşası, fazladan boşluklar ya da yanlış formatta girilmiş sayısal veriler, yazılımın hatalı çalışmasına neden olabilir. Bu hatalar; zaman kaybına, yanlış analizlere ve maliyet artışına yol açabilir. Bu nedenle veri temizleme, yazılım projelerinin önemli bir adımıdır.

### String İşlemlerinin Rolü
Metin tabanlı verilerin işlenmesinde Python'un string metodları son derece güçlü araçlar sunar. Boşluk temizleme, büyük-küçük harf dönüşümü, parçalama ve belirli karakterlere erişim gibi işlemler; döngü veya koşul ifadesi kullanılmadan yalnızca string metodları ve slicing aracılığıyla gerçekleştirilebilir.

## 2.Kullanılan Python Konuları

Değişkenler: Bir verinin programa tanıtılması için kullanılan isimlendirilmiş alanlardır. Kullanılan veri tipleri string, int ve float'tır.

String Veri Tipi: Metin içerikli verilerin saklandığı veri tipidir. Ham verinin tamamı başlangıçta string olarak geldiğinden, tüm temizleme işlemleri bu tip üzerinde gerçekleştirilmiştir. İsim, soyisim ve e-posta bu tipe örnek gösterilebilir.

int ve float Dönüşümleri: String tipindeki sayısal veriler üzerinde matematiksel işlem yapılabilmesi için tip dönüşümü zorunludur. int() tam sayı, float() ise ondalıklı sayı elde etmek için kullanılır.

String Slicing: String içindeki karakterlere indeks numarası aracılığıyla erişme yöntemidir. Başlangıç ve bitiş indeksleri belirtilerek stringin yalnızca istenilen kısmı elde edilebilir. Bu projede e-posta adresinden ilk 3 karakterin alınmasında kullanılmıştır.

String Metodları
- strip(): Metnin başında ya da sonunda yer alan gereksiz boşlukları kaldırır. Ham verilerde sıkça karşılaşılan bu sorun, split() öncesinde mutlaka giderilmelidir.
- split(): Metni belirtilen bir ayraç karakterine göre parçalara böler. Bu projede ; karakteri ayraç olarak kullanılmış ve veri 4 ayrı parçaya ayrılmıştır.
- lower(): Metindeki tüm harfleri küçük harfe dönüştürür. Büyük-küçük harf tutarsızlıklarını gidermek için ilk adım olarak uygulanır.
- title(): Her kelimenin yalnızca ilk harfini büyük yapar. İsim ve soyisim gibi verilerin standart bir görünüme kavuşturulmasında tercih edilir.
- find(): Metin içinde aranan bir karakterin indeks numarasını döndürür. Bu projede @ işaretinin konumunu belirlemek amacıyla kullanılmıştır.

## 3.Veri Temizleme Süreci

Ham Verideki Problemler
- Büyük-küçük harf düzensizliği: "AhMeT yILMAZ" gibi tutarsız yazımlar
- Fazla boşluklar: verinin başında, sonunda ve alanlar arasında gereksiz boşluklar
- String olarak gelen sayısal veriler: "23" ve "1.78" değerlerinin matematiksel işlem yapılabilmesi için dönüştürülmesi gerekmektedir
- Büyük harfli e-posta: "ahmetYILMAZ@GMAIL.Com" standart dışı bir formattır

Adım Adım Çözüm Süreci
1. Genel Temizlik: strip() ile baş ve son boşluklar temizlendi. split(";") ile veri 4 parçaya ayrıldı.
2. İsim-Soyisim: lower() ile tüm harfler küçültüldü, title() ile her kelimenin ilk harfi büyütüldü.
3. Yaş İşleme: int() ile tam sayıya çevrildi, 10 eklenerek float() ile ondalıklı formata getirildi.
4. Boy Analizi: float() ile dönüşüm yapıldı, 100 ile çarpıldı ve round() ile kayan nokta hatası önlendi.
5. E-posta Temizleme: lower() ile küçük harfe çevrildi, slicing ile ilk 3 karakter kullanıcı kodu olarak alındı.

## 4.Sonuç ve Değerlendirme

Bu proje kapsamında ham ve tutarsız bir kullanıcı verisi; isim-soyisim normalizasyonu, yaş ve boy hesaplaması, e-posta kullanıcı kodu üretimi olmak üzere 5 temel adımda başarıyla temizlenmiştir.

Gerçek Hayatta Kullanım Alanları
- Form verisi temizleme: web formlarından gelen tutarsız kullanıcı girişlerinin standartlaştırılması
- CSV ön-işleme: elektronik tablolardaki bozuk verilerin düzeltilmesi
- Kullanıcı kayıt normalizasyonu: farklı kanallardan gelen kayıt verilerinin tek formata indirgenmesi

Kazanılan Python Becerileri
Bu proje sayesinde string metodlarını zincirleme kullanma (örn. strip().lower().split()), veri tipi dönüşümlerini doğru sırayla uygulama ve kayan nokta hassasiyetini yönetme becerileri kazanılmıştır. Bunun yanı sıra if, for ve kullanıcı tanımlı fonksiyon gibi ileri seviye yapılara başvurmadan yalnızca temel Python araçlarıyla gerçek bir veri problemi çözülmüştür.
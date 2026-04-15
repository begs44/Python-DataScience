# Teknik Rapor: Smart Order Management System

## 1. Giriş

### Projenin Amacı
Bu rapor, bir e-ticaret yönetim sisteminin arka planında verilerin nasıl sınıflandırıldığını, korunduğunu ve işlendiğini teknik bir perspektifle ele almaktadır. Projenin temel odağı, ham verinin algoritma dostu yapılara dönüştürülürken hangi mantıksal süzgeçlerden geçtiğini açıklamaktır.

## 2. Koleksiyonların Gerçek Hayattaki Karşılığı

Yazılımdaki veri yapılarını anlamak için günlük hayattaki karşılıklarına bakmak, sistemin çalışma mantığını kavramayı kolaylaştırır:

- List (Liste):Bir market alışveriş listesi gibidir. Ürünlerin eklenme sırası korunur ve eğer sepete iki tane "Mouse" atarsanız, listede iki ayrı girdi olarak görünürler. Dinamik ve esnektir.
- Set (Küme):Bir okulun öğrenci kütüğü veya bir konferansın katılımcı listesi gibidir. Aynı isim listeye kaç kez yazılırsa yazılsın, sistem o kişiyi sadece bir "benzersiz varlık" olarak tanır.
- Tuple (Demet): Bir mezuniyet diploması veya bir tapu kaydı gibidir. Bilgiler bir kez yazılır ve üzerine mühür basılır; üzerinde karalama yapılamaz, içeriği değiştirilemez.

## 3. Karşılaştırmalı Analiz: List vs Set vs Tuple

Listeler verileri giriş sırasına göre tutan en esnek yapımız. Eğer verinin sırası önemliyse ve değerlerin değişmesine izin vereceksek listeleri kullanırız. Setler ise tam bir temizlik aracı; içine ne atarsak atalım tekrar edenleri sildiği için analiz aşamasında mükerrer kayıtları ayıklamakta çok hızlılar. Tuple'lar ise işin güven tarafında. Bir kez oluşturulduktan sonra değiştirilemedikleri için kritik verileri mühürlemek ve yanlışlıkla bozulmalarını önlemek istediğimizde devreye giriyorlar.

## 4. Bool ve If Kontrollerinin Sistem Mantığındaki Rolü

Bir sistemin "akıllı" hareket etmesini sağlayan unsur, verideki durumları analiz edip karar verebilmesidir:

- Boolean Mantığı (True/False): Sistemde bir siparişin "Ödendi" veya "Ödenmedi" gibi kesin hallerini ifade eder. Bu, yazılım için bir "evet/hayır" anahtarıdır.
- Karar Mekanizması (If-Else): Bu kontroller, sistemin yol ayrımıdır. Eğer bir siparişin ödeme durumu False ise, sistem o veriyi kargo listesine dahil etmez. Bu mantıksal süzgeçler, hatalı işlemlerin (örneğin ödenmemiş bir ürünün gönderilmesi) önüne geçen en temel güvenlik duvarıdır.

## 5. Bu Projede Hangi Veri Yapısı Neden Seçildi?

Sistem tasarımı aşamasında her yapı belirli bir probleme çözüm üretmek için seçilmiştir:

1. Neden List? Siparişlerin geliş sırasını takip etmek ve bir siparişteki tüm kalemleri (aynı üründen birden fazla olsa dahi) eksiksiz saklamak için en uygun yapıdır.
2. Neden Set? Analiz aşamasında "Sistemde toplam kaç farklı kişi alışveriş yaptı?" sorusuna yanıt ararken, mükerrer isimleri (gürültü veriyi) temizleyip saf bilgiye ulaşmak için kullanılmıştır.
3. Neden Tuple? Raporlama aşamasında müşteri ismi ile toplam tutarı birbirine "mühürlemek" için tercih edilmiştir. Bu sayede finansal özetin programın başka bir yerinde yanlışlıkla değiştirilmesi engellenmiş, veri bütünlüğü sağlanmıştır.

## 6. Sonuç ve Değerlendirme

Bu çalışma, sadece Python kodlarını çalıştırmak değil, hangi veriyi nerede saklarsam daha düzenli ve güvenli bir sistem kurabileceğimi deneyimlediğim bir süreç oldu. Listelerle veriyi toplama, setlerle sadeleştirme ve tuple'lar ile sonuçları sabitleme mantığı, ilerideki mühendislik projelerim için temel bir yaklaşım oluşturacaktır.

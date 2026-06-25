Trading Günlüğü Kullanım Kılavuzu
Bu proje, tek dosyalık bir Trading Günlüğü / İşlem Performans Analizi uygulamasıdır. Uygulama; işlemleri kaydetmek, açık pozisyonları izlemek, takip listesini yönetmek, kapalı işlemlerden performans analizi üretmek ve JSON/CSV olarak yedek almak için hazırlanmıştır.
Uygulama tamamen tarayıcıda çalışır. Ek veritabanı, sunucu veya üyelik gerektirmez.
---
1. Uygulamanın Amacı
Bu uygulama ile şunları yapabilirsiniz:
Açık, kapalı ve takip durumundaki işlemleri kaydetmek
Aynı semboldeki açık pozisyonların ağırlıklı ortalama maliyetini görmek
Manuel güncel fiyat girerek açık pozisyonlarda tahmini kâr/zarar hesaplamak
Takip listesindeki hisselerin hedefe, stopa veya iptal seviyesine uzaklığını izlemek
Strateji, sembol, duygu durumu, hata etiketi ve kurala uyum bazında performans analizi yapmak
Risk/ödül, R multiple, profit factor, expectancy ve drawdown gibi metrikleri takip etmek
JSON yedeği alarak verileri saklamak ve daha sonra tekrar içe aktarmak
CSV dışa aktarımı ile Excel’de ayrıca analiz yapmak
---
2. Kurulum ve Çalıştırma
2.1. Bilgisayarda çalıştırma
HTML dosyasını bilgisayarınıza indirin.
Dosyaya çift tıklayın.
Dosya varsayılan tarayıcıda açılır.
İşlem kayıtlarınızı girmeye başlayabilirsiniz.
Uygulama internet bağlantısı olmadan da çalışır. Ancak GitHub Pages üzerinden kullanıyorsanız sayfayı açmak için internet gerekir.
2.2. GitHub Pages ile kullanma
GitHub Pages’te kullanmak için:
HTML dosyasının adını `index.html` yapın.
GitHub’daki ilgili repo içine yükleyin.
Repo ayarlarından GitHub Pages’i aktif edin.
Oluşan bağlantıyı telefon veya bilgisayar tarayıcınızda açın.
Örnek kullanım yapısı:
```text
trading-gunlugu/
└── index.html
```
2.3. Telefon ana ekranına ekleme
Web Browser GitHub Pages bağlantısını açın.
Paylaş simgesine dokunun.
Ana Ekrana Ekle seçeneğini seçin.
Uygulamaya bir ad verin.
Ana ekrandaki simgeden kullanmaya başlayın.
---
3. Veri Saklama Mantığı
Uygulama verileri tarayıcının localStorage alanında saklar.
Bu şu anlama gelir:
Veriler aynı tarayıcıda kalır.
Sayfayı kapatsanız bile kayıtlar silinmez.
Ancak tarayıcı verilerini temizlerseniz kayıtlar silinebilir.
Farklı cihazda veya farklı tarayıcıda aynı kayıtlar otomatik görünmez.
Güvenli kullanım için düzenli olarak JSON yedeği almanız gerekir.
Önemli öneri:
> Haftada en az bir kez \*\*JSON Yedek Al\*\* butonuyla yedek alın.
---
4. Temel Kavramlar
4.1. Açık pozisyon
Gerçekten aldığınız veya sattığınız, henüz kapatmadığınız pozisyonlardır.
Açık pozisyonlar:
Açık pozisyon özetine dahil edilir.
Ağırlıklı ortalama maliyet hesabına dahil edilir.
Güncel fiyat girilirse tahmini gerçekleşmemiş K/Z hesaplanır.
Gerçekleşmiş performansa dahil edilmez.
4.2. Takip pozisyonu
Henüz gerçek işlem yapmadığınız, sadece izlediğiniz fırsatlardır.
Takip kayıtları:
Açık pozisyon ortalama maliyetine dahil edilmez.
Gerçekleşmiş kâr/zarara dahil edilmez.
Hedef, stop ve manuel güncel fiyat üzerinden fırsat analizi yapılabilir.
Daha sonra işlem listesinde durum değiştirerek açık pozisyona çevrilebilir.
4.3. Kapalı pozisyon
Giriş ve çıkışı tamamlanmış işlemlerdir.
Kapalı pozisyonlar:
Gerçekleşmiş performans analizine dahil edilir.
Net K/Z, getiri yüzdesi ve R multiple hesaplanır.
Strateji, sembol, duygu, hata ve kurala uyum analizlerinde kullanılır.
---
5. Yeni İşlem Ekleme
Yeni kayıt eklemek için Yeni İşlem Ekle formunu kullanın.
5.1. Zorunlu temel alanlar
Aşağıdaki alanlar işlem kaydının temelini oluşturur:
Tarih
Sembol
Piyasa
Yön
İşlem Durumu
Giriş Fiyatı
Miktar / Lot
Kapalı işlem için ayrıca Çıkış Fiyatı girilmelidir.
Açık ve takip kayıtlarında çıkış fiyatı zorunlu değildir.
---
6. Form Alanları ve Kullanım Mantığı
6.1. Temel işlem alanları
Alan	Açıklama
Tarih	İşlemin veya takip kaydının tarihi
Sembol	Hisse, kripto veya varlık kodu
Piyasa	BIST, Kripto, Forex, ABD Hisse, Emtia veya Diğer
Yön	Long veya Short
İşlem Durumu	Açık, Takip veya Kapalı
Strateji	İşlem stratejisinin kısa adı
Giriş Fiyatı	Gerçekleşen veya takip edilen giriş fiyatı
Çıkış Fiyatı	Sadece kapalı işlemler için zorunlu
Miktar / Lot	İşlem miktarı
Komisyon	İşlem maliyeti
Stop Loss	Stop seviyesi
Take Profit / Hedef Fiyat	Hedef fiyat seviyesi
Güncel Fiyat	Manuel güncel fiyat
6.2. Strateji ve piyasa bağlamı alanları
Alan	Açıklama
İşlem Tipi	Trend takip, kırılım, pullback, bilanço, haber vb. sınıflandırma
Ana Gerekçe	Teknik, temel, haber, endeks, risk yönetimi vb. ana neden
Kurulum Kalitesi	İşlem kurulumunun 1-5 arasında puanlanması
Zaman Dilimi	Haftalık, günlük, 4 saatlik, saatlik, 15 dakika vb.
Piyasa Koşulu	Yükseliş, düşüş, yatay, belirsiz, endeks güçlü/zayıf
Çıkış Nedeni	Hedef, stop, manuel, panik, haber, kural dışı vb.
Bu alanlar ileride hangi işlem tiplerinde daha başarılı olduğunuzu görmek için önemlidir.
6.3. Risk yönetimi alanları
Alan	Açıklama
Portföy Büyüklüğü	İşlem anındaki toplam portföy büyüklüğü
İşleme Ayrılan Sermaye	Bu işleme ayrılan sermaye tutarı
Planlanan Risk %	İşlem öncesinde portföye göre planlanan risk yüzdesi
Maks. Kabul Edilen Zarar	Bu işlemde kabul edilen azami zarar tutarı
Planlanan Giriş	İşleme girmeyi planladığınız fiyat
Planlanan Stop	İşlem öncesi planlanan stop seviyesi
Planlanan Hedef	İşlem öncesi planlanan hedef fiyat
Bu alanlar, plan ile gerçekleşen işlem arasındaki sapmayı ölçmek için kullanılır.
6.4. Psikoloji ve disiplin alanları
Alan	Açıklama
Duygu Durumu	Sakin, aceleci, FOMO, stresli, kararsız vb.
Güven Puanı	İşlem öncesi güven düzeyi, 1-5
Stres Puanı	İşlem öncesi stres düzeyi, 1-5
Sabır Puanı	İşlem sırasında plana ne kadar sabır gösterildiği, 1-5
İşlem Sonrası Puan	İşlem sonrası kişisel değerlendirme puanı, 1-5
Kurala Uyum	Evet, Kısmen veya Hayır
Bu alanlar davranışsal performans analizi için kullanılır.
6.5. İşlem yönetimi alanları
Alan	Açıklama
Stop Taşındı mı?	Stop seviyesi işlem sırasında değiştirildiyse işaretlenir
Hedef Değiştirildi mi?	Hedef fiyat işlem sırasında değiştirildiyse işaretlenir
Erken Çıkış mı?	Planlanan noktadan önce çıkıldıysa işaretlenir
Geç Giriş mi?	İşleme planlanandan geç girildiyse işaretlenir
Pozisyon Eklendi mi?	İşlem sırasında ek alım/satım yapıldıysa işaretlenir
Kademeli Çıkış Var mı?	Pozisyon parça parça kapatıldıysa işaretlenir
Bu alanlar işlem yönetimi disiplininizi ölçmek için kullanılır.
6.6. Takip listesi alanları
Alan	Açıklama
Takip Nedeni	Destek bölgesi, direnç kırılımı, bilanço beklentisi vb.
Takip Sonucu	Devam ediyor, işleme döndü, vazgeçildi, hedefe gitti, kaçırıldı vb.
İşleme Döndü mü?	Takip kaydı sonradan gerçek işleme çevrildiyse işaretlenir
Hedefe Ulaştı mı?	Takip edilen varlık hedefe geldiyse işaretlenir
İptal Seviyesi Çalıştı mı?	Stop/iptal seviyesi geldiyse işaretlenir
Kaçırılan Fırsat Notu	Fırsat kaçtıysa kısa açıklama
Takip kayıtları, işlem yapmadığınız ama izlediğiniz fırsatların kalitesini ölçmek için kullanılır.
---
7. İşlem Listesini Kullanma
İşlem listesinde kayıtlar şu sırayla gösterilir:
Açık pozisyonlar
Takip kayıtları
Kapalı pozisyonlar
Aynı grup içindeki kayıtlar genellikle en yeni tarih üstte olacak şekilde sıralanır.
Her işlem satırında şu işlemleri yapabilirsiniz:
Kaydı düzenleme
Kaydı silme
Pozisyon durumunu değiştirme
Açık veya takip kayıtları için manuel güncel fiyat girme
Kapalı duruma geçerken sistem kapanış fiyatı ister.
---
8. Manuel Güncel Fiyat Kullanımı
Uygulama otomatik fiyat verisi çekmez. Güncel fiyatı siz elle girersiniz.
Kullanım:
İşlem listesinde veya açık pozisyon özetinde Fiyat Gir butonuna basın.
Güncel fiyatı yazın.
Sistem aynı semboldeki açık ve takip kayıtlarına bu fiyatı uygular.
Açık pozisyonlarda tahmini K/Z hesaplanır.
Takip kayıtlarında hedefe/stopa uzaklık ve potansiyel analiz hesaplanır.
Virgüllü sayı kullanılabilir:
```text
168,40
1250,75
```
---
9. Açık Pozisyon Özeti
Açık pozisyon özeti yalnızca Açık durumundaki kayıtları dikkate alır.
Bu bölümde şunlar hesaplanır:
Sembol
Yön
Pozisyon sayısı
Toplam miktar
Ağırlıklı ortalama maliyet
Toplam pozisyon büyüklüğü
Toplam risk
Potansiyel ödül
Risk/ödül oranı
Güncel fiyat
Tahmini açık K/Z
Ağırlıklı ortalama maliyet formülü:
```text
Toplam (Giriş Fiyatı × Miktar) / Toplam Miktar
```
---
10. Analiz Panelleri
10.1. Analiz Paneli
Bu bölümde şu analizler yer alır:
Psikoloji analizi
Hata analizi
Etiket analizi
Bu analizler kapalı işlemler üzerinden anlamlı sonuç üretir.
10.2. Performans Analizi Paneli
Bu bölümde daha gelişmiş performans metrikleri yer alır:
Genel performans özeti
Toplam net K/Z
Win Rate
Profit Factor
Expectancy
Toplam R
Ortalama R
Ortalama kazanç
Ortalama kayıp
Kazanç/kayıp oranı
Maksimum düşüş / drawdown
Açık pozisyon riski
Açık pozisyon tahmini K/Z
Takip listesi özeti
10.3. Kırılım bazlı performans analizleri
Uygulama şu kırılımlarda performans tablosu üretir:
Strateji bazlı performans
Sembol bazlı performans
Kurala uyum performansı
Duygu durumu performansı
Zaman dilimi performansı
Piyasa koşulu performansı
İşlem tipi performansı
Ana gerekçe performansı
Kurulum kalitesi performansı
Güven puanı performansı
Stres puanı performansı
Sabır puanı performansı
İşlem sonrası puan performansı
Hata maliyeti analizi
10.4. Risk ve plan-uygulama analizi
Bu bölümde işlem öncesi plan ile gerçekleşen işlem karşılaştırılır.
Örnek metrikler:
Planlanan risk tutarı
Planlanan risk/ödül oranı
Gerçekleşen risk/ödül oranı
Pozisyonun portföye oranı
Riskin portföye oranı
Maksimum kabul edilen zarar kullanım oranı
Planlanan girişten sapma
Planlanan stop seviyesinden sapma
Planlanan hedeften sapma
---
11. Temel Performans Metrikleri
11.1. Win Rate
Kazanan kapalı işlem sayısının toplam kapalı işlem sayısına oranıdır.
```text
Win Rate = Kazanan İşlem / Kapalı İşlem
```
11.2. Profit Factor
Toplam kazancın toplam zarara oranıdır.
```text
Profit Factor = Toplam Kazanç / Toplam Zarar
```
Genel yorum:
1’in altı: sistem zayıf olabilir
1 civarı: başabaş bölge
1’in üstü: pozitif sistem işareti
11.3. Expectancy
İşlem başına ortalama beklenen kazanç veya kayıptır.
```text
Expectancy = Toplam Net K/Z / Kapalı İşlem Sayısı
```
11.4. R Multiple
İşlemde elde edilen net sonucun, işlem öncesi alınan riske oranıdır.
```text
R Multiple = Net K/Z / Risk Tutarı
```
Örneğin:
+2R: alınan riskin iki katı kazanç
-1R: planlanan risk kadar zarar
+0,5R: riskin yarısı kadar kazanç
11.5. Drawdown
Kümülatif performansın zirveden ne kadar gerilediğini gösterir.
Bu metrik, yalnızca toplam kâra değil, süreç içindeki düşüşlere de bakmanızı sağlar.
---
12. Filtreleme
Filtreler bölümünde kayıtları şu alanlara göre süzebilirsiniz:
Sembol
Strateji
Etiket
Yön
Durum
Sonuç
Kurala uyum
Filtreleri sıfırlamak için Filtreleri Temizle butonunu kullanın.
---
13. Veri Yönetimi
13.1. JSON yedek alma
JSON Yedek Al butonu tüm işlem kayıtlarınızı `.json` dosyası olarak indirir.
Bu dosya:
Verilerinizi yedeklemek
Başka tarayıcıya taşımak
Daha sonra tekrar içe aktarmak
ChatGPT’ye performans analizi için göndermek
için kullanılabilir.
13.2. JSON içe aktarma
Daha önce indirdiğiniz JSON dosyasını seçin.
JSON İçe Aktar butonuna basın.
Sistem mevcut verilerin üzerine yazmak isteyip istemediğinizi sorar.
Onay verirseniz kayıtlar yüklenir.
Dikkat:
> JSON içe aktarma mevcut kayıtların üzerine yazabilir. Önce mevcut verinizin yedeğini alın.
13.3. CSV dışa aktarma
CSV Dışa Aktar butonu verileri Excel uyumlu `.csv` formatında indirir.
CSV dosyası Excel’de açılarak ayrıca tablo, pivot tablo veya grafik analizi yapılabilir.
---
14. JSON Dosyasını Yapay Zeka ile Analiz Etme
JSON yedeğini indirip yapay zekaya gönderdiğinizde şu analizler yapılabilir:
Genel performans özeti
Strateji bazlı başarı analizi
Sembol bazlı kâr/zarar analizi
Kurala uyumun performansa etkisi
Psikoloji ve duygu durumu analizi
Hata maliyeti analizi
R multiple analizi
Risk yönetimi analizi
Planlanan işlem ile gerçekleşen işlem sapması
Açık pozisyon risk değerlendirmesi
Takip listesinin kalitesi
Kaçırılan fırsat analizi
Davranışsal iyileştirme önerileri
JSON gönderirken şu şekilde talep yazabilirsiniz:
```text
Bu Trading Günlüğü JSON dosyasını analiz et.
Özellikle strateji performansı, hata maliyeti, psikoloji etkisi, risk yönetimi ve takip listesi kalitesi açısından yorumla.
Bana güçlü/zayıf yönlerimi ve sonraki ay için uygulanabilir önerileri çıkar.
```
---
15. İyi Kayıt Tutma Önerileri
Daha kaliteli analiz için her işlemde şu alanları doldurmaya çalışın:
Strateji
İşlem tipi
Ana gerekçe
Zaman dilimi
Piyasa koşulu
Giriş
Stop
Hedef
Miktar
Portföy büyüklüğü
Planlanan risk yüzdesi
Duygu durumu
Kurala uyum
Hata etiketleri
Not
Kapalı işlemlerde ayrıca:
Çıkış fiyatı
Çıkış nedeni
Erken çıkış / geç giriş bilgisi
Stop veya hedef değiştirildiyse ilgili alanlar
İşlem sonrası puan
Takip kayıtlarında ayrıca:
Takip nedeni
Hedef fiyat
Stop / iptal seviyesi
Güncel fiyat
Takip sonucu
Kaçırılan fırsat notu
---
16. Örnek Kullanım Akışları
16.1. Açık pozisyon ekleme
Durum alanını Açık seçin.
Giriş fiyatı, miktar, stop ve hedef girin.
Strateji, duygu, kurala uyum ve not alanlarını doldurun.
Kaydedin.
Daha sonra manuel güncel fiyat girerek tahmini K/Z takip edin.
16.2. Takip kaydı ekleme
Durum alanını Takip seçin.
Sembol, takip fiyatı/giriş fiyatı, hedef ve stop/iptal seviyesi girin.
Takip nedenini seçin.
Güncel fiyat girdikçe hedefe ve stopa uzaklığı izleyin.
İşleme girerseniz kayıt durumunu Açık yapın.
16.3. Kapalı işlem ekleme
Durum alanını Kapalı seçin.
Giriş ve çıkış fiyatını girin.
Miktar, komisyon, stop ve hedef bilgilerini girin.
Çıkış nedeni, hata etiketi, duygu ve kurala uyum alanlarını doldurun.
Kaydedin.
İşlem performans analizine otomatik dahil olur.
---
17. Mobil Kullanım
Uygulama mobil uyumludur.
Mobil ekranda:
Form alanları tek sütuna düşer.
İşlem listesi kart görünümünde gösterilir.
Büyük tablolar kaydırılabilir yapıdadır.
iPhone’da Safari üzerinden ana ekrana eklenerek uygulama gibi kullanılabilir.
---
18. Güvenlik ve Gizlilik
Verileriniz varsayılan olarak tarayıcı içinde saklanır.
Veriler otomatik olarak herhangi bir sunucuya gönderilmez.
JSON veya CSV dosyasını siz indirmedikçe dışarı aktarım yapılmaz.
JSON dosyasını bir yapay zekâ aracına gönderdiğinizde, dosya içindeki kişisel notlarınız da paylaşılmış olur. Göndermeden önce hassas notları kontrol edin.
---
19. Sık Karşılaşılan Sorunlar
Kayıtlarım görünmüyor
Muhtemel nedenler:
Farklı tarayıcı kullanıyorsunuz.
Farklı cihazdasınız.
Tarayıcı verileri temizlenmiş olabilir.
Gizli sekmede kullanmış olabilirsiniz.
Çözüm:
Daha önce aldığınız JSON yedeğini içe aktarın.
Sayfayı güncelledim ama eski sürüm açılıyor
Tarayıcı önbelleği eski dosyayı göstermiş olabilir.
Çözüm:
Sayfayı yenileyin.
Gerekirse tarayıcı önbelleğini temizleyin.
GitHub Pages kullanıyorsanız birkaç dakika bekleyin.
JSON içe aktarırken veri değişti
JSON içe aktarma mevcut verilerin üzerine yazabilir.
Çözüm:
İçe aktarmadan önce mevcut verilerinizin JSON yedeğini alın.
Türkçe virgüllü sayılar çalışır mı?
Evet. Uygulama `168,40` gibi virgüllü girişleri okuyacak şekilde hazırlanmıştır.
---
20. Önerilen Rutin
Günlük kullanım için önerilen rutin:
İşleme girmeden önce planı girin.
Giriş, stop, hedef ve risk bilgisini yazın.
İşlem sırasında değişiklik olursa ilgili alanları güncelleyin.
İşlem kapanınca çıkış nedeni ve hata/psikoloji alanlarını doldurun.
Haftada bir performans panelini inceleyin.
Haftada bir JSON yedeği alın.
Ay sonunda JSON dosyasını analiz ettirin.
---
21. Uyarı
Bu uygulama yatırım tavsiyesi vermez. Sadece kendi işlem kayıtlarınızı düzenli tutmak ve performansınızı analiz etmek için hazırlanmış kişisel bir araçtır.
Finansal kararlarınızdan kendiniz sorumlusunuz.

# Trading Günlüğü

Tek dosyalık, tarayıcıda çalışan bir **işlem günlüğü ve performans analizi** uygulamasıdır. Açık, takip ve kapalı pozisyonları kaydetmek; risk, psikoloji, hata ve strateji performansını analiz etmek için kullanılır.

Veriler tarayıcının `localStorage` alanında saklanır. Uygulama otomatik olarak herhangi bir sunucuya veri göndermez.

---

## Temel Kullanım

Uygulamada üç tür kayıt vardır:

| Durum | Anlamı |
|---|---|
| Açık | Gerçek işlem yapılmış, henüz kapanmamış pozisyon |
| Takip | Henüz işlem yapılmamış, izlenen fırsat |
| Kapalı | Giriş ve çıkışı tamamlanmış işlem |

İşlem listesi şu sırayla gösterilir:

1. Açık pozisyonlar
2. Takip kayıtları
3. Kapalı pozisyonlar

---

## Veri Girişi

Yeni kayıt eklerken temel olarak şu alanları doldurun:

- Tarih
- Sembol
- Piyasa
- Yön: Long / Short
- Durum: Açık / Takip / Kapalı
- Giriş fiyatı
- Miktar
- Stop Loss
- Take Profit / Hedef fiyat
- Strateji
- Duygu durumu
- Kurala uyum
- Hata etiketleri
- Genel etiketler
- Not

Kapalı işlemde **çıkış fiyatı** girilmelidir. Açık ve takip kayıtlarında çıkış fiyatı zorunlu değildir.

---

## Manuel Güncel Fiyat

Uygulama otomatik piyasa verisi çekmez. Açık veya takip kayıtları için güncel fiyatı elle girebilirsiniz.

Güncel fiyat girildiğinde uygulama şunları hesaplar:

- Açık pozisyon tahmini K/Z
- Hedefe uzaklık
- Stopa uzaklık
- Takip kayıtlarında potansiyel getiri

Virgüllü sayı girebilirsiniz:

```text
168,40
```

---

## Performans Analizi

Uygulama kapalı işlemler üzerinden performans analizi üretir.

Başlıca metrikler:

| Metrik | Açıklama |
|---|---|
| Net K/Z | Gerçekleşmiş toplam kâr/zarar |
| Win Rate | Kazanan işlem oranı |
| Profit Factor | Toplam kazanç / toplam zarar |
| Expectancy | İşlem başına beklenen ortalama sonuç |
| Ortalama R | Risk birimine göre ortalama sonuç |
| Drawdown | Kümülatif performanstaki en büyük düşüş |

Analiz kırılımları:

- Strateji performansı
- Sembol performansı
- Kurala uyum analizi
- Duygu durumu analizi
- Hata maliyeti analizi
- Zaman dilimi performansı
- Piyasa koşulu performansı
- Çıkış nedeni analizi
- Takip listesi analizi

---

## Önemli Form Alanları

Daha iyi analiz için şu alanları mümkün olduğunca doldurun:

| Alan | Ne işe yarar? |
|---|---|
| Zaman Dilimi | Hangi periyotta daha başarılı olduğunuzu gösterir |
| Piyasa Koşulu | Yükseliş/düşüş/yatay piyasada performansı ayırır |
| Çıkış Nedeni | Hedef, stop, manuel veya kural dışı çıkışları analiz eder |
| Portföy Büyüklüğü | Riskin portföye oranını hesaplar |
| Güven / Stres / Sabır Puanı | Psikoloji etkisini ölçer |
| İşlem Tipi | Kırılım, pullback, trend takip gibi ayrımlar yapar |
| Ana Gerekçe | Teknik, temel, haber, endeks gibi nedenleri sınıflandırır |
| Takip Nedeni / Sonucu | İzlenen fırsatların kalitesini analiz eder |

---

## Veri Yönetimi

| İşlem | Açıklama |
|---|---|
| JSON Yedek Al | Tüm kayıtları yedekler |
| JSON İçe Aktar | Daha önce alınan yedeği geri yükler |
| CSV Dışa Aktar | Verileri Excel’de incelemek için dışa aktarır |

Düzenli olarak JSON yedeği almak önerilir.

---

## JSON Dosyasıyla Analiz

Uygulamadan aldığınız JSON dosyasını ChatGPT’ye yükleyerek performans analizi isteyebilirsiniz.

Örnek istek:

```text
Bu trading günlüğü JSON dosyamı analiz et. Strateji, sembol, hata, psikoloji ve risk yönetimi açısından güçlü/zayıf yönlerimi çıkar. Bana uygulanabilir iyileştirme önerileri ver.
```

---

## Mobil Kullanım

Uygulama mobil uyumludur. Telefonda işlem listesi kart görünümünde gösterilir. Açık, takip ve kapalı kayıtlar mobil ekranda daha rahat okunacak şekilde düzenlenir.

---

## Gizlilik ve Güvenlik

- Veriler tarayıcınızda saklanır.
- Veriler otomatik olarak herhangi bir sunucuya gönderilmez.
- Tarayıcı verilerini silerseniz kayıtlarınız da silinebilir.
- Cihaz değiştirirken JSON yedeği alıp yeni cihazda içe aktarın.

---

## Önerilen Kullanım Rutini

Her işlemden sonra:

- İşlem nedenini yazın.
- Stop ve hedefi girin.
- Duygu durumunu işaretleyin.
- Hata varsa etiketleyin.
- Kapandıktan sonra çıkış nedenini ve sonucu kaydedin.

Haftalık olarak:

- JSON yedeği alın.
- Performans panelini inceleyin.
- En çok zarar yazdıran hata ve stratejileri kontrol edin.
- Sonraki hafta için bir davranış hedefi belirleyin.

---

## Not

Bu uygulama yatırım tavsiyesi vermez. Kayıt, analiz ve kişisel performans takibi amacıyla hazırlanmıştır.

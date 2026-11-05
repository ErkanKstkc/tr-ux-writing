# Test vakaları

Skill'i değiştirdikten sonra bu vakaları skill'le çalıştır ve beklenen davranışı kontrol et. Ürünler kurgusaldır.

## 1. Stokla ana sayfası (siz dili)

Bilinenler: barkodla ürün girişi, stok 5'in altına düşünce e-posta, Trendyol ve Hepsiburada ile stok eşitleme, 14 gün ücretsiz deneme, kart istenmez.

Girdi:
- Başlık: Stok Yönetiminin Geleceğini Bugün Keşfedin
- Alt başlık: Yenilikçi, hızlı ve güvenilir çözümlerimizle işletmenizi bir üst seviyeye taşıyın.
- Buton: Hemen Keşfet
- Kart: Akıllı Takip / Stoklarınızın takip edilmesi sağlanarak süreçleriniz optimize edilir.
- Kart: Uyarılar / Bu bağlamda, kritik seviyelerde bildirim alırsınız. Bununla birlikte, ayarlar kişiselleştirilebilir.
- Yorum: "Stokla sayesinde işlerimiz çok kolaylaştı, harika bir deneyim!" — Ayşe K.
- SSS: Deneme için kredi kartı gerekiyor mu? / Harika bir soru! Müşteri memnuniyetini ön planda tutuyoruz.
- Hata: Bir hata oluştu. Lütfen daha sonra tekrar deneyiniz.
- Fiyat notu: Stokla ile stok kayıplarınızı %40 azaltın. Learn more

Beklenen:
- Başlık, alt başlık ve kartlar bilinen özelliklerle yazılır. Yeni özellik eklenmez.
- Buton için varsayımla öneri verilir ("14 gün ücretsiz deneyin"), yalnızca `[hedef?]` yazılmaz.
- Kart başlıkları ("Akıllı Takip") tabloda yer alır.
- "kişiselleştirilebilir" olanak olarak kalır ("değiştirebilirsiniz"), silinmez.
- 5 eşiğinin sabit mi değiştirilebilir mi olduğu sorulur. Soru listesinde ya da çelişki listesinde olabilir.
- Yorum değişmez, yalnızca not düşülür.
- SSS cevabı "Hayır" ile başlar.
- Hata mesajı kullanılabilir genel bir metindir, "Lütfen" içermez, işlem listede sorulur.
- %40: `Değişmedi, vaat`, kanıt istenir. Vaat silinip yerine yeni vaat yazılmaz.
- "Learn more" için Türkçe karşılık önerilir.

## 2. Fon sayfası

Girdi:
- Başlık: ÖRNEK PORTFÖY BİRİNCİ SERBEST FON
- Metin: Birikimleriniz güvenle büyüsün, geleceğinizi bugünden garanti altına alın.
- Uyarı: Geçmiş getiri gelecek getirinin göstergesi değildir.

Beklenen:
- Resmî ad ve yasal uyarı değişmez.
- Metin `Değişmedi, vaat` olarak işaretlenir. Vaatsiz alternatif not olarak verilir, uyum kontrolü istenir.

## 3. Tek buton (sen dili)

Girdi: Bağlam "fiyat planlarının listelendiği sayfa". Buton: Hemen Keşfet

Beklenen:
- Kısa iş modu: bağlam bloğu ve boş listeler yok.
- "Planları gör" gibi fiilli, hedefi söyleyen bir öneri.

## 4. Bağlamsız hata mesajı

Girdi: Bir hata oluştu. Lütfen daha sonra tekrar deneyiniz.

Beklenen:
- Kısa iş modu.
- Neden uydurulmaz. Kullanılabilir genel metin ve "hangi işlem?" sorusu.
- Hitap kaynaktaki "deneyiniz"den "siz" olarak varsayılır ve işaretlenir.

## 5. Sıfırdan landing page (yazma modu, siz dili)

Girdi: "Stokla için tek sayfalık bir React landing page yaz." Bilinenler vaka 1'deki gibi. Fiyat, müşteri ve yorum bilgisi yok.

Beklenen:
- Metin doğrudan JSX'te. Tablo ya da bağlam bloğu yok.
- Görünür metinde `[...?]` yok. Eksik bilgi `TODO` yorumunda.
- Uydurma sayı, müşteri, logo veya yorum yok. Yorum, logo ve fiyat bölümü eklenmez; yerlerinde yalnızca TODO yorumu olabilir.
- Butonlar fiilli ve hedefli, hitap her yerde "siz".
- `alt`, `aria-label` ve `placeholder` metinleri de Türkçe ve doğal.
- Sonda TODO, varsayım ve vaat listesi var.

## 6. Defterim landing page (yazma modu, anlatım gücü)

Girdi: "Defterim için tek sayfalık bir landing page yaz." Brief: serbest çalışanlar için fatura ve gider takibi. Bilinenler: GİB entegrasyonlu e-fatura ve e-arşiv, fiş fotoğrafından tutar/tarih/KDV okuma (okunamayan alan elle düzeltilir), ay sonu KDV özeti (PDF/Excel, müşavirle paylaşılabilir), isteğe bağlı ödeme hatırlatma e-postası (kullanıcı açarsa), web/iOS/Android, 30 gün ücretsiz deneme, kart istenmez. Bilinmeyenler: fiyat, kullanıcı sayısı, yorum, şirket bilgisi, şifre kuralı, ödeme durumu takibi.

Beklenen:
- Brief'te olmayan özellik veya davranış yok (ödeme durumu takibi, "kurulum yok", şifre kuralı, "bütün özellikler açık" gibi).
- Olanaklar kesinleşmez: hatırlatma "gidebilir", özet "paylaşabilirsiniz".
- En az bir sahne yalnızca bilinen eylemlerle kurulur.
- SSS'de bilinen özelliklerden doğan en az bir gerçek itiraz var (müşavir sorusu gibi).
- Aynı bilgi sayfada en çok 2 kez geçer.
- Art arda üç cümle aynı ekle bitmez.
- Yasal cümle varsa aydınlatma metni için "kabul" yazılmaz.
- Kayıt formunda dört durum metni de var: alan hatası, gönderiliyor, başarılı, sunucu hatası. Şifre kuralı ipucunda ya da hatada geçmiyor.

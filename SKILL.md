---
name: tr-ux-writing
description: Web sitesi, ürün arayüzü ve dokümantasyon için yazılan Türkçe metinlerdeki AI ve çeviri izlerini temizler; metni somut, doğal ve tutarlı hâle getirir. Hero, alt başlık, buton, özellik kartı, SSS, form, hata mesajı ve boş ekran metni yazarken ya da düzeltirken kullan. "AI yazmış gibi", "çeviri gibi", "yapay duruyor", "metni doğallaştır", "site metni", "microcopy", "UX yazımı", "buton metni" dendiğinde ve bir arayüze Türkçe metin eklerken devreye gir. Site, sayfa veya bileşen kodu (React, HTML, JSX) yazarken içindeki görünür metinler için de kullan. Akademik metin, hukuki metin veya imla denetimi için kullanma. Türkçe metinde emil-unslop-writing gibi İngilizce yazım skill'leri yerine bunu kullan.
---

# Türkçe site metinlerini doğallaştırma

Amaç metni süslemek değil, okura ne olduğunu ve ne yapacağını söylemektir. Önce modu seç, sonra adımları sırayla uygula:

```
Metni site veya bileşen kodunun içine mi yazıyorsun?
├── Evet → Yazma modu: adımlar aynı, metin doğrudan koda gider, tablo ve bağlam bloğu yok
└── Hayır → Düzeltilecek kaç öğe var?
    ├── 1-3 (tek buton, tek hata mesajı) → Kısa iş: bağlam bloğu yok, tablo ve varsa sorular
    └── Daha fazla → Tam düzeltme: bağlam bloğu, tablo, listeler
```

İşe başlamadan projenin yazım kurallarını oku (`CLAUDE.md`, `AGENTS.md`, stil rehberi): hitap, terimler, belirsiz bilginin işaretlenme biçimi. Bu skill ile çelişirse proje kazanır, çünkü ekibin kararı genel kuraldan önce gelir. `[...?]` yerine projenin işaretleme biçimini kullan.

## 1. Dokunulmayacakları ayır

Bunları olduğu gibi koru çünkü değişmeleri yanlış bilgi veya hukuki risk doğurur:

- Müşteri yorumları ve alıntılar: bunlar gerçek kişilerin sözüdür. Sorun görürsen yalnızca not düş.
- Marka, ürün ve resmî fon adları, kodlar, fiyatlar, oranlar, tarihler. Büyük harfle yazılmış resmî ad da değişmez. Resmî ada ek getirmemek için cümleyi adı eksiz kullanacak şekilde kur.
- Hukuki metinler, yasal uyarılar, risk bildirimleri, KVKK ve çerez metinleri. Form altına yasal cümle yazıyorsan kullanım koşulları "kabul edilir", KVKK aydınlatma metni "okunabilir"; aydınlatma metnine "kabul" yazma, çünkü aydınlatma onay değil bilgilendirmedir. Son hâli için hukuk onayı iste.
- Panelde birebir geçen arayüz etiketleri ("Cache Yenile" gibi), çünkü rehber ile ürün farklı konuşursa okur butonu bulamaz. Etiketin kendisi kötüyse not düş.
- Rehberlerde kod, komut, dosya yolu ve adım sırası.
- Sektörde yerleşmiş terimler ("dijital ikiz", "SEO"). Hedef okur tanımıyorsa terimi silme, yanına en çok 5 kelimelik açıklama ekle.

## 2. Bağlamı belirle

Bu üç soruyu her modda kendine sor, tam düzeltmede çıktının başına da yaz (aynı okura yazılmış rehber sayfalarında bölüm başına bir kez yeter): nerede duruyor, kim okuyor, okur sonra ne yapmalı. Ürünün ne yaptığını veya okurun kim olduğunu bilmiyorsan tahmin etme, sor. Hitabı mevcut siteden al ve her yerde aynı tut. Yeni sitede ve belirsiz durumda sor. Tonu koru: kurumsal bir site daha net olur, gündelik konuşmaya dönmez.

## 3. Her cümleyi sına

```
Cümle kimin ne yaptığını düz söylüyor ve klişe içermiyor mu?
├── Evet → kalsın, 4. adıma geç (rakip de kullanabilse bile: yaygın özelliği düz söylemek kusur değildir)
└── Hayır → Aynı sektördeki bir rakip, marka adını değiştirince cümleyi aynen kullanabilir mi?
    ├── Hayır → kalsın, 4. adıma geç
    └── Evet → Cümlede kimin ne yaptığı veya okurun ne kazandığı var mı?
        ├── Var → genel kısmı at, somut kısmı tut
        ├── Yok ama bilgi metnin başka yerinde var → o bilgiyle yeniden yaz
        └── Yok ve hiçbir yerde yok → [süre?], [kanıt?] gibi işaretle ve sor
```

**Asla uydurma:** sayı, süre, müşteri, özellik, ödül veya garanti ekleme çünkü daha doğal görünen yanlış bilgi, klişeden daha zararlıdır. Metni düzenlerken yeni bir iddia da ekleme.

**Bilinenle sahne kur:** Düz metin ikna etmez, uydurma metin yanıltır. Arası, bilinen özelliklerden okurun gününden bir an kurmaktır ("Faturayı bilgisayardan kesin, fişi yolda telefondan ekleyin"). Sahnedeki her eylemi bilinenler listesinde ara; bulamadığın eylem uydurmadır, çıkar. Bilinen bir özellikten türettiğin yeni özellik de uydurmadır (hatırlatma var diye "Ödendi/Ödenmedi" sekmesi eklemek gibi). Zaman vaadi de öyledir ("bugün", "hemen", "dakikalar içinde"). Örnekler: `references/ornekler.md`.

**Varsayım:** Buton hedefi, sonraki adım veya hitap metinde yazılı bir bilgiden çıkıyorsa (sayfada "14 gün ücretsiz deneme" yazıyorsa ya da kaynak "deneyiniz" diyorsa) öner ve `(varsayım: ...)` diye işaretle, çünkü kullanılamayan çıktı da işe yaramaz. Metinde dayanağı yoksa `[...?]` yaz. Ürün, okur, özellik ve ürün kuralı (şifre uzunluğu, limit, süre) varsayılmaz; bunlar için TODO bırak, çünkü ekranda yazan kural kullanıcıya söz verir.

**Anlamı koru:** Bir cümleyi silmeden önce taşıdığı bilgiyi yaz. Bilgi varsa düzelt, silme. Bilgi yoksa sil ve nedenini söyle. Olanak bildiren ifadeyi kesinleştirme ("yerleştirilebilir" → "yerleştirebilirsiniz", "yerleştirirsiniz" değil), çünkü ürünün davranışını değiştirmiş olursun.

"Çözüm", "profesyonel", "stratejik", "sürdürülebilir", "yenilikçi", "uçtan uca" gibi kelimeleri listeden otomatik silme. Türkçe kurumsal dilde insanlar da kullanır. Yukarıdaki sınavdan geçmeyen cümlede sorun sayılırlar. Türkçe AI kalıpları için `references/ai-izleri.md`'ye bak; oradakiler de silme listesi değil, bu sınava sokulacak sinyallerdir.

**Çelişkide seçim yapma:** İki kaynak çelişiyorsa birini doğru kabul etme, çünkü yanlış olan diğeri de olabilir. Metni değiştirme, iki kaynağı dosya ve satırıyla "Doğrulanacak çelişkiler" listesine yaz.

**Biçimi koru:** Tablo hücresi ve madde kısa kalır. Yeni metin kaynaktan %30'dan fazla uzuyorsa yalnızca eksik bilgi tamamlandığında kabul et ve nedenini yaz, çünkü tasarımdaki yer kaynak metne göre ayrılmıştır. Başka sayfadan bilgiyi yalnızca anlamı netleştirmek için gerekiyorsa ekle ve kaynağını belirt.

## 4. Çeviri izini kaldır

`references/dil.md` dosyasının "Çeviri izini kaldır" bölümünü oku ve uygula. Okumadan bu adımı geçme, çünkü çeviri kalıpları ve özne kuralları orada.

## 5. Bileşene göre yaz

`references/bilesenler.md` dosyasını oku ve her bileşeni oradaki satırına göre yaz. Vaat kontrolü de orada; sonuç vaadi her sektörde geçerli, atlama.

## 6. Akışı düzelt

`references/dil.md` dosyasının "Akışı düzelt" bölümünü oku ve uygula: bağlaç, virgül, cümle uzunluğu, ek tekdüzeliği.

## 7. Son kontrol

- Anlam, sayı ve özel adlar kaynakla aynı mı?
- Cümle sildikten veya böldükten sonra sonucu baştan oku: "bu", "bu durum" gibi gönderimler hâlâ neyi gösterdiğini belli ediyor mu, art arda dört kısa cümle kesik kesik okunuyor mu?
- Yeni bir iddia eklendi mi? Eklendiyse kaldır.
- Başlık değiştiyse o başlığa giden bağlantılar çalışıyor mu?
- Hitap ve terimler bütün sayfada aynı mı? `Yeni` sütunundaki her fiili tek tek sayfanın hitabıyla karşılaştır.
- Metin tasarımdaki yere sığıyor mu? Buton en çok 4 kelimedir, çünkü daha uzunu mobilde iki satıra kırılır.
- Vaat işaretlediysen uyum veya hukuk kontrolü notunu yazdın mı?
- Aynı bilgi ("Kart bilgisi istemiyoruz" gibi) sayfada en çok 2 kez geçiyor mu? Fazlası dolgu gibi okunur.

## Yazma modu (site veya bileşen kodu yazarken)

- Görünür metne `[...?]` koyma çünkü canlı sitede görünür. Bilinenle nötr bir metin kur ve yanına kod yorumu olarak `TODO` bırak (JSX'te `{/* TODO: deneme süresi? */}`, HTML'de `<!-- TODO: ... -->`). Bilinenle hiç metin kurulamıyorsa o bölümü ekleme, çünkü içi boş bölüm de canlıda görünür. Yerine TODO bırak ve listede sor.
- Sayfayı doldurmak için örnek müşteri yorumu, logo veya istatistik ekleme.
- Bitirmeden önce koddaki görünür metinleri (buton, `placeholder`, `aria-label`, `alt`, hata, boş ekran) 6. ve 7. adımla kontrol et; aynı ekle biten cümle zincirleri en çok yazarken oluşur.
- Sonda kısa bir liste ver: TODO'lar, varsayımlar, vaat notları.

## Çıktı

Mevcut metin verildiğinde tablo kullan: `Önceki | Yeni | Neden`. Metnin altına ayrı listeler ekle: kullanıcıdan istenen bilgiler (`[...?]`), doğrulanacak çelişkiler, dokunulmayan yerlerdeki notlar, tutarlılık sorunları, metin dışı öneriler. Boş kalan listeyi yazma. Sayfa, kart ve bölüm başlıkları metindir, tabloya girer. Bölüm düzeni, madde birleştirme ve bağlantı ekleme ise "Metin dışı öneriler"e yazılır. Değişmesi gerekmeyen metni değiştirme ve bunu söyle.

Okura görünen örnek metinler de kapsamdadır: arayüz sahneleri, bildirimler, ekran örnekleri. Kod örnekleri kapsam dışıdır.

Kapsamı dürüst yaz: satır satır okunan ve yalnızca kalıp taramasından geçen sayfaları ayrı listele. Okumadığın metin için "temiz" deme, çünkü tarama anlam sorunlarını yakalayamaz.

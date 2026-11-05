# tr-ux-writing

Türkçe site, arayüz ve dokümantasyon metinlerindeki AI ve çeviri izlerini temizleyen bir Claude Code skill'i. Metni somut, doğal ve tutarlı yapar; ürün hakkında bilgi uydurmaz.

İngilizce yazım skill'leri Türkçe metinde iyi çalışmadığı için yazıldı. Akademik metin, hukuki metin ve imla denetimi için değildir.

## Kurulum

```bash
git clone https://github.com/ErkanKstkc/tr-ux-writing.git ~/.claude/skills/tr-ux-writing
```

Claude Code skill'i metin yazarken ya da düzeltirken kendiliğinden yükler. Elle çağırmak için: `/tr-ux-writing`.

## Modlar

- **Yazma modu:** Site veya bileşen kodu yazılırken metin doğrudan koda gider. Eksik bilgi ekrana değil, `TODO` yorumuna yazılır.
- **Kısa iş:** 1-3 öğelik düzeltme (tek buton, tek hata mesajı). Yalnızca tablo ve varsa sorular.
- **Tam düzeltme:** Bağlam, `Önceki | Yeni | Neden` tablosu ve sorular, çelişkiler, notlar listeleri.

## Dosyalar

- `SKILL.md`: süreç, korunacak metinler, uydurma ve varsayım kuralları, son kontrol
- `references/bilesenler.md`: başlık, buton, form, SSS gibi bileşenlerin kuralları ve vaat kontrolü
- `references/dil.md`: çeviri izi, bağlaç, virgül, cümle uzunluğu
- `references/ai-izleri.md`: Türkçe AI kalıpları (silme listesi değil, sinyal)
- `references/ornekler.md`: önce/sonra örnekleri
- `evals/vakalar.md`: skill'i değiştirdikten sonra çalıştırılacak test vakaları

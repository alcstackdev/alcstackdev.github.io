# alcstackdev.github.io

Tüm AlcStack Dev app'leri için tek, kalıcı legal sayfa barınağı. GitHub Pages otomatik
`https://alcstackdev.github.io` adresinde yayınlar (repo adı özel, ekstra Pages ayarı gerekmez).

## Yapı

```
<app-slug>/
  en/privacy-policy.html
  en/terms.html
  tr/privacy-policy.html
  tr/terms.html
```

## Referans örnek

`_example-filled/` klasörü, `_template-app/`'ın tüm değişkenleri gerçek değerlerle doldurulmuş
tam bir örneğidir (kurgusal "Daily Verse Bible" app'i ile). Otomasyon yazarken veya elle yeni
bir app eklerken şüpheye düşülen her durumda buraya bakılabilir — placeholder'ların ne şekilde
doldurulacağının somut kanıtı budur, `_template-app/` sadece boş iskelet.

## Yeni bir app eklerken

1. `_template-app/` klasörünü kopyala, adını gerçek app slug'ı ile değiştir
   (örn. `bible-daily-verse/`). Doldurma şekli için `_example-filled/`'a bak.
2. Her HTML dosyasındaki `{{DEĞİŞKEN}}` alanlarını doldur:
   - `{{APP_NAME}}` — Play/App Store'daki gerçek app adı
   - `{{DEVELOPER_NAME}}` — AlcStack Dev (sabit)
   - `{{DEVELOPER_EMAIL}}` — destek e-postası
   - `{{LAST_UPDATED}}` — yayın tarihi (YYYY-MM-DD)
   - `{{DATA_COLLECTION_LIST}}` — app'in gerçekten kullandığı SDK'lara göre veri toplama
     listesi (örn. "We collect: device identifiers (Firebase Analytics), purchase history
     (RevenueCat)...")
   - `{{THIRD_PARTY_SERVICES_LIST}}` — `<li>` listesi: Firebase, RevenueCat, Shorebird vb.
     hangileri kullanılıyorsa
   - `{{SUBSCRIPTION_TERMS}}` (sadece terms.html) — abonelik varsa otomatik yenileme/iptal
     koşulları, yoksa bu bölüm silinir
   - `{{GOVERNING_JURISDICTION}}` (sadece terms.html) — örn. "Türkiye" veya "the State of
     Delaware, USA"
3. Commit + push (veya `github_create_or_update_file` MCP aracıyla otomatik).
4. Play Console / App Store Connect'e girilecek URL:
   - `https://alcstackdev.github.io/<app-slug>/tr/privacy-policy.html`
   - `https://alcstackdev.github.io/<app-slug>/en/terms.html`

## Not

Bu, `boilerplate_millioner` ana reposundan **ayrı bir git reposu**
(`alcstackdev/alcstackdev.github.io`) — `tooling/alcstackdev.github.io/` altında sadece
kolaylık olsun diye klonlu duruyor, ana repo'nun `.gitignore`'unda hariç tutuluyor. Değişiklikler
bu klasörde kendi `git add/commit/push`'u ile bu repoya gönderilir.

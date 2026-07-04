# 02B_Reject

Bu workflow, red linki üzerinden gelen token değerini kontrol eder ve talebi reddedilmiş olarak işaretler.

## Endpoint

```text
GET /webhook/reject?token=APPROVAL_TOKEN
```

## Akış

1. Webhook, query string içinden `token` değerini alır.
2. `Requests` sayfasında `approvalToken` ile kayıt aranır.
3. Token geçerli, süresi dolmamış ve daha önce kullanılmamışsa akış devam eder.
4. Kayıt `REJECTED` durumuna alınır.
5. `documentStatus` alanı `NOT_CREATED` olarak güncellenir.
6. Kullanıcıya kısa red mesajı döner.

## Kurulumda değiştirilecek alanlar

- Google Sheets credential'ları yeniden seçilmeli.
- Gemini node kullanılıyorsa credential yeniden seçilmeli.
- `REPLACE_WITH_STUDENT_REQUESTS_GOOGLE_SHEET_ID` kendi Sheet ID'nizle değiştirilmeli.
- `Requests` sayfa adı kendi dosyanızdaki adla eşleşmeli.

## Not

Temizlenmiş sürümde küçük bir düzeltme yapıldı: red akışındaki `isTokenUsed` alan adı ve zaman alanları GitHub sürümü için tutarlı hale getirildi.

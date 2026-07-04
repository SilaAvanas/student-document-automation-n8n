# 02A_Approve

Bu workflow, onay linki üzerinden gelen token değerini kontrol eder, talebi onaylar ve belge oluşturur.

## Endpoint

```text
GET /webhook/approve?token=APPROVAL_TOKEN
```

## Akış

1. Webhook, query string içinden `token` değerini alır.
2. `Requests` sayfasında `approvalToken` ile kayıt aranır.
3. Token geçerli, süresi dolmamış ve daha önce kullanılmamışsa akış devam eder.
4. Talep geçici olarak işleniyor durumuna alınır.
5. `Students` sayfasında `studentNo` ile öğrenci bilgisi aranır.
6. Öğrenci bulunursa Google Docs belgesi oluşturulur.
7. Belge paylaşılır ve belge URL'i log tablosuna yazılır.
8. Talep `APPROVED` ve belge `COMPLETED` durumuna alınır.
9. Kullanıcıya kısa onay mesajı döner.

## Kurulumda değiştirilecek alanlar

- Google Sheets credential'ları yeniden seçilmeli.
- Google Docs credential'ı yeniden seçilmeli.
- Google Drive credential'ı yeniden seçilmeli.
- Gemini node kullanılıyorsa credential yeniden seçilmeli.
- `REPLACE_WITH_STUDENT_REQUESTS_GOOGLE_SHEET_ID` kendi Sheet ID'nizle değiştirilmeli.
- `Requests` ve `Students` sayfa adları kendi dosyanızdaki adlarla eşleşmeli.

## Güvenlik notu

Workflow içinde Google Drive paylaşımı `anyone reader` mantığıyla çalışacak şekilde ayarlanmıştır. Gerçek kurum ortamında belge erişimini domain/kullanıcı bazlı sınırlamanız önerilir.

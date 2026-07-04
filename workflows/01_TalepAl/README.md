# 01_TalepAl

Bu workflow, öğrenciden gelen belge/talep başvurusunu alır ve log tablosuna kaydeder.

## Endpoint

```text
POST /webhook/talep
```

## Beklenen body

```json
{
  "studentNo": "202400001",
  "email": "student@example.com",
  "requestType": "Öğrenci Belgesi"
}
```

## Akış

1. Webhook, POST isteğini alır.
2. `studentNo`, `email` ve `requestType` alanları normalize edilir.
3. Code node içinde:
   - `requestId` üretilir.
   - `approvalToken` üretilir.
   - Token için 24 saat geçerlilik süresi atanır.
   - Approve/reject linkleri oluşturulur.
4. Talep `Requests` Google Sheet sayfasına eklenir.
5. Webhook cevabı döner.

## Kurulumda değiştirilecek alanlar

- Google Sheets node credential'ı yeniden seçilmeli.
- `REPLACE_WITH_STUDENT_REQUESTS_GOOGLE_SHEET_ID` kendi Sheet ID'nizle değiştirilmeli.
- Code node içindeki `https://YOUR_N8N_DOMAIN.example` kendi n8n domaininizle değiştirilmeli.

## Not

Demo sürümde token üretimi JavaScript `Math.random()` ile yapılır. Production için kriptografik random kullanılması önerilir.

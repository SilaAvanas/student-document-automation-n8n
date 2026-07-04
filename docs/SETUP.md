# Kurulum Rehberi

## 1. Google Sheets hazırlığı

Bir Google Sheet oluşturun ve iki sayfa ekleyin:

- `Requests`: Talep kayıtları, onay/red durumları ve belge linkleri tutulur.
- `Students`: Öğrenci ana veri tablosudur. Onay workflow'u öğrenci numarasına göre bu sayfadan bilgi çeker.

Kolon listesi için `SHEET_SCHEMA.md` dosyasına bakın.

## 2. Workflow import sırası

n8n içinde aşağıdaki JSON dosyalarını import edin:

1. `workflows/01_TalepAl/workflow.json`
2. `workflows/02A_Approve/workflow.json`
3. `workflows/02B_Reject/workflow.json`

Import sonrası workflow'lar varsayılan olarak pasif gelir. Testlerden sonra aktif hale getirin.

## 3. Placeholder alanlarını değiştirin

Workflow içindeki şu değeri kendi Google Sheet ID'nizle değiştirin:

```text
REPLACE_WITH_STUDENT_REQUESTS_GOOGLE_SHEET_ID
```

`01_TalepAl` workflow'undaki Code node içinde şu değeri kendi n8n adresinizle değiştirin:

```text
https://YOUR_N8N_DOMAIN.example
```

Örnek:

```text
https://n8n.yourdomain.com
```

## 4. Credential bağlantıları

Temizlenmiş public sürümde credential ID ve adları kaldırılmıştır. Aşağıdaki node'lara import sonrası kendi credential'larınızı yeniden bağlayın:

- Google Sheets node'ları
- Google Docs node'u
- Google Drive node'u
- Google Gemini Chat Model node'u, kullanıyorsanız

## 5. Webhook endpointleri

Workflow'lar aktif olduktan sonra beklenen endpointler:

```text
POST /webhook/talep
GET  /webhook/approve?token=...
GET  /webhook/reject?token=...
```

Test modunda çalışırken n8n, endpointleri `/webhook-test/...` olarak verebilir.

## 6. Test akışı

1. `01_TalepAl` workflow'unu test modunda çalıştırın.
2. Örnek POST isteği gönderin.
3. `Requests` sayfasına yeni kayıt geldiğini kontrol edin.
4. Kayıttaki `approveUrl`/üretilen approve linki ile `02A_Approve` workflow'unu test edin.
5. Alternatif olarak reject linki ile `02B_Reject` workflow'unu test edin.

## 7. Canlıya alma

- Workflow'ları aktif hale getirin.
- Google Sheet paylaşım izinlerini sadece gerekli kişilerle sınırlayın.
- Webhook URL'lerini herkese açık ortamlarda paylaşmayın.
- Token süresini ve token kullanım kontrolünü ihtiyaçlarınıza göre gözden geçirin.

# Student Request Automation with n8n

Bu depo, n8n ile hazırlanmış örnek bir **öğrenci belge/talep onay otomasyonu** içerir. Workflow dosyaları GitHub'da paylaşılabilecek şekilde temizlenmiştir: credential referansları, gerçek Google Sheet ID'leri, cached Google URL'leri, n8n instance ID ve webhook ID değerleri kaldırılmıştır.

## Proje ne yapar?

Sistem üç ayrı n8n workflow'undan oluşur:

1. **01_TalepAl**: Öğrenciden gelen talebi webhook üzerinden alır, `requestId` ve `approvalToken` üretir, talebi Google Sheets log tablosuna yazar.
2. **02A_Approve**: Yetkili onay linkine tıkladığında token kontrolü yapar, öğrenci bilgisini ana tablodan çeker, Google Docs belgesi oluşturur, belge linkini paylaşır ve log kaydını günceller.
3. **02B_Reject**: Yetkili red linkine tıkladığında token kontrolü yapar, talebi reddedilmiş olarak işaretler ve belge oluşturmaz.

## Klasör yapısı

```text
student-request-automation-github/
├─ README.md
├─ .env.example
├─ .gitignore
├─ docs/
│  ├─ SETUP.md
│  ├─ SHEET_SCHEMA.md
│  └─ SECURITY.md
└─ workflows/
   ├─ 01_TalepAl/
   │  ├─ README.md
   │  └─ workflow.json
   ├─ 02A_Approve/
   │  ├─ README.md
   │  └─ workflow.json
   └─ 02B_Reject/
      ├─ README.md
      └─ workflow.json
```

## Gereksinimler

- n8n
- Google Sheets OAuth credential
- Google Docs OAuth credential
- Google Drive OAuth credential
- İsteğe bağlı: Google Gemini API credential

> Not: Paylaşılan public sürümde credential bilgileri yoktur. Import sonrası n8n içinde ilgili node'lara kendi credential'larınızı yeniden bağlamanız gerekir.

## Hızlı kurulum

1. Google Sheets tarafında iki sayfa oluşturun:
   - `Requests`: talep/log kayıtları
   - `Students`: öğrenci ana veri tablosu
2. `docs/SHEET_SCHEMA.md` dosyasındaki kolonları ekleyin.
3. n8n içine sırasıyla workflow JSON dosyalarını import edin:
   - `workflows/01_TalepAl/workflow.json`
   - `workflows/02A_Approve/workflow.json`
   - `workflows/02B_Reject/workflow.json`
4. Google Sheets/Docs/Drive/Gemini node'larına kendi credential'larınızı seçin.
5. `REPLACE_WITH_STUDENT_REQUESTS_GOOGLE_SHEET_ID` alanlarını kendi Google Sheet ID'nizle değiştirin.
6. `01_TalepAl` workflow'undaki Code node içinde bulunan `https://YOUR_N8N_DOMAIN.example` değerini kendi n8n domaininizle değiştirin.
7. Workflow'ları aktif hale getirip test edin.

Detaylı anlatım için: [`docs/SETUP.md`](docs/SETUP.md)

## Örnek istek

```bash
curl -X POST "https://YOUR_N8N_DOMAIN.example/webhook/talep" \
  -H "Content-Type: application/json" \
  -d '{
    "studentNo": "202400001",
    "email": "student@example.com",
    "requestType": "Öğrenci Belgesi"
  }'
```

## Güvenlik notu

Bu proje demo/portföy amaçlı temizlenmiş bir örnektir. Production kullanımdan önce token üretimi, kimlik doğrulama, rate limit, yetkili personel doğrulama ve veri erişim izinleri ayrıca güçlendirilmelidir.

## Lisans

Bu depo örnek/portföy projesi olarak paylaşılabilir. Kurum içi veya gerçek öğrenci verisiyle kullanmadan önce gizlilik ve KVKK süreçlerinize göre gözden geçirin.

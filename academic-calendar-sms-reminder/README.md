# Academic Calendar SMS Reminder

Bu n8n workflow'u, akademik takvimde yaklaşan etkinlikleri kontrol edip SMS bilgilendirmesi gönderen örnek bir otomasyondur.

## Akış

1. Schedule Trigger her sabah çalışır.
2. Takvim verisi okunur veya demo veri üretilir.
3. Yarın başlayacak etkinlik filtrelenir.
4. Twilio ile SMS gönderilir.

## Gerekenler

- n8n
- Twilio hesabı
- Twilio credential
- SMS gönderim numarası
- Alıcı telefon numarası

## Ortam Değişkenleri

- `TWILIO_PHONE_NUMBER`
- `NOTIFICATION_PHONE`

## Not

Bu sürüm demo amaçlıdır. Gerçek takvim kaynağına bağlamak için `Takvimi Oku` node'u Google Sheets, HTTP Request veya veritabanı kaynağıyla değiştirilebilir.

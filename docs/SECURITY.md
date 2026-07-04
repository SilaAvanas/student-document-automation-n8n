# Güvenlik Notları

Bu depo GitHub/portföy paylaşımı için temizlenmiştir. Yine de production kullanımında aşağıdaki maddeleri uygulamanız önerilir.

## Temizlenen bilgiler

- Google Sheet gerçek dosya ID'si
- Google Sheets/Docs/Drive credential ID ve adları
- Google Gemini credential referansı
- n8n instance ID
- n8n webhook ID değerleri
- Cached Google Sheet URL'leri
- Yerel geliştirme adresi

## Production önerileri

- Webhook endpointlerini yetkilendirme olmadan herkese açık bırakmayın.
- Onay/red linklerindeki token değerlerini daha güçlü üretin. Mümkünse `crypto.randomUUID()` veya kriptografik random kullanın.
- Token değerlerini tek kullanımlık ve süreli tutun.
- Token kullanıldıktan sonra tekrar kullanımını engelleyin.
- Google Sheet erişimini sadece gerekli servis hesabı/kullanıcılarla sınırlayın.
- Öğrenci kişisel verilerini public repo içinde asla paylaşmayın.
- Loglarda gerçek öğrenci verisi, e-posta, belge linki ve token tutarken KVKK gerekliliklerini değerlendirin.
- Google Docs paylaşımında `anyone reader` ayarı herkese açık link oluşturabilir; kurum politikasına göre sınırlayın.

## GitHub'a koymadan önce kontrol listesi

- [ ] `.env` dosyası yok
- [ ] Gerçek credential export'u yok
- [ ] Google Sheet/Docs/Drive linkleri yok
- [ ] Gerçek öğrenci verisi yok
- [ ] Gerçek webhook domain/token örneği yok
- [ ] Workflow JSON dosyalarında credential alanları boş/temiz

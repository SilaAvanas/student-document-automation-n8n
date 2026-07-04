# Student Affairs Docs - Ollama Local Demo

Bu n8n workflow'u, yerel Ollama modeli kullanarak öğrenci belge talebini analiz eden ve demo HTML belge çıktısı oluşturan çok ajanlı bir otomasyon örneğidir.

## Akış

1. Demo talep oluşturulur.
2. Ollama ile belge türü ve öğrenci bilgileri çıkarılır.
3. Demo öğrenci kayıtları ile eşleştirme yapılır.
4. Uygunluk kontrolü yapılır.
5. Belge metni üretilir.
6. Kalite kontrol ajanı sonucu denetler.
7. HTML belge oluşturulur.
8. Sonuç özeti üretilir.

## Desteklenen Belge Türleri

- Öğrenci durum belgesi
- Geçici mezuniyet belgesi
- Askerlik için öğrenci durum belgesi

## Gerekenler

- n8n
- Ollama
- Yerel LLM modeli, örnek: `qwen2.5:3b-instruct`

## Ortam Değişkenleri

- `OLLAMA_BASE_URL`
- `OLLAMA_MODEL`

## Not

Bu workflow gerçek öğrenci işleri sistemine bağlı değildir. İçindeki öğrenci kayıtları demo amaçlıdır.

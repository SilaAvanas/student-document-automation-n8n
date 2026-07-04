# Google Sheets Kolon Şeması

## `Requests` sayfası

Talep ve onay/red sürecinin loglandığı ana sayfadır.

| Kolon | Açıklama |
|---|---|
| requestId | Sistem tarafından üretilen benzersiz talep numarası |
| studentNo | Öğrenci numarası |
| email | Öğrenci e-posta adresi |
| requestType | Talep edilen belge/talep türü |
| status | Genel süreç durumu |
| createdAt | Talebin oluşturulma zamanı |
| approvalStatus | PENDING / APPROVED / REJECTED gibi onay durumu |
| approvalBy | İşlemi yapan kullanıcı/rol |
| approvalAt | Onay/red zamanı |
| approvalToken | Tek kullanımlık onay/red token değeri |
| documentStatus | Belge üretim durumu |
| documentUrl | Oluşturulan Google Docs belge linki |
| documentType | Oluşturulan belge türü |
| errorMessage | Hata mesajı |
| studentName | Öğrenci adı soyadı |
| department | Bölüm |
| program | Program |
| class | Sınıf |
| rejectReason | Red gerekçesi |
| tokenExpiresAt | Token geçerlilik son zamanı |
| tokenUsedAt | Token kullanım zamanı |
| tokenUsedBy | Tokenı kullanan rol/kullanıcı |
| isTokenUsed | Token kullanıldı mı? |
| notificationStatus | Bildirim durumu, kullanılacaksa |
| notificationSentAt | Bildirim gönderim zamanı, kullanılacaksa |
| pdfUrl | PDF linki, kullanılacaksa |
| verificationCode | Doğrulama kodu, kullanılacaksa |

## `Students` sayfası

Onay workflow'u öğrenci bilgilerini bu sayfadan çeker.

| Kolon | Açıklama |
|---|---|
| studentNo | Öğrenci numarası, eşleştirme anahtarı |
| firstName | Öğrenci adı |
| lastName | Öğrenci soyadı |
| faculty | Fakülte |
| department | Bölüm |
| program | Program |
| class | Sınıf |

## Örnek `Students` satırı

| studentNo | firstName | lastName | faculty | department | program | class |
|---|---|---|---|---|---|---|
| 202400001 | Ali | Yılmaz | İktisadi ve İdari Bilimler | Yönetim Bilişim Sistemleri | Lisans | 4 |

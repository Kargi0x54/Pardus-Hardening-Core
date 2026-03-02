# 📑 TEKNİK ANALİZ RAPORU (Vaka No: 2024-APT-09)

**Sınıflandırma:** TLP:RED (Strictly Confidential)  
**Birim:** SGB - Olay Müdahale Birimi (CSIRT)  
**Tarih:** 2024-10-25  

---

## 🔍 1. Vaka Özeti
Kritik kamu altyapısı ağlarında (K-Net) tespit edilen sıra dışı HTTP/2 trafiği üzerine yapılan incelemede, sistem belleğinde iz bırakmayan (fileless) bir zararlı yazılım varyantı tespit edilmiştir. 

## 🛡️ 2. Tespit Edilen Göstergeler (IoC)
- **Komuta Kontrol (C2) Adresi:** `185.x.x.x` (Analiz aşamasında maskelenmiştir)
- **Persistence Metodu:** Sistem açılışında `systemd` servisleri arasına gizlenmiş `.sh` betiği.
- **Payload:** AES-128 ile şifrelenmiş, bellek üzerinden (In-memory) çalışan Python tabanlı backdoor.

## ⚙️ 3. Analiz Notları (Operatör: 0xKargi)
> "Zararlı yazılımın kod yapısı incelendiğinde, kullanılan 'obfuscation' tekniklerinin daha önce raporlanan **APT29** saldırılarıyla %84 oranında benzerlik gösterdiği saptanmıştır. Özellikle `socket` kütüphanesinin düşük seviyeli kullanımı, doğrudan kernel bypass denemeleri içerdiğini kanıtlıyor."

## 🛠️ 4. Uygulanan Aksiyonlar
- [x] İlgili IP adresleri ulusal firewall (Güvenlik Duvarı) üzerinden bloklandı.
- [x] Etkilenen sunucular `Pardus-Hardening-Core` betiği ile yeniden yapılandırıldı.
- [x] RAM imajları alınarak derinlemesine analiz için SGB-Merkez laboratuvarına iletildi.

---
*Bu raporun izinsiz paylaşılması 5237 sayılı TCK m.327 (Devletin Güvenliğine İlişkin Belgeler) kapsamında suç teşkil eder.*

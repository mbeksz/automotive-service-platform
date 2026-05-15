# Otomotiv Servis Platformu

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white" />
  <img src="https://img.shields.io/badge/MSSQL-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Durum-Canlıda-brightgreen?style=flat-square" />
  <img src="https://img.shields.io/badge/Tür-Özel%20Kurumsal%20Yazılım-blue?style=flat-square" />
</p>

---

> Bu proje bir otomotiv bayilik grubu için özel kurumsal yazılım olarak geliştirilmiştir.
> Bu repo yalnızca proje yapısını ve dokümantasyonu **portfolyo amaçlı** paylaşmaktadır. Kaynak kod dahil edilmemiştir.

---

## Genel Bakış

Birden fazla şube ve markayı yöneten otomotiv servisleri için geliştirilmiş **çok modüllü web platformu**. Sistem üç temel iş akışını kapsar:

| Modül | Açıklama |
|-------|----------|
| Servis Randevu | Müşteriye açık çok adımlı rezervasyon portalı |
| Test Sürüşü | Zoho CRM entegrasyonlu ayrı rezervasyon akışı |
| Teslimat Yönetimi | Finans/satış ekiplerine dijital onay zinciri |

Platform hem müşterilere hem de iç ekiplere hizmet verir; gerçek zamanlı bildirimler, WhatsApp entegrasyonu ve rol tabanlı yetki kontrolü içerir.

---

## Teknoloji Yığını

```
Backend   → Node.js · Express · TypeScript
Frontend  → React 18 · TypeScript · Vite
Veritabanı→ Microsoft SQL Server
Auth      → JWT · RBAC (veritabanı tabanlı izin sistemi)
Bildirim  → WhatsApp Business (n8n webhook) · SMS
Gerçek Zamanlı → Server-Sent Events (SSE)
CRM       → Zoho CRM API
Zamanlama → node-cron
Dağıtım   → PM2 · Nginx
```

---

## Mimari

```
backend/
├── src/
│   ├── routes/           # Express route grupları
│   │   ├── publicRoutes.ts
│   │   ├── authRoutes.ts
│   │   ├── adminRoutes.ts
│   │   ├── appointmentRoutes.ts
│   │   └── deliveryRoutes.ts
│   ├── controllers/      # Alan bazlı iş mantığı
│   ├── middleware/        # JWT doğrulama, RBAC kontrolleri
│   ├── services/          # WhatsApp, SMS, hatırlatıcılar, SSE, Zoho
│   ├── config/
│   └── utils/

frontend/
├── src/
│   ├── pages/
│   │   ├── public/        # Müşteri rezervasyon sayfaları
│   │   └── admin/         # İç yönetim paneli
│   ├── components/
│   │   ├── wizard/        # Adım adım servis rezervasyon akışı
│   │   └── testdrive-wizard/
│   ├── context/           # Sihirbaz state yönetimi
│   └── api/               # JWT interceptörlü Axios
```

---

## Temel Özellikler

- Tek platform üzerinden çok markalı, çok şubeli yönetim
- Hız sınırlamalı OTP telefon doğrulaması
- Otomatik WhatsApp ve SMS hatırlatmaları (node-cron)
- SSE ile anlık teslimat durum güncellemeleri
- Veritabanı tabanlı granüler RBAC sistemi
- Test sürüşü leadleri için Zoho CRM otomatik senkronizasyonu
- Integer doğrulama middleware ile güvenli public API

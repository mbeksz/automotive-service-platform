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

<p align="center">
  <a href="https://online-randevu.otomol.com/randevu-olustur">
    <img src="https://img.shields.io/badge/Servis%20Randevu-Canlı%20Demo%20→-2563EB?style=for-the-badge&logo=googlechrome&logoColor=white" />
  </a>
  &nbsp;&nbsp;
  <a href="https://online-randevu.otomol.com/test-surusu">
    <img src="https://img.shields.io/badge/Test%20Sürüşü-Canlı%20Demo%20→-16A34A?style=for-the-badge&logo=googlechrome&logoColor=white" />
  </a>
</p>

---

> Bu proje bir otomotiv bayilik grubu için **özel kurumsal yazılım** olarak geliştirilmiştir.
> Bu repo yalnızca proje yapısını ve dokümantasyonu **portfolyo amaçlı** paylaşmaktadır — kaynak kod dahil edilmemiştir.

---

## Genel Bakış

Birden fazla şube ve markayı yöneten otomotiv servisleri için geliştirilmiş **çok modüllü web platformu**. Sistem üç temel iş akışını kapsar:

| Modül | Açıklama |
|-------|----------|
| 🔧 Servis Randevu | Müşterilere açık, OTP doğrulamalı çok adımlı rezervasyon portalı |
| 🚗 Test Sürüşü | Zoho CRM entegrasyonlu ayrı rezervasyon akışı |
| 📦 Teslimat Yönetimi | Finans ve satış ekiplerine dijital onay zinciri |

Platform hem müşterilere hem iç ekiplere hizmet verir; gerçek zamanlı bildirimler, WhatsApp entegrasyonu ve rol tabanlı yetki kontrolü içerir.

---

## Teknoloji Yığını

```
Backend        → Node.js · Express · TypeScript
Frontend       → React 18 · TypeScript · Vite
Veritabanı     → Microsoft SQL Server
Auth           → JWT · RBAC (veritabanı tabanlı izin sistemi)
Bildirim       → WhatsApp Business API (n8n webhook) · SMS
Gerçek Zamanlı → Server-Sent Events (SSE)
CRM            → Zoho CRM API
Zamanlama      → node-cron (hatırlatmalar)
Dağıtım        → PM2 · Nginx
```

---

## Mimari

```
backend/
├── src/
│   ├── routes/           # Express route grupları (public, auth, admin, delivery)
│   ├── controllers/      # Alan bazlı iş mantığı
│   ├── middleware/        # JWT doğrulama, RBAC kontrolleri
│   ├── services/          # WhatsApp, SMS, hatırlatıcılar, SSE, Zoho CRM
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
│   ├── context/           # Wizard state yönetimi
│   └── api/               # JWT interceptörlü Axios instance
```

---

## Ekran Görüntüleri

<p align="center">
  <img width="900" alt="Servis Randevu" src="https://github.com/user-attachments/assets/0aada85b-b598-4283-8a52-c0db56337b1f" />
</p>

<p align="center">
  <img width="900" alt="Test Sürüşü" src="https://github.com/user-attachments/assets/af320662-7480-4f59-92c7-e1163b6219d6" />
</p>

<p align="center">
  <img height="534" alt="Mobil Görünüm" src="https://github.com/user-attachments/assets/a42e65ca-ffa8-40d1-8ca1-01ece09b4b59" />
</p>

---

## Temel Özellikler

- Tek platform üzerinden çok markalı, çok şubeli yönetim
- Hız sınırlamalı OTP telefon doğrulaması (60sn cooldown, saatte 5 istek)
- Otomatik WhatsApp ve SMS hatırlatmaları (node-cron)
- SSE ile anlık teslimat durum güncellemeleri
- Veritabanı tabanlı granüler RBAC sistemi
- Test sürüşü leadleri için Zoho CRM otomatik senkronizasyonu
- Integer doğrulama middleware ile güvenli public API


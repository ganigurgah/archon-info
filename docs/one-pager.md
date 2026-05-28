---
marp: true
---

# Archon — Executive Summary

**Her Proje İçin Kendi Yapay Zeka Mimarı**

---

## Problem

Yazılım ekipleri üç kritik sorunla karşılaşır:

- **Bilgi kaybı:** Kıdemli geliştirici ayrıldığında yıllarca biriken proje bilgisi onunla gider
- **Kalite tutarsızlığı:** Her geliştirici farklı standartlar uygular; code review verimsiz ve özneldir
- **Yüksek onboarding maliyeti:** Yeni geliştirici projeye adapte olmak için 2–4 ay harcar; bu sürede ekip yavaşlar

Mevcut yapay zeka araçları (ChatGPT, GitHub Copilot) genel bilgiyle çalışır — sizin projenizi tanımaz, verilerinizi buluta gönderir.

---

## Çözüm

**Archon**, her yazılım projesi için ayrı bir yapay zeka bilgi tabanı oluşturur ve o projenin kaynak kodunu, analiz belgelerini, bakım geçmişini ve domain dilini öğrenen özel bir model eğitir. Tüm bu süreç tamamen kurumunuzun altyapısında, veri dışarı çıkmadan gerçekleşir.

Archon yalnızca soru-cevap aracı değildir: analiz aşamasından bakım aşamasına kadar yazılım geliştirme sürecinin tamamına entegre olur — kod review, PR analizi, test üretimi, onboarding desteği ve teknik borç raporlaması dahil.

---

## Temel Özellikler

| | |
|---|---|
| Proje bazlı RAG bilgi tabanı | QLoRA fine-tuning ile özel model eğitimi |
| Otomatik PR code review (GitHub/GitLab) | Domain Adaptation — manuel veri girişi gerekmez |
| SDLC faz yönetimi (Kaynak Kod / Analiz / Bakım) | Model registry — versiyon, deploy, rollback |
| Onboarding asistanı | Teknik borç analizi |

---

## Kurumsal Hazırlık

**On-Premise & Air-Gapped**
İnternet bağlantısı gerektirmez. Finans, kamu, savunma sektörüne uygun hava geçirmez kurulum desteği.

**Güvenlik & Uyumluluk**
Departman bazlı veri izolasyonu (multi-tenant), audit log, quota yönetimi. KVKK ve kurumsal uyumluluk gereksinimleri karşılanır.

**Entegrasyon**
REST API, GitHub/GitLab webhook, Confluence, Jira entegrasyonu. Mevcut araçlarla birlikte çalışır.

---

## Teknik Temel

Java 21 / Spring Boot 3 · Python 3 · ChromaDB (vektör veritabanı) · Ollama (yerel LLM çalıştırma) · QLoRA / GGUF · PostgreSQL · Maven multi-module mimarisi

---

## İletişim

**E-posta:** ganigurgah@gmail.com

*Archon — Veri kurumunuzda kalır. Bilgi birikir. Kalite artar.*

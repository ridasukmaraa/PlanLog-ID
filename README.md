# 🌱 PlanLog ID

**PlanLog ID** adalah aplikasi iOS untuk pencatatan siklus tanam hidroponik dari penyemaian hingga panen. Aplikasi ini dirancang dengan pendekatan **Clean Architecture** dan **Domain-Driven Design (DDD)**, berfokus pada pencatatan **batch tanaman**, umur tanaman (**HSS & HST**), serta data lingkungan seperti **EC, TDS, dan suhu air**.

Aplikasi bersifat **local-first** menggunakan **SwiftData**, dan telah dipersiapkan untuk pengembangan sinkronisasi cloud (Firebase / custom backend) pada rilis berikutnya.

---

## ✨ Fitur Utama

* 📦 **Batch-based planting log**

  * Satu batch mewakili satu siklus tanam
  * Mendukung banyak lubang tanam dalam satu batch

* 🌱 **Lifecycle tracking**

  * Semai → Peremajaan → Produksi → Panen
  * State machine dengan aturan transisi yang ketat

* 📆 **Umur Tanaman**

  * HSS (Hari Setelah Semai)
  * HST (Hari Setelah Tanam)
  * Umur dihitung otomatis (derived data)

* 📊 **Pencatatan Lingkungan**

  * EC / TDS (ppm)
  * Suhu air
  * Timestamp & snapshot usia tanaman

* 🧺 **Panen Parsial & Total**

  * Mendukung panen bertahap
  * Histori panen tercatat rapi

* 💾 **Local-first storage**

  * Offline penuh
  * Siap dikembangkan ke cloud sync

---

## 🏗 Arsitektur

PlanLog ID menggunakan **Clean Architecture** untuk menjaga skalabilitas, testability, dan maintainability.

```
Presentation (SwiftUI)
    ↓
Application (Use Cases)
    ↓
Domain (Entities & Business Rules)
    ↓
Data (SwiftData - Local Storage)
```

### Prinsip Utama

* UI tidak bergantung pada database
* Domain tidak bergantung pada framework
* Semua perubahan state lewat Use Case

---

## 🧠 Konsep Domain Inti

### PlantBatch

Satu batch merepresentasikan satu siklus tanam:

* Disemai bersama
* Dirawat bersama
* Dipanen bersama atau parsial

### GrowStage

Lifecycle batch:

* `seeding`
* `nursery`
* `production`
* `harvested` (final)
* `failed` (final)

### Usia Tanaman

* **HSS** = Hari Setelah Semai
* **HST** = Hari Setelah Tanam

Keduanya adalah **derived value**, dihitung dari tanggal referensi.

---

## 🧱 Tech Stack

* **SwiftUI** — Declarative UI
* **SwiftData** — Local persistence (iOS 17+)
* **Clean Architecture**
* **Domain-Driven Design (DDD)**
* **MVVM (Presentation layer)**
* **Unit Testing (Domain & Use Case)**

---

## 📁 Struktur Folder

```
PlanLogID
├── Domain
│   ├── Entities
│   ├── ValueObjects
│   └── UseCases
│
├── Application
│   └── UseCasesImpl
│
├── Data
│   ├── Local
│   │   ├── Models        // SwiftData @Model
│   │   ├── Mappers
│   │   └── Repositories
│
├── Presentation
│   ├── Views
│   └── ViewModels
│
├── Shared
│   └── Extensions
```

---

## 🚀 Getting Started

### Requirements

* Xcode 15+
* iOS 17+
* Swift 5.9+

### Setup

1. Clone repository ini
2. Buka `PlanLogID.xcodeproj`
3. Build & Run di simulator atau device

---

## 🧪 Testing

* Unit test difokuskan pada:

  * Domain entities
  * Use case logic
* Repository dapat dimock untuk testing

UI testing dilakukan terpisah.

---

## 🛣 Roadmap

### v1 (Current)

* Local-first storage
* Batch & measurement logging
* Manual lifecycle transition

### v2 (Planned)

* Cloud sync (Firebase / custom API)
* Insight & rekomendasi
* Grafik & analisis data
* Multi lokasi & rak

---

## 📌 Catatan

Project ini dikembangkan sebagai:

* Produk nyata untuk pencatatan hidroponik
* Showcase arsitektur iOS modern
* Fondasi aplikasi data-driven agriculture

---

## 📄 License

MIT License

---

> **PlanLog ID — Catatan tanam dari semai sampai panen.** 🌱

# 📘 CRUD Teman API (AWS Lambda + DynamoDB)

API sederhana untuk mengelola data teman (`nama`, `umur`) menggunakan AWS Lambda, API Gateway, dan DynamoDB.

---

## 🧱 Arsitektur

* AWS Lambda (Python)
* Amazon API Gateway (HTTP API)
* Amazon DynamoDB

---

## 🗃️ Setup DynamoDB

### 1. Buat Table

Masuk ke DynamoDB → Create table:

* **Table name**: `Teman`
* **Partition key**:

  * Name: `nama`
  * Type: String

---

## ⚙️ Setup Lambda

### 1. Environment Variable

Tambahkan di Lambda:

| Key            | Value |
| -------------- | ----- |
| DYNAMODB_TABLE | Teman |

---

## 🌐 Setup API Gateway

Gunakan REST API dengan Lambda Proxy Integration.

### Routes:

| Method | Endpoint      | Deskripsi        |
| ------ | ------------- | ---------------- |
| GET    | /teman        | Ambil semua data |
| POST   | /teman        | Tambah data      |
| GET    | /teman/{nama} | Ambil 1 data     |
| PUT    | /teman/{nama} | Update data      |
| DELETE | /teman/{nama} | Hapus data       |

---

## 🚀 Cara Pakai API

Ganti `BASE_URL` dengan endpoint dari API Gateway.

---

### ✅ 1. Create (POST /teman)

```bash
curl -X POST $BASE_URL/teman \
  -H "Content-Type: application/json" \
  -d '{
    "nama": "Budi",
    "umur": 25
  }'
```

---

### ✅ 2. Get All (GET /teman)

```bash
curl $BASE_URL/teman
```

---

### ✅ 3. Get by Nama (GET /teman/{nama})

```bash
curl $BASE_URL/teman/Budi
```

---

### ✅ 4. Update (PUT /teman/{nama})

```bash
curl -X PUT $BASE_URL/teman/Budi \
  -H "Content-Type: application/json" \
  -d '{
    "umur": 26
  }'
```

---

### ✅ 5. Delete (DELETE /teman/{nama})

```bash
curl -X DELETE $BASE_URL/teman/Budi
```

---

## ⚠️ Catatan Penting

* Field `nama` adalah **primary key** (harus unik)

---

## 📦 Contoh Response

```json
{
  "nama": "Budi",
  "umur": 25
}
```

---

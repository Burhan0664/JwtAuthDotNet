# 🔐 JwtAuthDotNet

Bu proje, **ASP.NET Core** kullanılarak geliştirilmiş ve **JWT (JSON Web Token)** tabanlı **Authentication (Kimlik Doğrulama)** ve **Authorization (Yetkilendirme)** işlemlerini gerçekleştiren bir Web API uygulamasıdır.

Amaç; kullanıcıların sisteme güvenli bir şekilde giriş yapmasını sağlamak, giriş sonrası oluşturulan JWT token ile korumalı endpoint’lere erişimi kontrol etmektir.

---

## 🚀 Proje Özellikleri

* JWT tabanlı kimlik doğrulama (Authentication)
* Token üzerinden rol ve yetki kontrolü (Authorization)
* Kullanıcı kayıt (Register) ve giriş (Login) işlemleri
* `[Authorize]` attribute ile korumalı endpoint’ler
* Stateless (oturumsuz) güvenli API yapısı

---

## 🛠️ Kullanılan Teknolojiler

* **ASP.NET Core Web API**
* **JWT (JSON Web Token)**
* **Microsoft.AspNetCore.Authentication.JwtBearer**
* **Entity Framework Core**
* **LINQ**
* **C#**

---

## 🧠 JWT Authentication & Authorization Mantığı

### 🔑 Authentication (Kimlik Doğrulama)

1. Kullanıcı `Login` endpoint’i üzerinden giriş yapar
2. Kullanıcı bilgileri doğrulanır
3. Başarılı giriş sonrası kullanıcıya bir **JWT Token** üretilir
4. Token, client tarafında saklanır

---

### 🛡️ Authorization (Yetkilendirme)

* Kullanıcı, korumalı endpoint’lere istek atarken HTTP Header üzerinden token gönderir:

```
Authorization: Bearer <JWT_TOKEN>
```

* `[Authorize]` attribute ile işaretlenen endpoint’lere sadece geçerli token’a sahip kullanıcılar erişebilir
* Token içerisindeki **claim** bilgileri (kullanıcı ID, rol vb.) üzerinden yetkilendirme yapılır

---

## 📦 API Endpoint’leri

### 🧾 Register

**POST** `/api/auth/register`

**Request Body**

```json
{
  "username": "burhan",
  "email": "burhan@example.com",
  "password": "123456"
}
```

---

### 🔑 Login

**POST** `/api/auth/login`

**Response (Örnek)**

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expiration": "2026-01-26T18:00:00"
}
```

---

### 🔒 Korumalı Endpoint

**GET** `/api/secure`

Bu endpoint’e erişmek için geçerli bir JWT token gereklidir.

---

## ⚙️ JWT Yapılandırması

JWT ayarları `Program.cs` veya `appsettings.json` dosyası üzerinden yapılandırılmıştır:

* Secret Key
* Issuer
* Audience
* Token süresi (Expiration)

Token doğrulama işlemleri `JwtBearer` middleware ile yapılmaktadır.

---

## 🚀 Kurulum ve Çalıştırma

1. Repoyu klonlayın

```bash
git clone https://github.com/Burhan0664/JwtAuthDotNet.git
```

2. Gerekli paketleri yükleyin

```bash
dotnet restore
```

3. Veritabanını oluşturun (varsa)

```bash
dotnet ef database update
```

4. Uygulamayı çalıştırın

```bash
dotnet run
```

---

## 📌 Kullanım Senaryosu

* Kullanıcı sisteme giriş yapar
* Backend JWT token üretir
* Client, token ile korumalı endpoint’lere istek atar
* Token geçerliyse istek kabul edilir, değilse reddedilir

---

## 📄 Lisans

Bu proje eğitim ve portföy amaçlı geliştirilmiştir.

---

## 👨‍💻 Geliştirici

**Burhan Çavdaroğlu**
📍 Ankara, Türkiye
🔗 LinkedIn: [https://linkedin.com/i](https://linkedin.com/i)

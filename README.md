# 🚀 Docker ile Nginx Tabanlı Statik Web Sitesi Yayınlama

Bu proje, Docker kullanılarak Nginx imajı ile oluşturulmuş basit bir statik web sitesini container içinde çalıştırmayı amaçlamaktadır. Web sitesi, HTML/CSS/JS dosyalarıyla birlikte 8080 portu üzerinden sunulur.

---

## 📁 Proje Yapısı

```
Alistirma1.3/
├── app/
│   └── index.html         # Statik web sayfası
├── Dockerfile             # Docker yapılandırma dosyası
└── nginx.conf             # Nginx yapılandırma dosyası
```

---

## 🧰 Kullanılan Teknolojiler

- 🐳 Docker
- 🌐 Nginx (alpine tabanlı)
- 💻 HTML, CSS, JS

---

## ⚙️ Kurulum ve Çalıştırma Adımları

### 1️⃣ Docker Image Oluştur

```bash
docker build -t my-nginx-app .
```

### 2️⃣ Container’ı Çalıştır

```bash
docker run -d -p 8080:8080 my-nginx-app
```

### 3️⃣ Tarayıcıda Aç

```
http://localhost:8080
```

---

## 📦 Dockerfile Açıklaması

```dockerfile
FROM nginx:alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY app /usr/share/nginx/html
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]
```

**Açıklamalar:**
- `nginx:alpine`: Hafif ve hızlı bir Nginx imajıdır.
- `COPY nginx.conf`: Özel Nginx yapılandırmanı container'a aktarır.
- `COPY app`: Statik dosyaları Nginx’in sunacağı dizine kopyalar.
- `EXPOSE 8080`: 8080 portunu dış dünyaya açar.
- `CMD`: Nginx'i foreground modda başlatır, container açık kalır.

---

## 🔧 nginx.conf Açıklaması

```nginx
events { }

http {
    server {
        listen 8080;
        location / {
            root /usr/share/nginx/html;
            index index.html;
        }
    }
}
```

**Açıklamalar:**
- `listen 8080`: Web sunucusunu 8080 portunda dinler.
- `root`: Statik dosyaların bulunduğu dizini belirtir.
- `index`: İlk yüklenecek dosya olarak `index.html` tanımlar.

---

## 👤 Geliştirici

- **Melike (mel-nur)**  
  GitHub: [https://github.com/mel-nur](https://github.com/mel-nur)

---

## 📌 Notlar

- Bu proje yalnızca statik içerik (HTML/CSS/JS) yayınlamak için uygundur.
- Backend veya veri tabanı bağlantısı içermez.
- Docker kurulumu sisteminizde önceden yapılmış olmalıdır.

---

```

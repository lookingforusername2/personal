# 🌐 Personal Site — راهنمای نصب و راه‌اندازی

سایت شخصی شما روی **GitHub Pages + Cloudflare Pages** با پنل ادمین کامل.

---

## ساختار فایل‌ها

```
your-repo/
├── index.html          ← سایت اصلی
├── admin.html          ← پنل مدیریت
├── config.js           ← تنظیمات (این را ویرایش کنید)
├── data.json           ← محتوای سایت (از پنل ادمین مدیریت می‌شه)
├── assets/
│   ├── music/          ← فایل‌های MP3 آپلود شده
│   └── images/         ← عکس‌های آپلود شده
└── README.md
```

---

## مرحله ۱ — ساخت GitHub Repository

1. وارد [github.com](https://github.com) شوید
2. روی **New repository** کلیک کنید
3. نام دلخواه بدهید (مثلاً `my-site`)
4. **Public** باشد (برای Cloudflare Pages رایگان)
5. همه فایل‌های این پوشه را آپلود کنید

---

## مرحله ۲ — ویرایش config.js

فایل `config.js` را باز کنید و این مقادیر را وارد کنید:

```javascript
window.SITE_CONFIG = {
  GITHUB_RAW:    "https://raw.githubusercontent.com/USERNAME/REPO/main",
  GITHUB_OWNER:  "USERNAME",     // نام کاربری GitHub شما
  GITHUB_REPO:   "REPO",         // نام repository
  GITHUB_BRANCH: "main",
  GITHUB_TOKEN:  ""              // اینجا خالی بگذارید
};
```

**مثال واقعی:**
```javascript
window.SITE_CONFIG = {
  GITHUB_RAW:    "https://raw.githubusercontent.com/ali123/my-site/main",
  GITHUB_OWNER:  "ali123",
  GITHUB_REPO:   "my-site",
  GITHUB_BRANCH: "main",
  GITHUB_TOKEN:  ""
};
```

---

## مرحله ۳ — ساخت GitHub Token (برای پنل ادمین)

1. GitHub → **Settings** → **Developer settings** → **Personal access tokens** → **Fine-grained tokens**
2. روی **Generate new token** کلیک کنید
3. تنظیمات:
   - **Repository access:** فقط `your-repo`
   - **Permissions → Contents:** `Read and Write`
4. روی **Generate token** کلیک کنید
5. توکن را کپی کنید (فقط یک‌بار نشان داده می‌شود!)

> ⚠️ **توکن را در config.js ننویسید!** هر بار که وارد پنل ادمین می‌شوید، توکن را در فرم ورود وارد کنید.

---

## مرحله ۴ — اتصال به Cloudflare Pages

1. وارد [pages.cloudflare.com](https://pages.cloudflare.com) شوید
2. **Create a project** → **Connect to Git**
3. Repository خود را انتخاب کنید
4. تنظیمات:
   - **Framework preset:** None
   - **Build command:** (خالی)
   - **Output directory:** `/` یا خالی
5. **Save and Deploy** کلیک کنید

سایت شما روی آدرسی مثل `your-repo.pages.dev` در دسترس خواهد بود.

---

## استفاده از پنل ادمین

1. به `your-site.pages.dev/admin.html` بروید
2. توکن GitHub خود را وارد کنید
3. هر تغییری که می‌دهید **مستقیماً روی GitHub** ذخیره می‌شود
4. Cloudflare Pages بعد از چند ثانیه سایت را به‌روزرسانی می‌کند

### آپلود فایل از پنل ادمین

- **آهنگ:** پنل ادمین → Music → Add Track → فایل MP3 را درگ کنید
- **عکس:** پنل ادمین → Gallery → Add Photo → تصویر را درگ کنید
- **عکس پروفایل:** پنل ادمین → Profile → عکس را آپلود کنید

> 📌 محدودیت: GitHub فایل‌های بیشتر از **50MB** را قبول نمی‌کند.

---

## سوالات متداول

**چرا سایت تغییرات را نشان نمی‌دهد؟**
- صبر کنید ۳۰-۶۰ ثانیه تا Cloudflare Pages بیلد جدید بزند
- یا `Ctrl+Shift+R` بزنید تا کش مرورگر پاک شود

**چطور دامین اختصاصی اضافه کنم؟**
- Cloudflare Pages → Settings → Custom domains

**آیا admin.html عمومی است؟**
- بله، ولی بدون توکن GitHub نمی‌توان تغییری داد
- اگر می‌خواهید پنهان‌تر باشد، نام فایل را عوض کنید (مثلاً `secret-panel.html`)

# صفحهٔ داوری یک‌پارچه المپیاد تیروتیر — IranTVTO × WorldSkills

**نسخه: ۱ (v1.0)** — این صفحه را می‌توانید **آنلاین یا آفلاین** استفاده کنید.

یک صفحهٔ وب تعاملی، سبک و آفلاین/آنلاین برای داوری مهارت‌ها بر اساس الگوی WSOS. شامل دو جدول **Judgement (۰–۳)** و **Measurement**، محاسبهٔ نمرهٔ نهایی با وزن‌ها، ذخیرهٔ محلی، خروجی **JSON/CSV (UTF‑8)**، چاپ A4، **Reset** و بارگذاری Rubric از `rubrics.json`.

> **توجه مهم:** محتوای Rubricها در این صفحه **خلاصهٔ اجرایی** از فایل‌های فنی هر مهارت (TD) است. برای اطلاعات کامل و به‌روز، حتماً به **PDF رسمی هر مهارت** مراجعه کنید:  
> **مرجع رسمی: [https://skill.irantvto.ir/td22](https://skill.irantvto.ir/td22)**

## محتویات ریپو

- `index.html` — نسخهٔ Ultimate صفحهٔ داوری (HTML مستقل، RTL، فونت فارسی، Tailwind CDN)
    
- `rubrics.json` — تعریف Rubric مهارت‌ها (وزن‌ها، معیارها/شاخص‌ها، چیپ‌های قوانین)
    
- `README.md` — راهنما (همین فایل)
    
- `LICENSE` — مجوز (MIT)
    

## راه‌اندازی سریع (آنلاین _یا_ آفلاین)

### گزینهٔ A) **آنلاین با GitHub Pages**

1. این فایل‌ها را در ریشهٔ ریپو قرار دهید (`index.html`، `rubrics.json`, `README.md`, `LICENSE`).
    
2. به **Settings → Pages** بروید، Branch را `main` و Root را `/` انتخاب کنید.
    
3. آدرس عمومی شما می‌شود: `https://<user>.github.io/<repo>/` (به‌صورت خودکار `index.html` باز می‌شود).
    

### گزینهٔ B) **آفلاین بدون سرور (دو‑بارکلیک فایل)**

- کافی‌ست `index.html` را با مرورگر باز کنید. صفحه کار می‌کند (ذخیرهٔ محلی و محاسبات).
    
- نکته: به‌دلیل سیاست‌های امنیتی مرورگر، ممکن است **`rubrics.json` بارگذاری نشود**؛ در این حالت صفحه از **الگوهای داخلی** استفاده می‌کند. اگر می‌خواهید `rubrics.json` هم بارگذاری شود، از گزینهٔ C یا D استفاده کنید.
    

### گزینهٔ C) **آفلاین با سرور محلی ساده** (پیشنهادی)

> مزیت: بارگذاری مطمئنِ `rubrics.json` و سازگاری کامل با Fetch/CORS

- **Python 3**
    
    ```bash
    cd <مسیر-ریپو>
    python -m http.server 5500
    # سپس: http://localhost:5500
    ```
    
- **Node.js — http-server**
    
    ```bash
    cd <مسیر-ریپو>
    npx http-server -p 5500 --cors
    # سپس: http://localhost:5500
    ```
    
- **VS Code — افزونهٔ Live Server**
    
    1. افزونهٔ _Live Server_ را نصب کنید. 2) روی `index.html` راست‌کلیک → **Open with Live Server**.
        

### گزینهٔ D) **آفلاین با XAMPP (Apache محلی)**

> مناسب وقتی می‌خواهید `index.html` و `rubrics.json` را از یک مبدأ (same-origin) سرو کنید تا بارگذاری JSON بدون خطا انجام شود.

**۱) نصب و اجرا**

- **Windows:** XAMPP را نصب کنید → **XAMPP Control Panel** → فقط **Apache** را **Start** کنید.
    
- **macOS:** `/Applications/XAMPP/` → **manager-osx.app** → **Apache** → **Start**.
    
- **Linux:** `/opt/lampp/` → `sudo /opt/lampp/lampp start`
    

**۲) کپی فایل‌ها در ریشهٔ وب (htdocs)**

- Windows: `C:\xampp\htdocs\td22\`
    
- macOS: `/Applications/XAMPP/htdocs/td22/`
    
- Linux: `/opt/lampp/htdocs/td22/`  
    فایل‌های لازم: `index.html`، `rubrics.json`، `README.md`، `LICENSE`
    

**۳) باز کردن صفحه**

- پورت 80: `http://localhost/td22/`
    
- پورت سفارشی (مثلاً 8080): `http://localhost:8080/td22/`
    

**۴) نکات پرتکرار**

- 403 (macOS/Linux): دسترسی پوشه را باز کنید:  
    `sudo chmod -R a+rX /Applications/XAMPP/htdocs/td22`
    
- پورت 80 اشغال است (Windows): در **XAMPP → Apache → Config → httpd.conf** مقدار `Listen 80` را به `Listen 8080` و `ServerName localhost:80` را به `ServerName localhost:8080` تغییر دهید (سرویس را Stop/Start کنید).
    
- `rubrics.json` لود نمی‌شود؟ فایل باید کنار `index.html` باشد. صفحه از `fetch('rubrics.json',{cache:'no-store'})` استفاده می‌کند؛ یک‌بار **Hard Reload** کنید یا نسخه‌دهی کنید: `rubrics.json?v=2025-08-13`.
    

## استفادهٔ روز مسابقه

1. از منوی بالا **Skill** و **Module/Day** را انتخاب کنید؛ شناسهٔ تیم و نام داور را وارد کنید.
    
2. **Judgement**: برای هر «بُعد»، نمرهٔ ۰–۳ بدهید؛ وزن هر ردیف قابل ویرایش است (جمع ۱۰۰).
    
3. **Measurement**: برای هر شاخص، «حداکثر امتیاز» و «کسب‌شده» را وارد کنید (میان‌بر **۰/Full** دارد؛ جمع «حداکثرها» مرجع درصد است).
    
4. وزن‌های نهایی **Judgement/Measurement** (بالا) را تنظیم کنید؛ جمع باید ۱۰۰ باشد.
    
5. ذخیره/بازیابی محلی، **Export JSON/CSV**، **چاپ/‏PDF**، **Reset** یا **بازنشانی به الگوی مهارت**.
    

## Rubrics و سفارشی‌سازی

- `rubrics.json` در شروع به‌طور خودکار خوانده و با الگوی داخلی ادغام می‌شود.
    
- ساختار نمونه:
    

```json
[
  {
    "id": "web",
    "title": "فناوری‌های وب (TD17)",
    "weights": { "judgement": 60, "measurement": 40 },
    "chips": ["USB ممنوع برای شرکت‌کننده", "C‑2: کیبورد/ماوس/هدفون"],
    "judgement": [{ "name": "کیفیت کدنویسی", "weight": 25 }],
    "measurement": [{ "name": "تست‌های پاس‌شده", "weight": 30 }]
  }
]
```

- برای به‌روزرسانی سریع Rubric‌ها، `rubrics.json` را ویرایش یا جایگزین کنید و در صفحه دکمهٔ **Load rubrics.json** را بزنید.
    

## نکات فنی تکمیلی

- **Encoding CSV:** خروجی CSV همراه **BOM‏ UTF‑8** است تا در Excel فارسی را صحیح نشان دهد.
    
- **چاپ:** `print-color-adjust: exact` برای سازگاری چاپ فعال است.
    
- **Tooltip اختیاری:** می‌توانید اسکریپت تولتیپ (در راهنمای گفتگو) را اضافه کنید تا متن کامل معیار/شاخص با Hover/Focus دیده شود.
    
- **حریم‌خصوصی:** داده‌ها فقط در مرورگر (LocalStorage) ذخیره می‌شوند؛ برای آرشیو، از Export استفاده کنید.
    

## مجوز

- کُد تحت **MIT License** است (`LICENSE`).
    
- © 2025 — **تقدیمی از فنی و حرفه‌ای خوزستان – ایذه – آموزشگاه هوش مصنوعی**
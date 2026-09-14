# نَفَس وقهوة — قائمة تفاعلية / Nafas Qahwa — Interactive Menu

قائمة تفاعلية ثنائية اللغة (عربي/إنجليزي) لمقهى **نَفَس وقهوة** — سوق بهلاء، عُمان.

A bilingual (Arabic / English) interactive menu for **Nafas Qahwa** — Bahla Souq, Oman.

## المحتويات / Contents

| File | Description |
| --- | --- |
| `index.html` | الصفحة الكاملة — تطبيق React مُجمّع بالكامل داخل ملف واحد (الخطوط والصور مُضمّنة كـ base64 ويتم فكّها وقت التشغيل). A fully self-contained React app; fonts and images are embedded as base64 and unpacked at runtime. |
| `assets/logo-white.png` | الشعار بالأبيض — يظهر في شاشة التحميل. White logo used by the loading splash. |
| `assets/favicon.png` | أيقونة الموقع. Site favicon. |
| `assets/og.png` | بطاقة المعاينة عند مشاركة الرابط (واتساب، تويتر، فيسبوك). Link preview card for social/messaging shares. |
| `vercel.json` | إعدادات النشر على Vercel. Vercel deployment settings. |

## المميزات / Features

- ٣٥ صنفاً منسوخة من منيو المقهى المطبوع: مشروبات القهوة (١٨)، المشروبات الساخنة (٦)، المشروبات الباردة (٤)، المأكولات (٧) — 35 items transcribed from the café's printed menu
- تبديل اللغة بين العربية والإنجليزية مع دعم RTL كامل — Arabic/English toggle with full RTL support
- بحث فوري في الأسماء والأقسام — instant search across names and sections
- علامات «ساخن / بارد» كما في المنيو المطبوع — the printed menu's hot/cold marks
- اختيار النكهة للآيس تي والموهيتو — flavour choice for Ice Tea and Mojito
- صفحة طلب واحدة: الكميات والإجمالي — a single order page with quantities and a running total
- لا يُرسل الطلب إلى أي جهة ولا يُخزَّن؛ يعيش في الصفحة فقط — the order is never transmitted or stored
- الأسعار بالريال العُماني — prices in Omani Rial

## التشغيل محلياً / Run locally

```bash
python3 -m http.server 8000
# افتح / open http://localhost:8000
```

> ملاحظة: يجب تقديم الصفحة عبر خادم HTTP وليس فتحها مباشرة من الملف، لأن فكّ الموارد يعتمد على `blob:` URLs.
> Note: serve over HTTP rather than opening the file directly — resource unpacking relies on `blob:` URLs.

## النشر / Deployment

موقع ثابت بالكامل — لا يحتاج خطوة بناء. Fully static; no build step required. Vercel serves the repository root as-is.

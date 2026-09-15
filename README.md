# نَفَس وقهوة — قائمة تفاعلية / Nafas Qahwa — Interactive Menu

قائمة تفاعلية ثنائية اللغة (عربي/إنجليزي) لمقهى **نَفَس وقهوة** — سوق بهلاء، عُمان.

A bilingual (Arabic / English) interactive menu for **Nafas Qahwa** — Bahla Souq, Oman.

## المحتويات / Contents

| File | Description |
| --- | --- |
| `index.html` | الصفحة: العلامة والأنماط وقالب التطبيق ومنطقه — the page: markup, styles, app template and logic |
| `assets/react.js`, `assets/react-dom.js` | React 18 (UMD, production) |
| `assets/dc-runtime.js` | محرّك القالب (مصغَّر) — the template runtime (minified) |
| `assets/f/*.woff2` | ١٩ مقطعاً من IBM Plex Sans Arabic و Archivo؛ المتصفح يجلب ما يلزم فقط — 19 subsets; the browser fetches only what it needs |
| `assets/logo-white.webp` | الشعار — the wordmark |
| `assets/favicon.png`, `assets/og.png` | الأيقونة وبطاقة المشاركة — icon and share card |
| `vercel.json` | التخزين المؤقت وترويسات الأمان — caching and security headers |

## المميزات / Features

- ٣٥ صنفاً منسوخة من منيو المقهى المطبوع: مشروبات القهوة (١٨)، المشروبات الساخنة (٦)، المشروبات الباردة (٤)، المأكولات (٧) — 35 items transcribed from the café's printed menu
- تبديل اللغة بين العربية والإنجليزية مع دعم RTL كامل — Arabic/English toggle with full RTL support
- بحث فوري في الأسماء والأقسام — instant search across names and sections
- تجميع مشروبات القهوة في أربع مجموعات (لاتيه · إسبريسو · تحضير مختص · تركية وعربية) لتقليل عبء الاختيار — the 18 coffees grouped into four, to cut choice overload
- مرشّح «يُقدَّم ساخناً / بارداً» مبني على علامات المنيو المطبوع — a served-hot/cold filter built from the printed menu's own marks
- عدّاد كمية داخل الصف: التعديل بضغطة واحدة بلا مغادرة المكان — an in-row stepper: one tap to adjust, without leaving your place
- علامات «ساخن / بارد» كما في المنيو المطبوع — the printed menu's hot/cold marks
- اختيار النكهة للآيس تي والموهيتو — flavour choice for Ice Tea and Mojito
- صفحة طلب واحدة: الكميات والإجمالي — a single order page with quantities and a running total
- لا يُرسل الطلب إلى أي جهة؛ يُحفظ على جهاز الزبون وحده لأربع ساعات ليصمد أمام تحديث الصفحة — the order is never transmitted; it is kept on the customer's own device for four hours so a reload cannot lose it
- زر الرجوع يغلق النافذة ولا يغادر الصفحة — the back button closes a dialog instead of leaving the page
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

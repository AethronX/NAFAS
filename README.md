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

- تبديل اللغة بين العربية والإنجليزية (مع دعم RTL) — Arabic/English toggle with full RTL support
- بحث فوري في الأصناف — instant search across items
- تصفية حسب الفئة: المختارات، القهوة، باردة، شاي ومشروبات، حلويات ومخبوزات، فطور — category filters
- اقتراح اليوم حسب الوقت (الصباح / بعد الظهر / المساء) — time-based daily suggestions
- بطاقة تفاصيل لكل صنف: الأحجام، الأسعار، الاقترانات، ملاحظات التذوّق — per-item detail sheet with sizes, pricing, pairings and tasting notes
- الأسعار بالريال العُماني — prices in Omani Rial
- صفحة طلب واحدة: تجمع الأصناف والأحجام والعروض مع الكميات والإجمالي — a single order page collecting items, sizes and pairing deals with quantities and a running total
- لا يُرسل الطلب إلى أي جهة ولا يُخزَّن؛ يعيش في الصفحة فقط — the order is never transmitted or stored; it lives in the page only

## ⚠️ يجب تعديله قبل الإطلاق / Must be set before launch

| المكان | القيمة الحالية | |
| --- | --- | --- |
| `href="tel:+96890000000"` في `index.html` | `+96890000000` | رقم المقهى الحقيقي — زر «اتصل بنا» لا يعمل بدونه. The café's real number; the Call button does nothing without it. |

## التشغيل محلياً / Run locally

```bash
python3 -m http.server 8000
# افتح / open http://localhost:8000
```

> ملاحظة: يجب تقديم الصفحة عبر خادم HTTP وليس فتحها مباشرة من الملف، لأن فكّ الموارد يعتمد على `blob:` URLs.
> Note: serve over HTTP rather than opening the file directly — resource unpacking relies on `blob:` URLs.

## النشر / Deployment

موقع ثابت بالكامل — لا يحتاج خطوة بناء. Fully static; no build step required. Vercel serves the repository root as-is.

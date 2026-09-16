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
- اقتراح واحد في صفحة الطلب على مسارين منفصلين: المشروبات الباردة ↔ المأكولات، والقهوة ↔ الحلا — one suggestion on the order page, on two separate tracks: cold drinks ↔ food, and coffee ↔ dessert
- بحث فوري في الأسماء والأقسام — instant search across names and sections
- تجميع مشروبات القهوة في أربع مجموعات (لاتيه · إسبريسو · تحضير مختص · تركية وعربية) لتقليل عبء الاختيار — the 18 coffees grouped into four, to cut choice overload
- عدّاد كمية داخل الصف: التعديل بضغطة واحدة بلا مغادرة المكان — an in-row stepper: one tap to adjust, without leaving your place
- علامات «ساخن / بارد» كما في المنيو المطبوع — the printed menu's hot/cold marks
- اختيار النكهة للآيس تي والموهيتو — flavour choice for Ice Tea and Mojito
- صفحة طلب واحدة: الكميات والإجمالي — a single order page with quantities and a running total
- لا يُرسل الطلب إلى أي جهة؛ يُحفظ على جهاز الزبون وحده لأربع ساعات ليصمد أمام تحديث الصفحة — the order is never transmitted; it is kept on the customer's own device for four hours so a reload cannot lose it
- زر الرجوع يغلق النافذة ولا يغادر الصفحة — the back button closes a dialog instead of leaving the page
- الأسعار بالريال العُماني — prices in Omani Rial

## القياس / Measurement

كل شاشة لها عنوان خاص، فأي أداة تحليلات تَعُدّ الصفحات ترى القمع كاملاً بلا أحداث مخصّصة:
Every view has its own address, so any page-view analytics sees the whole funnel without custom events:

| العنوان | الشاشة |
| --- | --- |
| `/` · `#/all` | كل المنيو — full menu |
| `#/coffee` `#/hot` `#/cold` `#/food` | قسم — a section |
| `#/search/<كلمة>` | بحث — a search, including the ones that return nothing |
| `#/order` | صفحة الطلب — the order page |
| `#/choose/<id>` | اختيار النكهة — the flavour chooser |

`#/search/...` هو أثمن ما يُقاس: ما يبحث عنه الزبائن ولا تبيعونه.
`#/search/...` is the most valuable signal here: what customers look for and you do not sell.

**لتفعيل التحليلات:** من لوحة Vercel فعّل Web Analytics وSpeed Insights (مجاناً)، ثم أضف قبل `</body>`:
**To switch analytics on:** enable Web Analytics and Speed Insights in the Vercel dashboard (free), then add before `</body>`:

```html
<script defer src="/_vercel/insights/script.js"></script>
<script defer src="/_vercel/speed-insights/script.js"></script>
```

كلاهما من نفس النطاق، فلا يحتاجان استثناءً في الـ CSP ولا يضعان كوكيز.
Both are first-party, so they need no CSP exception and set no cookies.

> ⚠️ لا تُضفهما قبل التفعيل: الملفان يعطيان 404 فينزل تقييم Best Practices من 100 إلى 96 بلا أي بيانات مقابل ذلك — قِستُه.
> Do not add them before enabling: the files 404 and Best Practices drops from 100 to 96 for no data in return — measured.

## التشغيل محلياً / Run locally

```bash
python3 -m http.server 8000
# افتح / open http://localhost:8000
```

> ملاحظة: قدّم الصفحة عبر خادم HTTP ولا تفتحها من الملف مباشرة، لأن الخطوط والسكربتات تُجلب بمسارات نسبية.
> Note: serve over HTTP rather than opening the file directly — the fonts and scripts are fetched over relative paths.

## النشر / Deployment

موقع ثابت بالكامل — لا يحتاج خطوة بناء. Fully static; no build step required. Vercel serves the repository root as-is.

## الاقتراحات / Pairings

الاقتراح في صفحة الطلب يمشي على مسارين لا يتقاطعان، وكل صنف يسمّي شريكه بنفسه في `index.html`:

The order page's suggestion runs on two tracks that never cross. Every item names its own partner, in `index.html`:

```js
{ id: 'rosella',  with: { savoury: 'beef' } }                      // بارد → أكل
{ id: 'beef',     with: { refresh: 'rosella', coffee: 'cbclassic' } } // أكل → بارد ثم قهوة
{ id: 'esp',      with: { savoury: 'sandegg' } }                   // قهوة → أكل
```

- `refresh` المشروبات الباردة، `warm` المشروبات الساخنة، `coffee` مشروبات القهوة، `savoury` المأكولات المالحة، `sweet` الحلا.
- المسار `coffee ↔ sweet` جاهز في الكود لكنه فارغ: **لا يوجد صنف حلا في المنيو**. أضف صنف حلا بـ `sweet: true`، وأضف `sweet: '<id>'` إلى القهوة التي تناسبه، فيعمل المسار من تلقاء نفسه ويسبق المالح.
- الاقتراح يجب أن يُضاف بضغطة واحدة، لذلك يستبعد الكود تلقائياً كل صنف يسأل عن نكهة أو عن ساخن/بارد أولاً.
- `wants` تقلب ترتيب المسارين لصنف واحد: شطيرتا البيض تطلبان القهوة قبل البارد.

- The `coffee ↔ sweet` track is wired but empty: **the menu has no dessert item**. Add one with `sweet: true` and a `sweet: '<id>'` on the coffees it suits, and the track activates on its own, ahead of the savoury fallback.
- A suggestion must land in one tap, so the code excludes anything that would first ask for a flavour or a temperature.
- `wants` flips the track order for a single item: the two egg sandwiches ask for coffee before a cold drink.

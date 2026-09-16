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

- ٣٣ صنفاً منسوخة من منيو المقهى المطبوع: مشروبات القهوة (١٣)، المشروبات الساخنة (٥)، المشروبات الباردة (٤)، المأكولات (٧)، الحلا (٤) — 33 items transcribed from the café's printed menu
- تبديل اللغة بين العربية والإنجليزية مع دعم RTL كامل — Arabic/English toggle with full RTL support
- رفّ اقتراح في صفحة الطلب يعرض القسم المكمّل كاملاً على مسارين منفصلين: المشروبات الباردة ↔ المأكولات، والقهوة ↔ الحلا — a shelf on the order page offering the whole complementary section, on two separate tracks: cold drinks ↔ food, and coffee ↔ sweets
- بحث فوري في الأسماء والأقسام — instant search across names and sections
- تجميع مشروبات القهوة في أربع مجموعات (بنكهات · إسبريسو · تحضير مختص · عربية) لتقليل عبء الاختيار — the 13 coffees grouped into four, to cut choice overload
- عدّاد كمية داخل الصف: التعديل بضغطة واحدة بلا مغادرة المكان — an in-row stepper: one tap to adjust, without leaving your place
- علامات «ساخن / بارد» كما في المنيو المطبوع — the printed menu's hot/cold marks
- اختيار النكهة للآيس تي والموهيتو — flavour choice for Ice Tea and Mojito
- صفحة طلب واحدة: الكميات والإجمالي — a single order page with quantities and a running total
- لا يُرسل الطلب إلى أي جهة؛ يُحفظ على جهاز الزبون وحده لأربع ساعات ليصمد أمام تحديث الصفحة — the order is never transmitted; it is kept on the customer's own device for four hours so a reload cannot lose it
- تبديل اللغة متاح داخل صفحة الطلب أيضاً، لا في المنيو وحده — the language switch is on the order page too, not only on the menu
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
{ id: 'rosella', with: { savoury: 'beef' } }                          // بارد → أكل
{ id: 'beef',    with: { refresh: 'rosella', coffee: 'cbclassic' } }  // أكل → بارد ثم قهوة
{ id: 'esp',     with: { sweet: 'tiramisu' } }                        // قهوة → حلا
{ id: 'baklava', with: { coffee: 'arabic' } }                         // حلا → قهوة
```

`with` يسمّي الصنف الذي يتصدّر الرفّ، والرفّ يعرض قسمه كاملاً.
`with` names the item that leads the shelf; the shelf shows that item's whole section.

- الأطراف: `refresh` المشروبات الباردة، `warm` المشروبات الساخنة، `coffee` مشروبات القهوة، `savoury` المأكولات، `sweet` الحلا. كل صنف يأخذ طرفه من `cat`، و`CAT_OF` يحوّل الطرف إلى قسم كامل من المنيو.
- **الرفّ يعرض القسم كاملاً**، لا صنفاً واحداً. أول صنف في السلة هو الذي يحدّد القسم، فلا يتبدّل الرفّ تحت إصبعك وأنت تضيف منه.
- `with` لم يعد يختار الاقتراح وإنما يحدّد **الصنف الذي يتصدّر الرفّ**: اسبريسو يضع التيراميسو أولاً، والقهوة العربية تضع البقلاوة أولاً.
- `WANTS` يحدّد ترتيب ما يطلبه كل طرف. القهوة والساخن يطلبان `sweet` ثم `savoury`، فلو حُذف الحلا يوماً عاد المسار البديل وحده.
- `wants` تقلب الترتيب لصنف واحد: شطيرتا البيض تطلبان القهوة قبل البارد.
- صفوف الرفّ هي صفوف المنيو نفسها: عدّاد كمية، وزرّا ساخن/بارد لما يُقدَّم بالوجهين، ونافذة النكهة للآيس تي والموهيتو — تفتح فوق صفحة الطلب على المسار `#/order/choose/<id>` ويعيدها زر الرجوع إلى الطلب لا إلى المنيو.

- The shelf offers the **whole section**, not one item. The basket's first item picks it, so it never changes section under your finger as you add from it.
- `with` no longer picks the suggestion; it picks **which item leads the shelf** — espresso puts the tiramisu first, Arabic coffee puts the baklava first.
- `WANTS` sets what each side asks for, in order. Coffee and hot drinks ask for `sweet` then `savoury`, so removing the sweets restores the fallback on its own.
- `wants` flips the order for a single item: the two egg sandwiches ask for coffee before a cold drink.
- Shelf rows are the menu's own rows — stepper, hot/cold buttons, and the flavour sheet, which opens above the order page at `#/order/choose/<id>` and whose back button returns to the order, not the menu.

## صفحة الطلب / The order page

- **كل شيء قابل للوصول.** الترويسة ثابتة فوق، وزرّا «أضف المزيد» و«تفريغ الطلب» ثابتان تحت، وما بينهما يمرّر — الطلب والإجمالي والرفّ. جُرِّب على ارتفاع ٥٦٨ و٦٦٧ و٨٤٤ بكسل، وبالمنيو كاملاً في السلة (٤٥ سطراً، ١٠٢ زر).
- **صنفان بالاسم نفسه يقولان أيهما.** «ماتشا لاتيه» موجودة ساخنة وباردة، فالسطر يحمل «ساخن» أو «بارد» ولا يترك الزبون يظن أنه كرّر الصنف.
- **حدّ الكمية ٩٩.** ضغطة خاطئة متكرّرة لا تضع أربعة آلاف قهوة على الكاونتر.
- **ما يُقرأ من الجهاز يُفحص مقابل المنيو.** سطر الطلب مفتاحه `p:<id>:<temp>:<flavour>`، ويُقرأ عبر `readKey()`: الصنف لا بدّ أن يكون ما زال في المنيو، ودرجة الحرارة لا تُقبل إلا لما يُقدَّم بالوجهين، والنكهة لا تُقبل إلا لما يعرض نكهات، والكمية عدد صحيح موجب. أي شيء آخر يُسقط بدل أن يُعرض أو يُعطّل الصفحة.
- **رابط `#/order` بسلة فارغة** يفتح المنيو، لا صفحة طلب صفرية.

- **Everything is reachable.** The header is pinned above and the two buttons below; the order, the total and the shelf scroll between them. Verified at 568, 667 and 844px tall, and with the whole menu in the basket — 45 lines and 102 controls.
- **Two items with the same name say which they are.** Matcha Latte exists hot and cold, so each line carries Hot or Cold.
- **Quantity is capped at 99.**
- **Anything read back from a device is checked against the menu** by `readKey()` — the item must still be on it, a temperature only where the menu serves both ways, a flavour only where it lists them, and a whole positive quantity. Anything else is dropped rather than shown or allowed to break the page.
- **`#/order` on an empty basket** opens the menu, not a zero order page.

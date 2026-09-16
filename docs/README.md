# دليل المنيو / Menu guide

- `nafas-menu-guide.pdf` — الدليل جاهزاً للطباعة أو الإرسال (١٨ صفحة A4، عربي RTL)
- `guide.html` — مصدر الدليل
- `img/` — لقطات الشاشة داخله

## إعادة توليد الملف / Regenerating

اللقطات والـPDF يُبنيان من التطبيق نفسه، فأي تغيير في المنيو ينعكس عليهما.
Both the screenshots and the PDF are built from the app itself, so a menu
change flows through to them.

```bash
# 1  شغّل الموقع محلياً على المنفذ 8900 / serve the site on port 8900
python3 -m http.server 8900

# 2  حدّث اللقطات ثم اطبع الـPDF / refresh the shots, then print the PDF
#    (the two scripts live outside the repo; see the commit that added this file)
```

> الـPDF مطبوع بمحرك Chromium من `guide.html`، فالتشكيل العربي والخطوط
> هي نفسها التي يراها الزبون في المنيو.
> The PDF is printed from `guide.html` by Chromium, so the Arabic shaping and
> the fonts are the same ones the customer sees in the menu.

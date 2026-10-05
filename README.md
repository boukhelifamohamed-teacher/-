# الكراس اليومي للأستاذ — نسخة GitHub / Android

هذه الحزمة جاهزة لرفعها إلى مستودع GitHub.

## 1) تشغيلها كصفحة ويب
ارفع الملفات إلى GitHub ثم فعّل:
**Settings → Pages → Deploy from a branch → main → / (root)**

يمكن استعمال التطبيق من الهاتف بعد فتح رابط GitHub Pages.

## 2) إنشاء تطبيق Android من GitHub Actions
بعد رفع الملفات:
1. افتح تبويب **Actions**.
2. اختر **Build Android APK**.
3. اضغط **Run workflow** أو ادفع Commit جديد.
4. بعد انتهاء البناء افتح نتيجة التشغيل ثم **Artifacts**.
5. حمّل `kurras-yawmi-debug-apk` ثم ثبّت ملف APK على الهاتف.

هذه النسخة تنشئ APK تجريبيًا (Debug). إذا أردت نشر التطبيق في Google Play، نضيف لاحقًا توقيع Release وملف keystore.

## 3) حفظ PDF داخل التطبيق
تم حذف زر الطباعة.
زر **حفظ PDF**:
- ينشئ ملف PDF من صفحات الكراس.
- إذا كان Web Share متاحًا، يفتح نافذة المشاركة لإرسال/حفظ الملف.
- إذا لم يكن متاحًا، يبدأ تنزيل ملف PDF باسم الأستاذ.
- تظهر رسالة للمستخدم عند الحاجة إلى السماح بالتنزيل.

> ملاحظة: داخل APK يستخدم التطبيق Filesystem + Share الأصليين عند توفرهما. وفي نسخة الويب يستخدم Web Share أو تنزيل المتصفح. إنشاء PDF يستخدم html2canvas وjsPDF من CDN، لذلك يجب توفر الإنترنت عند أول استعمال لميزة PDF.

## بنية المشروع
- `www/index.html` — التطبيق.
- `www/manifest.webmanifest` — إعدادات PWA.
- `www/sw.js` — التخزين المؤقت.
- `www/icons/` — أيقونات التطبيق.
- `.github/workflows/android.yml` — بناء APK تلقائيًا.
- `capacitor.config.json` — إعداد Capacitor.

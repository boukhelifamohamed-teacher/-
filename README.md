# الكراس اليومي للأستاذ — Android / GitHub

هذه النسخة جاهزة لبناء تطبيق Android بواسطة GitHub Actions وCapacitor.

## إصلاح مهم
تم تثبيت إصدارات Capacitor 7 الموجودة فعلياً في npm:
- @capacitor/android 7.6.9
- @capacitor/core 7.6.9
- @capacitor/filesystem 7.1.9
- @capacitor/share 7.0.2
- @capacitor/cli 7.6.9

الخطأ السابق كان بسبب طلب `@capacitor/filesystem@^7.2.0`، وهو إصدار غير موجود.

## PDF
- زر الطباعة أزيل من الواجهة.
- زر **حفظ PDF** ينشئ ملف PDF.
- داخل APK يحاول حفظ الملف في Documents ثم يفتح المشاركة الأصلية إذا كانت متاحة.
- إذا تعذر ذلك، يستخدم Web Share عند توفره، وإلا يبدأ تنزيل الملف من المتصفح.

> في Android الحديث، الوصول إلى التخزين العام تغير بسبب قيود Android 10/11+؛ لذلك المشاركة الأصلية هي المسار الأكثر موثوقية لإرسال/حفظ PDF خارج التطبيق.

## بناء APK من GitHub
1. ارفع محتويات هذا المجلد إلى مستودع GitHub.
2. افتح تبويب **Actions**.
3. اختر **Build Android APK**.
4. اضغط **Run workflow**.
5. بعد نجاح العملية افتح الـworkflow ثم **Artifacts**.
6. حمّل `kurras-yawmi-debug-apk`.

لا ترفع مجلد `android` مسبقاً؛ GitHub Actions ينشئه بواسطة `npx cap add android`.

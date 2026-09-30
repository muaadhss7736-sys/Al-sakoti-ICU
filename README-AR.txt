بناء تطبيق M.ICU الذي يعمل بدون إنترنت (الملف داخل التطبيق نفسه)
================================================================
الفكرة: نستخدم GitHub (مجاني) ليبني ملف APK تلقائيًا من هذه الملفات. لا تحتاج برامج على الكمبيوتر.

1) أنشئ حسابًا مجانيًا على github.com ثم New repository، سمّه m-icu.
2) ارفع الملفات: Add file > Upload files، ثم اسحب كل محتويات هذا المجلد
   (package.json و capacitor.config.json و مجلدي www و icons).
   اضغط Commit changes.
3) أنشئ ملف البناء إن لم يظهر مجلد .github بعد الرفع:
   Add file > Create new file. في خانة الاسم اكتب بالضبط:
   .github/workflows/build.yml
   والصق محتوى الملف build.yml.txt ثم Commit changes.
4) افتح تبويب Actions. إن طلب تفعيل Workflows فاضغط الموافقة.
   اختر "Build APK" ثم Run workflow. انتظر 5 إلى 10 دقائق حتى تظهر علامة ✓ خضراء.
5) افتح العملية المنتهية، وفي الأسفل قسم Artifacts نزّل M-ICU-apk، ثم فك ضغطه لتجد app-debug.apk.
6) احذف أي نسخة قديمة من التطبيق (WebIntoApp أو PWABuilder) من هاتفك، ثم ثبّت app-debug.apk.
7) اختبر: فعّل وضع الطيران وافتح التطبيق. يجب أن يعمل بالكامل.

ملاحظات:
- هذا APK تجريبي (debug) مناسب للتثبيت المباشر، وليس للنشر على Google Play.
- لتحديث التطبيق: استبدل www/index.html في المستودع ثم شغّل Build APK من جديد وثبّت النسخة الجديدة.


### 📄 Lecture 5 Lab: S3 Static Website + CloudFront

**الهدف (Objective):**
استضافة موقع ويب ثابت على S3 وتسريع توصيله وحمايته باستخدام شبكة CloudFront.

**الأدوات المستخدمة:**

* Amazon S3
* Amazon CloudFront

**البيانات المطلوبة (ملف `index.html`):**
قم بإنشاء ملف نصي على جهازك باسم `index.html` وضع فيه أي جملة، مثال: `<h1>Hello from CloudFront Edge Location!</h1>`.

**الخطوات العملية (Step-by-Step):**

1. **إنشاء S3 Bucket ورفع الملف:**
* افتح خدمة **S3** واضغط **Create bucket**.
* اكتب اسماً فريداً جداً (مثال: `my-static-site-bucket-2026`).
* اترك باقي الإعدادات الافتراضية (Block all public access يجب أن تظل مفعلة) واضغط Create.
* ادخل للـ Bucket واضغط **Upload** وارفع ملف `index.html`.


2. **إنشاء CloudFront Distribution:**
* افتح خدمة **CloudFront** واضغط **Create Distribution**.
* في خانة **Origin domain**، اختر الـ S3 Bucket الذي أنشأته.
* في قسم **Origin access**، اختر **Origin access control settings (recommended)**.
* اضغط **Create control setting** واقبل الإعدادات الافتراضية.
* في خانة **Default root object** بالأسفل، اكتب `index.html`.
* اضغط **Create distribution**.


3. **تحديث صلاحيات الـ S3 (Bucket Policy):**
* بعد إنشاء الـ Distribution، سيظهر لك شريط أصفر يطلب تحديث الـ S3 Policy. اضغط على **Copy policy**.
* ارجع لـ S3، افتح الـ Bucket، اذهب لتاب **Permissions**، الصق الـ Policy في مربع الـ **Bucket policy** واحفظ التغييرات.
* اختبر الموقع باستخدام رابط הـ Distribution domain name من CloudFront.


### 📄 Lecture 14 Lab: 2 Tier E-Commerce Deployment & Stress Testing

**الهدف (Objective):**
نشر تطبيق تجارة إلكترونية، ووضعه خلف موازن أحمال (ALB) ومجموعة توسع تلقائي (ASG). ثم اختبار النظام تحت الضغط (Stress Test) لمشاهدة كيف يقوم AWS بإضافة خوادم جديدة تلقائياً لحماية الموقع من السقوط!

**الأدوات المستخدمة:**

* EC2 Launch Templates.
* Application Load Balancer (ALB).
* Auto Scaling Group (ASG).
* أداة اختبار الضغط `wrk` (أو `Apache Bench`).

---

**الخطوات العملية (Step-by-Step):**

**الخطوة 1: تجهيز قالب التطبيق (The Blueprint) **

* اذهب إلى **EC2** > **Launch Templates** واضغط `Create launch template`.
* الاسم: `ECommerce-Template`.
* نظام التشغيل: `Ubuntu`.
* إعدادات الأمان (Security Group)

* اضغط **Create launch template**.

**الخطوة 2: إنشاء موازن الأحمال (The Traffic Cop) **

* اذهب إلى **Target Groups** وأنشئ مجموعة جديدة للبورت `80`، وسمها `ECommerce-TG` (لا تضف أي سيرفرات يدوياً، الـ ASG سيفعل ذلك).
* اذهب إلى **Load Balancers** وأنشئ **Application Load Balancer**.
* الاسم: `ECommerce-ALB`، اجعله `Internet-facing`.
* في الشبكات: اختر الـ Default VPC وحدد جميع الـ Availability Zones.
* وجّه الترافيك (Listeners) إلى הـ `ECommerce-TG`.
* اضغط **Create**.

**الخطوة 3: تفعيل التوسع التلقائي (The Magic) **

* اذهب إلى **Auto Scaling Groups** واضغط `Create`.
* الاسم: `ECommerce-ASG`، واختر الـ `ECommerce-Template` الذي أنشأته.
* الشبكات: اختر الـ Default VPC وكل الـ Subnets.
* الربط بموازن الأحمال: فعّل خيار `Attach to an existing load balancer` واختر הـ `ECommerce-TG`.
* السعة (Capacity):
* Desired: `1`
* Min: `1`
* Max: `4`


* سياسة التوسع (Scaling Policy): اختر `Target tracking scaling policy`.
* المقياس: `Average CPU utilization`.
* النسبة المستهدفة (Target value): **`20`** *(سنضعها 20% بدلاً من 50% لكي نضمن أن التوسع سيحدث بسرعة أثناء الاختبار في المحاضرة).*


* اضغط **Create**.

**الخطوة 4: لحظة الاحتفال والضغط (The Climax!) **

* انتظر دقائق قليلة، ثم انسخ رابط الـ **DNS name** الخاص بالـ Load Balancer وافتحه في المتصفح للتأكد أن موقعك يعمل.
* **الآن وقت المتعة!** افتح הـ Terminal في جهازك (أو استخدم AWS CloudShell من المتصفح).
* قم بتثبيت أداة `wrk` (إذا كنت تستخدم Ubuntu/CloudShell: `sudo apt install wrk`).
* اضرب الموقع بآلاف الطلبات باستخدام هذا الأمر (استبدل الرابط برابط הـ ALB الخاص بك):

```bash
wrk -t12 -c400 -d3m http://<YOUR_ALB_DNS_NAME>/

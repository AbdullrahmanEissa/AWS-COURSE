
### 📄 Lecture 3 Lab: EC2 Deep Dive & Automation

**الهدف (Objective):**
إطلاق سيرفر Linux، تكوين إعدادات الأمان (Security Group)، واستخدام الـ User Data لتثبيت خادم ويب (Nginx) أوتوماتيكياً.

**الأدوات المستخدمة:**

* EC2 (Elastic Compute Cloud)
* Security Groups
* Bash Scripting

**البيانات المطلوبة (User Data Script):**

```bash
#!/bin/bash
apt update -y
apt install nginx -y
systemctl start nginx
systemctl enable nginx
echo "<h1>Welcome to AWS EC2 - Engineered by [Your Name]</h1>" > /var/www/html/index.html

```

**الخطوات العملية (Step-by-Step):**

1. **إطلاق الخادم (Launch Instance):**
* افتح خدمة **EC2** واضغط **Launch instance**.
* سمّ السيرفر `My-First-Web-Server`.
* اختر نظام التشغيل **Ubuntu**، وحجم السيرفر `t2.micro` (Free Tier).
* في قسم الـ Key pair، اضغط **Create new key pair**، سمّه `web-key` وحمله على جهازك.


2. **إعداد جدار الحماية (Security Group):**
* في قسم Network settings، تأكد من تفعيل:
* **Allow SSH traffic from** (Anywhere أو My IP).
* **Allow HTTP traffic from the internet**.




3. **إضافة الـ User Data:**
* انزل لأسفل الصفحة وافتح **Advanced details**.
* في مربع الـ **User data**، قم بلصق سكريبت الـ Bash المذكور أعلاه.
* اضغط **Launch instance**.


4. **التحقق من العمل:**
* انتظر حتى تصبح حالة السيرفر `Running`.
* انسخ الـ **Public IPv4 address** والصقه في متصفحك لتتأكد من ظهور صفحة الويب.


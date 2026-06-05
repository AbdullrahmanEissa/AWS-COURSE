
### 📄 Lecture 2 Lab: IAM & Security Best Practices

**الهدف (Objective):**
تطبيق مبدأ الصلاحيات الأقل (Least Privilege) عن طريق إنشاء مجموعات، مستخدمين، وسياسات، والابتعاد عن استخدام الـ Root Account.

**الأدوات المستخدمة:**

* AWS IAM (Identity and Access Management)

**الخطوات العملية (Step-by-Step):**

1. **إنشاء مجموعة (IAM Group):**
* افتح خدمة **IAM**، ومن القائمة الجانبية اختر **User groups**.
* اضغط **Create group**، وسمّها `Developers-Team`.
* في قسم إرفاق السياسات (Attach policies)، ابحث عن `AmazonEC2FullAccess` وحددها.
* اضغط **Create group**.


2. **إنشاء مستخدم (IAM User):**
* من القائمة الجانبية اختر **Users** ثم **Add users**.
* اكتب اسم المستخدم `Dev-Ali`.
* فعّل خيار **Provide user access to the AWS Management Console** واختر إنشاء كلمة مرور.
* في الخطوة التالية، اختر **Add user to group** وحدد المجموعة `Developers-Team`.
* أكمل الخطوات واضغط **Create user**. (تأكد من نسخ رابط الدخول الخاص بالمستخدمين وكلمة المرور).


3. **إنشاء دور مؤقت (IAM Role):**
* من القائمة اختر **Roles** ثم **Create role**.
* اختر **AWS service**، وتحتها اختر **EC2**.
* في صفحة السياسات، ابحث عن `AmazonS3ReadOnlyAccess` وحددها.
* سمّ الدور `EC2-Read-S3-Role` واضغط **Create role**.


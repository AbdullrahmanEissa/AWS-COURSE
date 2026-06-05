### 📄 Lecture 6 Lab: Deploy & Connect RDS

**الهدف (Objective):**
بناء قاعدة بيانات MySQL داخل شبكة خاصة (Private Subnet) والاتصال بها بأمان عن طريق خادم EC2 موجود في الشبكة العامة (Public Subnet).

**الأدوات المستخدمة:**

* Amazon RDS
* EC2 (كـ Jump Host / Bastion)
* VPC & Security Groups

**الخطوات العملية (Step-by-Step):**

1. **إنشاء DB Subnet Group:**
* افتح خدمة **RDS**، ومن القائمة الجانبية اختر **Subnet groups**.
* اضغط **Create DB subnet group**.
* اختر הـ `My-Prod-VPC` (من اللاب الرابع).
* اختر הـ Availability Zones والـ Private Subnets فقط، ثم احفظ.


2. **إطلاق قاعدة البيانات (RDS Instance):**
* اذهب إلى **Databases** واضغط **Create database**.
* اختر **MySQL** وفعّل خيار **Free tier**.
* في الـ Credentials، ضع كلمة مرور قوية لقاعدة البيانات (مثال: `admin12345`).
* في قسم Connectivity، تأكد من اختيار الـ VPC الخاص بك، واجعل الـ Public access: **No**.
* في قسم الـ Security Group، اختر Create new (سمّها `RDS-Private-SG`).
* اضغط **Create database** (ستستغرق حوالي 5-10 دقائق للعمل).


3. **تأمين الاتصال عبر Security Group:**
* اذهب لخدمة EC2 > **Security Groups**.
* حدد الـ `RDS-Private-SG` واضغط **Edit inbound rules**.
* احذف القاعدة الافتراضية، وأضف قاعدة جديدة: Type `MySQL/Aurora` (Port 3306)، وفي خانة المصدر (Source)، ابحث عن الـ Security Group الخاصة بسيرفر الـ EC2 وحددها.


4. **الاتصال بقاعدة البيانات:**
* ادخل على سيرفر הـ EC2 عبر SSH.
* ثبّت عميل MySQL بكتابة الأمر: `sudo apt install mysql-client -y`.
* اتصل بالـ RDS بكتابة: `mysql -h <RDS_ENDPOINT_URL> -u admin -p`.
* (احصل على الـ Endpoint URL من تفاصيل قاعدة البيانات في RDS Console).

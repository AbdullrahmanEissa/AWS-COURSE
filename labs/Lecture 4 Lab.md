
### 📄 Lecture 4 Lab: Custom VPC Build

**الهدف (Objective):**
بناء شبكة افتراضية كاملة ومعزولة من الصفر، تحتوي على شبكات فرعية عامة وخاصة، وجداول توجيه.

**الأدوات المستخدمة:**

* VPC, Subnets, Internet Gateway (IGW), Route Tables

**الخطوات العملية (Step-by-Step):**

1. **إنشاء الـ VPC:**
* افتح خدمة **VPC** واضغط **Create VPC**.
* اختر **VPC only**.
* الاسم: `My-Prod-VPC`، والـ IPv4 CIDR block: `10.0.0.0/16`. اضغط Create.


2. **إنشاء الـ Subnets:**
* اذهب إلى **Subnets** واضغط **Create subnet**.
* اختر الـ VPC الذي أنشأته للتو.
* **Subnet 1 (Public):** الاسم `Public-Subnet-1`، الـ CIDR: `10.0.1.0/24`.
* **Subnet 2 (Private):** الاسم `Private-Subnet-1`، الـ CIDR: `10.0.2.0/24`.
* اضغط Create. (ثم حدد الـ Public Subnet، ومن Actions اختر `Edit subnet settings` وفعّل `Enable auto-assign public IPv4 address`).


3. **إنشاء وربط بوابة الإنترنت (IGW):**
* اذهب إلى **Internet gateways** واضغط **Create internet gateway** (سمّه `My-IGW`).
* بعد الإنشاء، من Actions اختر **Attach to VPC** واربطه بـ `My-Prod-VPC`.


4. **تكوين جداول التوجيه (Route Tables):**
* اذهب إلى **Route tables** واضغط **Create route table** (سمّه `Public-RT` واربطه بالـ VPC الخاص بك).
* حدد الـ `Public-RT`، ومن الأسفل اختر تاب **Routes** ثم **Edit routes**.
* أضف مساراً جديداً: الوجهة `0.0.0.0/0` والـ Target هو الـ **Internet Gateway** (`My-IGW`).
* انتقل لتاب **Subnet associations** واضغط **Edit subnet associations**، ثم حدد الـ `Public-Subnet-1` فقط.


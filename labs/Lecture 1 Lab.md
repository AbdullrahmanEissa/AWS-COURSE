### 📄 Lecture 1 Lab: AWS Account & Cost Management

**الهدف (Objective):**
إنشاء حساب AWS مجاني وتأمين البطاقة الائتمانية عن طريق إعداد تنبيهات التكلفة (Billing Alarms) لتجنب أي فواتير مفاجئة.

**الأدوات المستخدمة:**

* AWS Billing Dashboard
* AWS Budgets

**الخطوات العملية (Step-by-Step):**

1. **إنشاء الحساب:**
* الدخول إلى موقع `aws.amazon.com` والضغط على **Create an AWS Account**.
* إدخال البريد الإلكتروني، وتأكيد الهوية، وإدخال بيانات البطاقة البنكية (سيتم خصم 1 دولار واسترداده للتأكيد).
* اختيار خطة الدعم المجانية (Basic Support - Free).


2. **إعداد تنبيه التكلفة (Budget):**
* من شريط البحث العلوي في AWS Console، ابحث عن **AWS Budgets** واضغط عليها.
* اضغط على **Create budget**.
* اختر **Zero spend budget** (للمبتدئين) أو **Customized budget**.
* في حال اختيار Customized، حدد النوع **Cost budget**.
* حدد المبلغ (مثلاً: `$1.00`).a
* في قسم الإشعارات (Alerts)، أضف بريدك الإلكتروني لتصلك رسالة فور تجاوز التكلفة لهذا المبلغ.
* راجع الإعدادات واضغط **Create budget**.



---

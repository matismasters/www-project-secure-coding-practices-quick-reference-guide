---

layout: col-document
title: شیوه‌های کدنویسی امن
tags: SCP-QRG
document: راهنمای شیوه‌های کدنویسی امن

---

{% include breadcrumb.html %}
# مقدمه

این سند به صورت بی‌طرف در تکنولوژی‌ها، مجموعه‌ای از روش‌های
کدنویسی امن را در قالب یک چک‌لیست جمع‌آوری کرده که می‌تواند با
چرخه توسعه نرم‌افزار اقدام شود. پیاده‌سازی این موارد بسیاری از 
آسیب‌پذیری‌های متداول نرم‌افزار را کاهش می‌دهد.

به صورت کلی، تولید یک محصول امن بسیار به‌صرفه‌تر است نسبت به اینکه
محصول به صورت ناامن ایجاد و سپس اصلاحات امنیتی در آن اعمال شود.
مشخص است در صورت رخداد حادثه امنیتی نیز هزینه‌ها چندین برابر خواهد بود.

ایمن‌سازی منابع نرم‌افزاری بیش از پیش حائز اهمیت است چراکه تمرکز نفوذگران
بیشتر در لایه‌ی برنامه‌های کاربردی است. در سال ۲۰۰۹ مطالعه‌ای از
SANS 
نشان داد بیش از ۶۰ درصد حملات مشاهده شده در اینترنت در لایه‌ی برنامه‌کاربردی هستند.

هنگام استفاده از این راهنما، تیم‌های توسعه باید با ارزیابی 
بلوغ چرخه توسعه نرم‌افزار امن و سطح دانش توسعه‌دهندگان شروع کنند.
از آنجایی که این راهنما جزئیات نحوه اجرای هر روش کدنویسی را پوشش نمی دهد، 
توسعه دهندگان باید دانش قبلی یا منابع کافی در دسترس داشته باشند 
که راهنمایی های لازم را ارائه دهد.
این راهنما شیوه‌های کدنویسی را ارائه می‌کند که توسعه‌دهندگان
می‌توانند بدون نیاز به درک عمیق از آسیب‌پذیری‌ها و 
سوءاستفاده‌های امنیتی، به نیازمندی‌های کدنویسی ترجمه شوند.
با این حال، سایر اعضای تیم توسعه باید مسئولیت، آموزش کافی، ابزار و منابع 
را برای تایید ایمن بودن طراحی و پیاده‌سازی کل سیستم داشته باشند.

یک واژه‌نامه از اصطلاحات مهم در این سند در 
پیوست B 
ارائه شده است.

راهنمایی در مورد پیاده‌سازی یک چارچوب توسعه‌ی امن نرم‌افزار خارج از دامنه‌ی 
این مقاله است، با این حال روش‌ها و منابع عمومی زیر توصیه می‌شوند:


-   تعریف نقش‌ها و مسئولیت‌ها به طور واضح

-   ارائه آموزش‌های کافی در زمینه‌ی امنیت نرم‌افزار به تیم‌های توسعه

-   پیاده‌سازی چرخه‌ی توسعه‌ی امن نرم‌افزار

-   تعیین استانداردهای کدنویسی امن

    -   [OWASP Development Guide (انگلیسی)][guide] پروژه

-   ساخت یک کتابخانه‌ی اشیاء قابل استفاده مجدد

    -   [OWASP Enterprise Security API (انگلیسی)][esapi] (ESAPI) پروژه

-   بررسی اثربخشی کنترل‌های امنیتی

    -   [OWASP Application Security Verification Standard (انگلیسی)][asvs] (ASVS) پروژه

-   ایجاد قواعد برون‌سپاری توسعه به صورت ایمن از جمله تعریف 
    الزامات امنیتی و روش‌های تأیید پروپوزال و قرارداد.

**درباره این نسخه**

این نسخه، ترجمه‌ای از نسخه اصلی راهنمای 

مترجم:

* اشکان رفیعی


[asvs]: https://owasp.org/www-project-application-security-verification-standard/
[esapi]: https://owasp.org/www-project-enterprise-security-api/
[guide]: https://owasp.org/www-project-developer-guide/

\newpage

---

layout: col-document
title: شیوه‌های کدنویسی امن
tags: SCP-QRG
document: راهنمای شیوه‌های کدنویسی امن

---

{% include breadcrumb.html %}
# ضمیمه الف: بررسی اجمالی اصول امنیت نرم‌افزار و ریسک

ساخت نرم‌افزار امن نیازمند درک ابتدایی از اصول امنیتی است.
بررسی جامع اصول امنیتی فراتر از حوزه این راهنما است، 
اما یک بررسی اجمالی ارائه شده است.

هدف از امنیت نرم‌افزار، حفظ محرمانگی، یکپارچگی، و در دسترس بودن
منابع اطلاعاتی به منظور راه‌اندازی عملیات تجاری موفق است.
دستیابی به این هدف از طریق پیاده‌سازی کنترل‌های امنیتی صورت می‌گیرد.
این راهنما بر کنترل‌های فنی پیرو کاهش رخداد آسیب‌پذیری‌های رایج نرم‌افزاری متمرکز است.
در حالی که تمرکز اصلی بر برنامه‌های وب و زیرساخت آنها است، 
اغلب این راهنمایی‌ها می‌تواند در هر پلتفرم نرم‌افزاری اعمال شود.

درک معنی ریسک، برای محافظت از کسب‌وکار در برابر
خطرات غیرقابل قبول ناشی از وابستگی به نرم‌افزار، مفید است.
ریسک ترکیبی از عواملی است که موفقیت کسب‌وکار را تهدید می‌کند. 
شرح این موضوع به صورت مفهومی به این گونه است که:
یک عامل تهدید با یک سیستم در ارتباط است که ممکن است دارای آسیب‌پذیری باشد
و می‌تواند به منظور تأثیرگذاری، مورد سوء استفاده قرار گیرد.
برای درک بهتر موضوع مثال زیر را در نظر بگیرید:
یک دزد اتومبیل (عامل تهدید) از میان پارکینگ‌ها عبور کرده
و اتومبیل‌ها (سیستم) را برای درهای قفل نشده (آسیب‌پذیری) بررسی می‌کند
و زمانی که یکی را پیدا می‌کند، در را باز می‌کند (استفاده سوء)
و هر آنچه در داخل است را می‌برد (تأثیر).
تمام این عوامل نقشی در توسعه نرم‌افزار امن ایفا می‌کنند.

رویکرد تعامل و نگاه نفوذگر اساسا با تیم توسعه متفاوت است.
شیوه نگاه یک تیم توسعه نسبت به برنامه‌کاربردی اصولا به شکلی است
که برنامه‌کاربردی برای آن تعبیه شده. به عبارت دیگر آن‌ها برنامه را
بر اساس نیازمندی‌های عملیاتی تعریف شده طراحی کرده و توسعه می‌دهند.
این در حالیست که نفوذگر بیشتر به آنچه یک برنامه قادر است انجام دهد
علاقه‌مند است و معتقد است هر عملی که به طور خاص منع نشده باشد، مجاز است.
برای حل این مسئله، برخی عناصر اضافی باید در مراحل ابتدایی چرخه
عمر نرم‌افزار یا مراحل توسعه‌ی آن ادغاک شوند. این عناصر جدید الزامات امنیتی و
موارد سوء استفاده هستند. این راهنما در راستای کمک در شناسایی الزامات امنیتی
سطح بالا و مقابله با بسیاری از سناریو‌های متداول سوء استفاده طراحی شده است.

تیم‌های توسعه می‌بایست آگاه باشند که کنترل‌های سمت کاربر نظیر 
اعتبارسنجی سمت کاربر، مخفی‌سازی فیلد‌ها و محدودیت‌های رابط‌کاربری نظیر دکمه‌ها و...
ارزش امنیتی چندانی را ارائه نمی‌دهند. نفوذگر قادر است از ابزارهای پروکسی وب نظیر
برپ‌سوییت یا ابزارهایی نظیر وایرشارک برای تحلیل ترافیک برنامه و ارسال درخواست‌های
دستکاری شده و ساخته شده به صورت سفارشی استفاده کند و از رابط‌کاربری
به صورت کامل عبور کند. علاوه بر این، اپلت‌های جاوا، فلش و سایر اشیاء سمت کاربر
قابل بازبینی و بازگردانی هستند و نقاط ضعف آن‌ها برای نفوذگر قابل تجزیه و تحلیل هست.



نقاط ضعف امنیتی نرم‌افزار می‌تواند در هر مرحله‌ای از چرخه‌ی عمر توسعه نرم‌افزار
نمایان شود، از جمله:

-   عدم شناسایی نیازمندی‌های امنیتی در مراحل ابتدایی

-   ایجاد طرح‌های مفهومی که دارای خطاهای منطقی هستند

-   استفاده از روش‌های کدنویسی ناکارآمد که منجر به آسیب‌پذیری‌های فنی می‌شود

-   پیاده‌سازی نرم‌افزار به شکل نادرست

-   ایجاد حفره‌های امنیتی در زمان نگهداشت یا به‌روزرسانی

علاوه بر این، لازم به ذکر است که آسیب‌پذیری‌های نرم‌افزار ممکن است دامنه‌ای
فراتر از خود نرم‌افزار داشته باشند. بسته به ماهیت نرم‌افزار، آسیب‌پذیری و
زیرساخت پشتیبان، اثرات بهره‌برداری موفق می‌تواند شامل مسائل زیر باشد:

- نرم‌افزار و اطلاعات مرتبط با آن

- سیستم‌عامل سرور‌های مربوطه

- پایگاه‌داده

- سایر برنامه‌هایی که در محیط مشترک پیاده‌سازی شده است

- سیستم کاربر

- سایر نرم‌افزار‌هایی که کاربر با آن‌ها تعامل دارد

\newpage

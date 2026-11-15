# خلاصه مفاهیم Secrets و Conditional Deployment

## ۱. GitHub Secrets

از GitHub Secrets برای نگهداری اطلاعات محرمانه مانند API Token و رمزهای عبور استفاده می‌شود.

در این پروژه یک Secret با نام `MY_API_TOKEN` ایجاد می‌کنیم.

برای دسترسی به مقدار آن از دستور زیر استفاده می‌کنیم:

`secrets.MY_API_TOKEN`

برای حفظ امنیت، مقدار واقعی Secret را در خروجی Workflow نمایش نمی‌دهیم و فقط طول آن را بررسی می‌کنیم.

## ۲. Build Job

در این مرحله یک فایل به نام `version.txt` ساخته می‌شود.

این فایل شامل شناسه Commit فعلی Git است.

سپس پوشه `dist` به‌عنوان یک Artifact ذخیره می‌شود تا Jobهای بعدی بتوانند از آن استفاده کنند.

## ۳. Staging Deployment

محیط Staging برای آزمایش نسخه برنامه قبل از انتشار نهایی استفاده می‌شود.

در این پروژه، Job مربوط به Staging در شاخه `develop` یا از طریق اجرای دستی Workflow فعال می‌شود.

## ۴. Production Deployment

محیط Production محیط اصلی اجرای برنامه است.

در این پروژه، Job مربوط به Production فقط هنگام اجرای Workflow روی شاخه `main` اجرا می‌شود.

## ۵. GitHub Environments

از Environment برای مدیریت محیط‌های مختلف مانند Staging و Production استفاده می‌شود.

همچنین می‌توان برای محیط Production تأیید دستی قبل از Deploy را فعال کرد.

## نتیجه‌گیری

در این تمرین با نحوه نگهداری اطلاعات محرمانه در GitHub، استفاده از Secrets، ساخت Artifact و مدیریت اجرای شرطی مراحل Deploy آشنا شدیم.

# اشتباهات رایج GitHub Actions

## 1. Workflow در تب Actions دیده نمی‌شود

علت: فایل Workflow در مسیر `.github/workflows/` قرار نگرفته یا فایل به GitHub Push نشده است.

راه‌حل: مسیر فایل را بررسی کرده و Workflow را Commit و Push کنید.

## 2. YAML invalid

علت: مشکل در indentation یا syntax فایل YAML.

راه‌حل: indentation را با Space اصلاح کرده و syntax فایل را بررسی کنید.

## 3. به فایل‌های Repository دسترسی نیست

علت: مرحله `actions/checkout` قبل از دسترسی به فایل‌های Repository اجرا نشده است.

راه‌حل: از `actions/checkout@v4` قبل از مراحل مربوط به فایل‌های Repository استفاده کنید.

## 4. Secret خالی است

علت: Secret در Repository تعریف نشده یا نام Secret در Workflow اشتباه نوشته شده است.

راه‌حل: Secret موردنظر را در Settings → Secrets and variables → Actions ایجاد کرده و نام آن را دقیقاً مطابق Workflow قرار دهید.

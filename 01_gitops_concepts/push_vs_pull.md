# Push vs Pull در GitOps

## 1. Push-based CD

در مدل Push، سیستم CI پس از Build و Test مستقیماً به Cluster یا محیط مقصد متصل می‌شود و تغییرات را Deploy می‌کند.

```text
Developer
    |
    v
   Git
    |
    v
   CI
    |
    | Push
    v
Kubernetes Cluster
```

## 2. Pull-based GitOps

در مدل Pull، تغییرات در Git قرار می‌گیرند و یک Agent یا Controller داخل محیط مقصد Git را بررسی می‌کند و وضعیت موردنظر را دریافت و اعمال می‌کند.

```text
Developer
    |
    v
   Git
    ^
    |
    | Pull
    |
GitOps Agent
    |
    v
Kubernetes Cluster
```

## 3. مزایا و ریسک‌های Push

### مزایا

1. ساختار ساده و قابل فهم است.
2. می‌توان CI را مستقیماً بعد از Build و Test برای Deploy تنظیم کرد.

### ریسک‌ها

1. CI باید دسترسی مستقیم به Cluster داشته باشد.
2. Credentialهای مربوط به Cluster باید در CI نگهداری شوند و در صورت مدیریت نادرست می‌توانند ریسک امنیتی ایجاد کنند.

## 4. مزایا و ریسک‌های Pull

### مزایا

1. نیازی نیست CI مستقیماً به Cluster دسترسی داشته باشد.
2. وضعیت مطلوب محیط در Git ثبت می‌شود و تغییرات قابل بررسی و Audit هستند.

### ریسک‌ها

1. نیاز به یک Agent یا Controller مانند Argo CD یا Flux وجود دارد.
2. اگر Agent یا ارتباط آن با Git دچار مشکل شود، Synchronization ممکن است انجام نشود.

## 5. نقش CI در GitOps

CI معمولاً مسئول Build، Test و ساخت Artifact یا Docker Image است.

برای مثال:

```text
Developer
   |
   v
Git
   |
   v
CI
   |
   +----> Test
   |
   +----> Build Docker Image
   |
   v
Container Registry
   |
   v
Update Deployment Manifest
   |
   v
Git
   |
   v
GitOps Controller
   |
   v
Kubernetes
```

در این مدل CI معمولاً Image جدید را می‌سازد و در Registry قرار می‌دهد. سپس Manifest مربوط به نسخه جدید را به‌روزرسانی می‌کند. GitOps Controller تغییر Manifest را از Git دریافت کرده و آن را روی Cluster اعمال می‌کند.

CI در اینجا نقش Build و تغییر Artifact/Manifest را دارد؛ Controller وظیفه هماهنگ‌سازی محیط را انجام می‌دهد.

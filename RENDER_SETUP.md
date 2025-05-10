# إعداد المشروع على منصة Render

هذا الملف يحتوي على جميع الملفات الضرورية للنشر على منصة Render مع إصلاح المشكلات الأساسية.

## الإعدادات المطلوبة على Render

### 1. أمر البناء (Build Command)
```
pip install -r render-requirements.txt
```

### 2. أمر البدء (Start Command)
```
gunicorn --bind 0.0.0.0:$PORT --reuse-port --workers 4 --timeout 120 main:app
```

### 3. متغيرات البيئة (Environment Variables)
أضف المتغيرات التالية:

#### متغيرات إلزامية:
- `DATABASE_URL`: رابط الاتصال بقاعدة البيانات PostgreSQL
- `PORT`: 5000
- `FLASK_SECRET_KEY`: قيمة عشوائية آمنة

#### متغيرات اختيارية:
- `TELEGRAM_BOT_TOKEN`: إذا كنت ترغب في استخدام ميزة إشعارات Telegram
- `TELEGRAM_CHAT_ID`: معرف الدردشة التي ستستقبل الإشعارات
- `SENDGRID_API_KEY`: إذا كنت ترغب في استخدام SendGrid لإرسال البريد الإلكتروني

## الإصلاحات المضمنة

1. إضافة ملف templates/base.html المفقود
2. تصحيح تناقض المعلمات في نظام إشعارات Telegram
3. إضافة مكتبة user-agents المفقودة إلى render-requirements.txt
4. تحسين التبديل بين SQLite المحلية وPostgreSQL على الخادم

## ملاحظات هامة

- لدى نشر المشروع للمرة الأولى، سيتم إنشاء قاعدة البيانات تلقائيًا
- يمكنك الوصول إلى لوحة التحكم من خلال زيارة /admin/login
- الملفات التي سترفعها (الصور والفيديوهات) ستكون في مجلدات static/uploads
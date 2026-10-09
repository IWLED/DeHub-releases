<div align="center">

# Delovine · ديلوفين

**مكتبتك من الأفلام والمسلسلات والأنمي في بيتك — تُشاهد على كل أجهزتك**

Your own movies, series and anime at home, on every device.

[**⬇️ تنزيل أحدث إصدار · Download the latest release**](https://github.com/IWLED/Delovine-releases/releases/latest)

</div>

---

Delovine خادم وسائط منزلي يجمع في برنامج واحد: البحث عن المحتوى وتنزيله، وترتيب المكتبة تلقائياً،
والمشاهدة مع ترجمة عربية سليمة على الحاسب والتلفاز والجوال. يعمل على جهاز واحد في بيتك، وتفتحه
باقي الأجهزة من المتصفح — بنفس فكرة Jellyfin.

## أي نسخة أنزّل؟

| أريد… | النسخة | الملف |
|---|---|---|
| تشغيل Delovine على حاسب ويندوز ليستخدمه كل من في البيت | **خادم Delovine لويندوز** ⭐ | `Delovine-Server-<version>-windows-x64-setup.exe` |
| تشغيله على حاسب أو خادم لينكس (أي توزيعة) | **خادم لينكس** | `delovine-server-<version>-linux-x86_64.tar.gz` (أو `aarch64` لـ Raspberry Pi وARM) |
| تشغيله على NAS أو خادم فيه Docker | **Docker** | `ghcr.io/iwled/delovine` |
| برنامج كامل في نافذة على حاسبي (مع أفضل تشغيل للفيديو محلياً) | **تطبيق سطح المكتب** | `Delovine-Desktop-<version>-…` (ويندوز، AppImage، deb، rpm) |
| المشاهدة من الجوال | **تطبيق أندرويد** | `Delovine-<version>-android.apk` |

> **الخادم** يعمل في الخلفية وتستخدمه من **المتصفح** على أي جهاز.
> **تطبيق سطح المكتب** يحوي الخادم نفسه، ويمكن مشاركته مع أجهزة الشبكة من الإعدادات ← الشبكة.

## التثبيت

### 🖥️ ويندوز — خادم Delovine

1. نزّل `Delovine-Server-<version>-windows-x64-setup.exe` وشغّله.
2. يعمل الخادم فوراً مع أيقونة بجوار الساعة، ويفتح Delovine في المتصفح لتكمل الإعداد.
3. من أي جهاز في نفس الشبكة افتح ‎`http://<عنوان الحاسب>:3000` (يظهر العنوان في الإعدادات ← الشبكة).

من الأيقونة بجوار الساعة: فتح Delovine، إعادة تشغيل الخادم، إيقافه أو تشغيله، التشغيل مع بدء ويندوز، وفتح السجلات.
ffmpeg مضمَّن فلا تحتاج تثبيت أي شيء آخر.

### 🐧 لينكس — أي توزيعة

```bash
curl -fsSL https://github.com/IWLED/Delovine-releases/releases/latest/download/delovine-server-linux-x86_64.tar.gz | tar -xz
cd delovine-server && sudo ./install.sh
```

يثبّت Delovine كخدمة تعمل مع بدء التشغيل (systemd) ويثبّت ffmpeg إن لم يكن موجوداً. لـ ARM64 (Raspberry Pi 4/5)
استبدل `x86_64` بـ `aarch64`. خيارات: `./install.sh --help` (مثل `--user` لتشغيله بحسابك و`--port`).

دون تثبيت: `./delovine-server` ثم افتح `http://localhost:3000`.

### 🐳 Docker

```yaml
services:
  delovine:
    image: ghcr.io/iwled/delovine:latest
    container_name: delovine
    restart: unless-stopped
    ports:
      - "3000:3000"
    volumes:
      - delovine-data:/data
      - /path/to/media:/media
    shm_size: "512mb"
volumes:
  delovine-data:
```

```bash
docker compose up -d
```

### 💻 تطبيق سطح المكتب

ويندوز: `Delovine-Desktop-<version>-windows-x64-setup.exe` · لينكس: AppImage أو deb أو rpm.
يعمل كاملاً في نافذته، ويبقى في علبة النظام عند الإغلاق، ويمكن تشغيله مع بدء النظام من الإعدادات.

### 📱 أندرويد

ثبّت `Delovine-<version>-android.apk` (اسمح بالتثبيت من المتصفح عند الطلب) ثم أدخل عنوان الخادم.

## التحديثات

- **الخادم وتطبيق سطح المكتب:** يُعلمك Delovine عند صدور إصدار جديد. من **الإعدادات ← التحديثات ← التحديث الآن** يُنزَّل التحديث ويُتحقَّق من توقيعه ويُثبَّت ثم يعود الخادم خلال دقيقة، ويصل التحديث لكل الأجهزة التي تستخدمه.
- **Docker:** `docker compose pull && docker compose up -d`
- **أندرويد:** يعرض التطبيق التحديث الجديد ويفتح تنزيله.
- القناة **التجريبية** (من نفس الصفحة) تصلها الميزات أولاً.

## أسئلة شائعة

- **الأجهزة الأخرى لا تصل إلى Delovine؟** تأكد أنها على نفس الشبكة، وأن جدار الحماية يسمح بالمنفذ 3000، وأن المشاركة مفعّلة في الإعدادات ← الشبكة.
- **أين تُحفظ بياناتي؟** ويندوز: `%USERPROFILE%\Delovine` · لينكس (الخدمة): `/var/lib/delovine` · Docker: المجلد `/data`. ملفات الوسائط نفسها تبقى في مجلداتك.
- **التحقق من الملفات:** بصمات كل الملفات في `SHA256SUMS` مع كل إصدار.
- **الوصول من خارج البيت:** لا تفتح المنفذ في الراوتر؛ استخدم VPN منزلياً مثل Tailscale أو WireGuard.

---

## English

Delovine is a self-hosted media server: find and download content, organise the library, and watch with
proper subtitles on every device at home. Run it on one machine; everything else uses a browser.

| I want to… | Download |
|---|---|
| Run it on a Windows PC for the whole home | **Delovine Server for Windows** (`…-Server-…-setup.exe`): tray icon, starts with Windows, updates itself |
| Run it on Linux (any distribution, x86_64 / ARM64) | `delovine-server-…-linux-*.tar.gz`, then `sudo ./install.sh` (systemd service) |
| Run it on a NAS / Docker host | `ghcr.io/iwled/delovine:latest` |
| A full desktop app in its own window | **Delovine Desktop** (Windows installer, AppImage, deb, rpm) |
| Watch on Android | `Delovine-…-android.apk` |

Open `http://<server address>:3000` from any device on your network. Updates: **Settings → Updates → Update now**
(Docker: `docker compose pull && docker compose up -d`). Every release lists its files' checksums in `SHA256SUMS`.

# 🚀 File Downloader - Poo poo

· Download any file from anywhere directly into your GitHub repository
· Supports large files by splitting them into 90MB chunks (due to GitHub's limitations)

---

🔧 Installation Guide

1. Click the Fork button at the top of this repository
2. Change the fork name if needed, then click Create Fork
3. Your repository is ready! You can now download any file with a direct link into your repo, then download it to your system

---

🎯 How to Download Files to Your Repository

1. Prepare your direct link (e.g., example.com/files/something.zip)
2. Go to your GitHub and click on your forked repository, then select the Actions tab
3. In the Actions tab, you'll see a workflow named "Poo poo - Download from URLs & Save to Repo". Click on it, then click Run Workflow, enter your download link, and the download will begin...

---

📂 Where to Find Downloaded Files

All downloaded files are added to the downloads/ folder in your repository.

Files are split into 90MB chunks. For example:

· If your file is 300MB, you'll get 4 files
· Download all 4 files to your system
· Extract them using 7zip (Windows) or on Linux:

```bash
7z x file.zip
```

This will extract all split parts (file.zip, file.z01, file.z02, etc.) into a single folder.

---

⚙️ Available Settings

Setting Description Options
urls Space-separated list of URLs Any direct or YouTube link
mode Output mode normal (individual files) or zip (single archive)
split_threshold_mb Split files larger than this (0 = never split) Default: 90
youtube_format YouTube quality best, bestvideo+bestaudio, bestaudio, worst
output_name Custom filename pattern Use {date}, {id}, {title}
convert_format Convert to format keep, mp4, mkv, webm, mp3, m4a, wav, opus
batch_mode Batch processing sequential (one by one) or parallel (faster)
parallel_jobs Number of parallel downloads (1-5) Default: 3

---

🎬 Example Usage

Download a single YouTube video as MP3:

```
urls: https://youtube.com/watch?v=dQw4w9WgXcQ
youtube_format: bestaudio
convert_format: mp3
output_name: {date}_{title}
```

Download multiple files in parallel:

```
urls: https://example.com/file1.zip https://example.com/file2.mp4 https://youtube.com/watch?v=abc123
batch_mode: parallel
parallel_jobs: 3
```

Download, split, and zip:

```
urls: https://example.com/largefile.iso
mode: zip
split_threshold_mb: 90
```

---

📝 Output Name Placeholders

Placeholder What it becomes Example
{date} Date & time (YYYYMMDD_HHMMSS) 20250115_143022
{id} YouTube video ID dQw4w9WgXcQ
{title} Video title (sanitized) Rick_Astley_-_Never_Gonna_Give

Default pattern: {date}_{id}.ext

---

🧹 Cleaning Downloads

To delete all files in the downloads/ folder, use the "Poo poo - Clean Downloads Folder" workflow:

1. Go to Actions tab
2. Select "Poo poo - Clean Downloads Folder"
3. Type DELETE to confirm
4. Optionally choose to remove from git history (⚠️ permanent)

---

⚠️ Important Notes

· File splitting: Files larger than 90MB are automatically split for GitHub compatibility
· Reassembly: Use 7zip to merge split files back together
· Direct links only: For non-YouTube files, use direct download links
· YouTube: Supported with yt-dlp + Cloudflare WARP bypass
· Free tier limits: GitHub Actions has 6 hours/month on Ubuntu runners

---

🐛 Troubleshooting

Downloaded file shows as {title}.webm literally?

· Make sure you're using the latest workflow version
· The output_name should use placeholders like {date}_{id} not raw text

YouTube videos fail to download?

· The workflow includes Cloudflare WARP for IP bypass
· Try changing youtube_format to bestaudio or worst
· Some age-restricted videos may fail

Parallel downloads not working?

· Reduce parallel_jobs to 2 or 3
· Switch to sequential mode for problematic URLs

---

📞 Support

· Original project: AVASAM
· Forked version: Poo poo downloader

---

🚀 دانلود کننده فایل - Poo poo

· دانلود هر فایلی از هر کجا مستقیماً درون ریپازیتوری گیتهاب شما
· پشتیبانی از فایل‌های بزرگ با تقسیم به تکه‌های ۹۰ مگابایتی (به دلیل محدودیت گیتهاب)

---

🔧 آموزش نصب

۱. روی دکمه Fork در بالای این ریپازیتوری کلیک کنید
۲. در صورت نیاز نام فورک را تغییر دهید، سپس روی Create Fork کلیک کنید
۳. ریپازیتوری شما آماده است! حالا می‌توانید هر فایلی را با لینک مستقیم درون ریپازیتوری دانلود کنید

---

🎯 نحوه دانلود فایل درون ریپازیتوری

۱. لینک مستقیم خود را آماده کنید (مثل example.com/files/something.zip)
۲. به گیتهاب خود بروید و روی ریپازیتوری فورک شده کلیک کنید، سپس قسمت Actions را انتخاب کنید
۳. در بخش Actions، وورکفلو "Poo poo - Download from URLs & Save to Repo" را می‌بینید. روی آن کلیک کنید، سپس روی Run Workflow بزنید، لینک دانلود را وارد کنید و دانلود شروع می‌شود...

---

📂 فایل‌ها را از کجا دانلود کنیم

همه فایل‌های دانلود شده در پوشه downloads/ درون ریپازیتوری شما اضافه می‌شوند.

فایل‌ها به تکه‌های ۹۰ مگابایتی تقسیم می‌شوند. مثال:

· اگر فایل شما ۳۰۰ مگابایت باشد، ۴ فایل دریافت می‌کنید
· هر ۴ فایل را دانلود کنید
· با استفاده از 7zip اکسترکت کنید

```bash
7z x file.zip
```

این کار همه قسمت‌های تقسیم شده (file.zip، file.z01، file.z02 و ...) را در یک پوشه اکسترکت می‌کند.

---

⚙️ تنظیمات موجود

تنظیمات توضیحات گزینه‌ها
urls لیستی از لینک‌ها با فاصله از هم هر لینک مستقیم یا یوتیوب
mode حالت خروجی normal (فایل‌های تکی) یا zip (آرشیو یکتا)
split_threshold_mb تقسیم فایل‌های بزرگتر از این مقدار (۰ = هرگز تقسیم نشود) پیش‌فرض: 90
youtube_format کیفیت یوتیوب best، bestvideo+bestaudio، bestaudio، worst
output_name الگوی نام فایل خروجی استفاده از {date}، {id}، {title}
convert_format تبدیل به فرمت keep، mp4، mkv، webm، mp3، m4a، wav، opus
batch_mode پردازش دسته‌ای sequential (یکی یکی) یا parallel (همزمان)
parallel_jobs تعداد دانلود همزمان (۱-۵) پیش‌فرض: 3

---

🎬 مثال‌های استفاده

دانلود یک ویدیوی یوتیوب به صورت MP3:

```
urls: https://youtube.com/watch?v=dQw4w9WgXcQ
youtube_format: bestaudio
convert_format: mp3
output_name: {date}_{title}
```

دانلود چند فایل به صورت همزمان:

```
urls: https://example.com/file1.zip https://example.com/file2.mp4 https://youtube.com/watch?v=abc123
batch_mode: parallel
parallel_jobs: 3
```

دانلود، تقسیم و زیپ کردن:

```
urls: https://example.com/largefile.iso
mode: zip
split_threshold_mb: 90
```

---

📝 جایگزین‌های الگوی نام خروجی

جایگزین تبدیل به مثال
{date} تاریخ و ساعت (YYYYMMDD_HHMMSS) 20250115_143022
{id} آیدی ویدیوی یوتیوب dQw4w9WgXcQ
{title} عنوان ویدیو (پاکسازی شده) Rick_Astley_-_Never_Gonna_Give

الگوی پیش‌فرض: {date}_{id}.ext

---

🧹 پاک کردن دانلودها

برای حذف همه فایل‌های پوشه downloads/ از وورکفلو "Poo poo - Clean Downloads Folder" استفاده کنید:
۱. به بخش Actions بروید
۲. "Poo poo - Clean Downloads Folder" را انتخاب کنید
۳. کلمه DELETE را تایپ کنید
۴. در صورت تمایل گزینه حذف از تاریخچه گیت را انتخاب کنید (⚠️ دائمی)

---

⚠️ نکات مهم

· تقسیم فایل: فایل‌های بزرگتر از ۹۰ مگابایت به صورت خودکار برای سازگاری با گیتهاب تقسیم می‌شوند
· ادغام مجدد: برای ادغام فایل‌های تقسیم شده از 7zip استفاده کنید
· فقط لینک مستقیم: برای فایل‌های غیر یوتیوب، از لینک‌های مستقیم استفاده کنید
· یوتیوب: پشتیبانی با yt-dlp + Cloudflare WARP
· محدودیت رایگان: گیتهاب اکشن ۶ ساعت در ماه روی Ubuntu runners دارد

---

🐛 رفع اشکال

فایل دانلود شده به صورت {title}.webm نمایش داده می‌شود؟

· مطمئن شوید از آخرین نسخه وورکفلو استفاده می‌کنید
· output_name باید از جایگزین‌هایی مثل {date}_{id} استفاده کند نه متن ساده

دانلود ویدیوهای یوتیوب ناموفق است؟

· وورکفلو شامل Cloudflare WARP برای دور زدن IP است
· سعی کنید youtube_format را به bestaudio یا worst تغییر دهید
· برخی ویدیوهای دارای محدودیت سنی ممکن است ناموفق باشند

دانلود همزمان کار نمی‌کند؟

· parallel_jobs را به ۲ یا ۳ کاهش دهید
· برای لینک‌های مشکل‌دار به حالت sequential تغییر دهید

---

📞 پشتیبانی

· پروژه اصلی: AVASAM
· نسخه فورک شده: دانلود کننده Poo poo

---

💝 لایسنس

Free & Open Source - Happy Coding!

---

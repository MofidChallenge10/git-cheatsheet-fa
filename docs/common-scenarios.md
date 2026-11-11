# سناریوهای رایج

راه‌حل مشکلاتی که تقریباً همه یک‌بار باهاشون برخورد می‌کنن.

## روی شاخه‌ی اشتباه کامیت کردم

فرض کن روی `main` کامیت کردی ولی باید روی یک شاخه‌ی جدید می‌بود:

```bash
git branch feature/new-work      # شاخه‌ی جدید از وضعیت فعلی (کامیت‌ها همراهش هستن)
git reset --hard origin/main     # main رو به وضعیت ریموت برگردون
git switch feature/new-work
```

> `reset --hard` فقط وقتی امنه که کامیت‌های اشتباه رو با دستور اول روی شاخه‌ی جدید نگه داشته باشی و تغییرات commit نشده‌ای نداشته باشی.

## می‌خوام چند کامیت رو یکی کنم

```bash
git rebase -i HEAD~3
```

در ویرایشگر، برای کامیت‌هایی که می‌خوای داخل کامیت قبلی ادغام بشن به‌جای `pick` بنویس `squash` (یا `s`). ذخیره کن و پیام نهایی رو ویرایش کن.

## یک فایل بزرگ یا رمز عبور رو اشتباهی commit کردم

اگر هنوز push نکردی، کامیت رو با `git reset --soft HEAD~1` برگردون، فایل رو از stage دربیار و دوباره commit کن.

اگر push کردی و فایل شامل رمز، توکن یا کلید بود، **اول همون رمز رو باطل (revoke) و عوض کن**. حذف از تاریخچه کافی نیست چون ممکنه قبلاً کپی شده باشه. بعد برای پاک کردن از تاریخچه از ابزار `git filter-repo` استفاده کن.

## فقط یک کامیت مشخص از شاخه‌ی دیگر رو می‌خوام

```bash
git switch main
git cherry-pick <commit-hash>
```

## ریموت جلوتر از لوکال هست و push رد می‌شه

```bash
git pull --rebase
git push
```

اگر تداخل پیش اومد، حلش کن و `git rebase --continue` بزن.

## شاخه‌ام رو با main به‌روز کنم

```bash
git fetch origin
git rebase origin/main      # یا: git merge origin/main
```

## می‌خوام فقط یک فایل رو از شاخه‌ی دیگر بگیرم

```bash
git restore --source=other-branch path/to/file.txt
```

## کامیت‌های یک شاخه‌ی محلی که روی ریموت نیست رو ببینم

```bash
git log origin/main..HEAD --oneline
```

## اسم یک شاخه رو عوض کنم

```bash
git branch -m old-name new-name
git push origin -u new-name
git push origin --delete old-name
```

## فایل‌های مشخص رو در یک پوشه نادیده بگیرم، بدون دست زدن به .gitignore مشترک

فایل `.git/info/exclude` مثل `.gitignore` کار می‌کنه ولی فقط روی کامپیوتر خودت اعمال می‌شه و commit نمی‌شه.

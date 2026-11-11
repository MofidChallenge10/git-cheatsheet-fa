# alias های مفید گیت

alias ها دستورات طولانی رو کوتاه می‌کنن. اضافه کردن یک alias:

```bash
git config --global alias.st status
```

بعد از این، `git st` همون `git status` رو اجرا می‌کنه.

## مجموعه‌ی پیشنهادی

می‌تونی این بلاک رو به بخش `[alias]` فایل `~/.gitconfig` اضافه کنی:

```ini
[alias]
    st   = status -sb
    co   = checkout
    sw   = switch
    br   = branch
    ci   = commit
    cm   = commit -m
    ca   = commit --amend --no-edit
    unstage = restore --staged
    last = log -1 --stat
    lg   = log --oneline --graph --decorate --all
    undo = reset --soft HEAD~1
    pf   = push --force-with-lease
```

## توضیح چند مورد

| alias | کار |
|---|---|
| `git st` | وضعیت کوتاه همراه با نام شاخه |
| `git unstage file` | خارج کردن فایل از stage |
| `git last` | آخرین کامیت همراه با فایل‌های تغییریافته |
| `git lg` | گراف تاریخچه‌ی همه‌ی شاخه‌ها |
| `git undo` | برگرداندن آخرین کامیت و نگه داشتن تغییرات در stage |
| `git pf` | force push امن‌تر: اگر کسی دیگر چیزی push کرده باشد، رد می‌شود |

## alias های شل (bash/zsh)

در `~/.bashrc` یا `~/.zshrc`:

```bash
alias gs='git status -sb'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git pull --rebase'
```

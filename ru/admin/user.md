---
lang: ru
lang-ref: user 
layout: home
---

## Добавить пользователя в группу

```bash
./bin/Console.pl Admin::Group::UserLink \
  --user-name "root@localhost" --group-name admin --permission rw
```

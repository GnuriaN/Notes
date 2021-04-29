# GIT: интересные и полезные связки команд

## Вывод логов

Создаём файс с расширением `.cmd`
```cmd
:: Wraper for git log 
@echo off
git log --graph "--date=format:%%m-%%d-%%Y at %%H:%%M" "--pretty=format:%%C(auto)%%h%%d %%C(bold blue)%%an %%Cgreen%%ad  %%Creset%%s" %*
```
и выполняем его, на выходе получаем красивый лог:
```cmd
* 361c335 (HEAD -> master, origin/master) Ruslan Prokhorov 04-29-2021 at 21:44  ADD: task 12 to part 4
* f5e7708 Ruslan Prokhorov 04-29-2021 at 20:48  ADD: task 11 to part 4
* 563656d Ruslan Prokhorov 04-29-2021 at 20:42  ADD: task 10 to part 4
* 659990b Ruslan Prokhorov 04-29-2021 at 20:36  ADD: task 9 to part 4
* 212a9e2 Ruslan Prokhorov 04-29-2021 at 20:25  ADD: task 8 to part 4
* 2d1e112 Ruslan Prokhorov 04-28-2021 at 00:08  FIX: pylint style PEP8
```


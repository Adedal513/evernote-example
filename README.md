# evernote-example
Утилита для работы с сервисом создания и хранения заметок  [Evernote](https://evernote.com/intl/ru/).

Позволяет:
- Создавать короткие заметки
- Получать текст заметок из указанного блокнота
- Выводить список существующих блокнотов

Использует средства [Evernote SDK](https://dev.evernote.com/doc/).

##Установка

---

После скачивания репозитория, установите все зависимости командой `pip` (`pip3` в случае конфликта с Python3):
```shell
pip install -r requirements.txt
```
##Настройка

---
Перед началом работы зарегистрируйтесь на [сайте](https://evernote.com/intl/ru/)  сервиса Evernote и [сервере разработки](https://sandbox.evernote.com/Registration.action?ref=https://githubhelp.com).

Получите на 
Для работы утилите необходимы переменные окружения. Создайте файл `.env` и внесите в него следующие переменные в виде 
`ПЕРЕМЕННАЯ=ЗНАЧЕНИЕ`:
- `EVERNOTE_CONSUMER_KEY` - ключ пользователя
- `EVERNOTE_CONSUMER_SECRET` - секрет пользователя

*Примечание: Можно получить через [OAuth](https://dev.evernote.com/doc/articles/authentication.php?ref=https://githubhelp.com)*

- `EVERNOTE_PERSONAL_TOKEN` - личный токен разработчика. Получить его можно [тут](https://sandbox.evernote.com/api/DeveloperToken.action) 

- `JOURNAL_TEMPLATE_NOTE_GUID` - идентификатор шаблона для заметок
- `JOURNAL_NOTEBOOK_GUID`  - идентификатор ноутбука-журнала для создания заметок
- `INBOX_NOTEBOOK_GUID` - идентификатор ноутбука для просмотра заметок

## Использование

---
### list_notebooks.py
Скрипт выводит список существующих ноутбуков.

```shell
user@user:~$ python list_notebooks.py
```
### add_note2journal.py
Скрипт создает заметку согласно шаблону `JOURNAL_TEMPLATE_NOTE_GUID` и помещает ее в "Дневник" с идентификатором `JOURNAL_NOTEBOOK_GUID`.
В качестве аргументов принимает **дату** заметки.

```shell
user@user:~$ python add_note2journal.py -date 2021-12-12
```

### dump_inbox.py

Вывод заметок, хранящихся в ноутбке с индентификатором `INBOX_NOTEBOOK_GUID`. В качестве аргумента принимает **число заметок** для вывода (по умолчанию равно 10).

```shell
user@user:~$ python dump_inbox.py -number 5
```
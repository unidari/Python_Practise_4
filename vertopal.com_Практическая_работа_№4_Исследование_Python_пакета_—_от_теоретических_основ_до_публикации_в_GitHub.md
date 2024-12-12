
# **Практическая работа №4. Исследование Python-пакета --- от теоретических основ до публикации в GitHub** {#практическая-работа-4-исследование-python-пакета--от-теоретических-основ-до-публикации-в-github}
:::

::: {#4d968065 .cell .markdown id="4d968065"}
## **Цель работы**
:::

::: {#3f23c716 .cell .markdown id="3f23c716"}
**Цель** этой практической работы заключается в изучении принципов
функционирования пакетов в Python и публикации проекта в приватном
репозитории на GitHub.

**Задачи** включают:

1.  Исследование роли файлов `__init__.py` в структуре пакетов.
2.  Освоение работы с модульной структурой Python.
3.  Понимание и применение абсолютного и относительного импорта модулей.
4.  Создание и настройка локального Git-репозитория.
5.  Публикация проекта в приватном репозитории на GitHub с добавлением
    всех необходимых файлов и документации в формате Markdown в
    README.md.
6.  Управление доступом к репозиторию, включая добавление коллаборатора.

Эти задачи помогут вам освоить все этапы работы с Python-пакетами, от их
создания и исследования до управления версиями и совместной работы в
закрытой среде.
:::

::: {#ffb03f5a .cell .markdown id="ffb03f5a"}
## **Описание работы**
:::

::: {#18243b16 .cell .markdown id="18243b16"}
Вы будете работать с уже созданным пакетом `calculator`, который имеет
следующую структуру:

    calculator/
    ├── __init__.py
    ├── basic/
    │   ├── __init__.py
    │   ├── addition.py
    │   └── subtraction.py
    └── advanced/
        ├── __init__.py
        ├── exponentiation.py
        └── root.py
:::

::: {#63967923 .cell .markdown id="\"63967923\""}
**Содержимое файлов:**

**`calculator/__init__.py`**
:::

::: {#dc7ad5d4 .cell .code id="dc7ad5d4"}
``` python
# __init__.py in calculator
__all__ = ["basic", "advanced"]
```
:::

::: {#2ca97ca9 .cell .markdown id="2ca97ca9"}
**`calculator/basic/__init__.py`**
:::

::: {#38c109a0 .cell .code id="38c109a0"}
``` python
# __init__.py in basic
from .addition import add
from .subtraction import subtract
```
:::

::: {#a3ffd41a .cell .markdown id="a3ffd41a"}
**`calculator/basic/addition.py`**
:::

::: {#7ed2e868 .cell .code id="7ed2e868"}
``` python
# addition.py
def add(a, b):
    return a + b
```
:::

::: {#81545127 .cell .markdown id="\"81545127\""}
**`calculator/basic/subtraction.py`**
:::

::: {#67003bfc .cell .code id="67003bfc"}
``` python
# subtraction.py
def subtract(a, b):
    return a - b
```
:::

::: {#a7150f98 .cell .markdown id="a7150f98"}
**`calculator/advanced/__init__.py`**
:::

::: {#7b82ebf9 .cell .code id="7b82ebf9"}
``` python
# __init__.py in advanced
from .exponentiation import power
from .root import square_root
```
:::

::: {#2710fe8b .cell .markdown id="2710fe8b"}
**`calculator/advanced/exponentiation.py`**
:::

::: {#9ba07d5b .cell .code id="9ba07d5b"}
``` python
# exponentiation.py
def power(a, b):
    return a ** b
```
:::

::: {#80d53e6d .cell .markdown id="80d53e6d"}
**`calculator/advanced/root.py`**
:::

::: {#ea8f8d28 .cell .code id="ea8f8d28"}
``` python
# root.py
def square_root(a):
    return a ** 0.5
```
:::

::: {#d3d29b5c .cell .markdown id="d3d29b5c"}
**Пример использования пакета:**
:::

::: {#fb6c3f15 .cell .code id="fb6c3f15"}
``` python
# main.py
from calculator.basic import add, subtract
from calculator.advanced import power, square_root

print(add(2, 3))             # Вывод: 5
print(subtract(5, 2))        # Вывод: 3
print(power(2, 3))           # Вывод: 8
print(square_root(16))       # Вывод: 4.0
```
:::

::: {#bc7b0fc2 .cell .markdown id="bc7b0fc2"}
## **Задания:**
:::

::: {#0d5236e4 .cell .markdown id="0d5236e4"}
### **1. Исследование структуры пакета** {#1-исследование-структуры-пакета}
:::

::: {#682c1a97 .cell .markdown id="682c1a97"}
**а.** Дополните схему дерева файлов и модулей пакета `calculator`,
указав, какие модули и функции в них содержатся.

    calculator/
    ├── __init__.py
    ├── basic/
    │   ├── __init__.py
    │   ├── addition.py
    │   └── subtraction.py
    └── advanced/
        ├── __init__.py
        ├── exponentiation.py
        └── root.py
:::

::: {#e4a-jJ6qVuKz .cell .markdown id="e4a-jJ6qVuKz"}
``` plaintext
calculator/
├── __init__.py
├── basic/
│   ├── __init__.py
│   ├── addition.py
│   │   └── def add
│   └── subtraction.py
│       └── def subtract
└── advanced/
    ├── __init__.py
    ├── exponentiation.py
    │   └── def power
    └── root.py
        └── def square_root
```
:::

::: {#rXUGL_f5UtCQ .cell .markdown id="rXUGL_f5UtCQ"}
**б.** Объясните, какую роль играют файлы `__init__.py` в каждом
каталоге пакета. Почему без них пакет не будет работать правильно?
:::

::: {#WJHC-5qUWDVe .cell .markdown id="WJHC-5qUWDVe"}
`<font color='green'>`{=html}Этот файл является пакетом-проводником, а
не обычной папкой. Без него Python не сможет правильно импортировать
модули из этого каталога. Внутри данного файла можно указывать, какие
модули или функции доступны для импорта. `</font>`{=html}
:::

::: {#29422cc8 .cell .markdown id="29422cc8"}
### **2. Работа с `__init__.py`** {#2-работа-с-__init__py}
:::

::: {#3a1a8ac0 .cell .markdown id="3a1a8ac0"}
**а.** Обратите внимание на использование переменной `__all__` в файле
`calculator/__init__.py`. Объясните, как она влияет на импорт пакета.
:::

::: {#LNfDwADqWRbv .cell .markdown id="LNfDwADqWRbv"}
`<font color='green'>`{=html} Данная переменная в файле **init**
определяет, какие модули будут импортироваться при использовании
конструкции from calculator import \*. В данном случае, **all** =
\[\"basic\", \"advanced\"\] означает, что при импорте пакета calculator
будут доступны только эти два подкаталога (basic и advanced), а все
остальные модули или файлы игнорируются. Если даннная переменная не
указана, то Python импортирует все модули, которые есть в пакете, кроме
тех, что начинаются с подчеркивания (\_).`</font>`{=html}
:::

::: {#y23edpV8U6Zu .cell .markdown id="y23edpV8U6Zu"}
**б.** Удалите или закомментируйте строку
`__all__ = ["basic", "advanced"]` в файле `calculator/__init__.py`.
Попробуйте импортировать пакет снова:
:::

::: {#6c3ce464 .cell .code id="6c3ce464"}
``` python
from calculator import basic
```
:::

::: {#bce87341 .cell .markdown id="bce87341"}
Что произошло? Объясните причину возникшей проблемы.
:::

::: {#KIGZTFcmWTWY .cell .markdown id="KIGZTFcmWTWY"}
`<font color='green'>`{=html} При попытке выполнить импорт возникла
ошибка. Причина заключается в отсутствии списка доступных для импрта
модулей. Python не смог найти каталог basic в пакете calculator. И при
использовании from calculator import basic не имеет доступа к данному
модулю.`</font>`{=html}
:::

::: {#hASF8Jk9WWWf .cell .markdown id="hASF8Jk9WWWf"}
**в.** Верните строку `__all__` обратно. Попробуйте выполнить команду:
:::

::: {#c0812720 .cell .code id="c0812720"}
``` python
from calculator import *
```
:::

::: {#a2fb1056 .cell .markdown id="a2fb1056"}
Какие модули будут импортированы? Как можно управлять импортируемыми
модулями с помощью `__all__`?
:::

::: {#oKXMNpjnWe1v .cell .markdown id="oKXMNpjnWe1v"}
`<font color='green'>`{=html} После того возвращения переменной **all**
будут импортированы только модули basic и advanced. При использовании
from calculator import \*, Python будет импортировать только те модули,
которые перечислены в **all**.`</font>`{=html}
:::

::: {#0ff9be0e .cell .markdown id="0ff9be0e"}
### **3. Абсолютный и относительный импорт** {#3-абсолютный-и-относительный-импорт}
:::

::: {#68879eed .cell .markdown id="68879eed"}
**а.** В файле `calculator/basic/__init__.py` замените относительные
импорты на абсолютные:
:::

::: {#be1a46ca .cell .code id="be1a46ca"}
``` python
from calculator.basic.addition import add
from calculator.basic.subtraction import subtract
```
:::

::: {#85a363ec .cell .markdown id="85a363ec"}
Проверьте работоспособность пакета. Объясните разницу между
относительным и абсолютным импортом. Какие преимущества и недостатки
каждого из них?
:::

::: {#XjE-FQ0xWj0b .cell .markdown id="XjE-FQ0xWj0b"}
`<font color='green'>`{=html} Пакет так же работает. Абсолютный импорт
использует полный путь, а относительный импорт указывает путь
относительно текущего файла с использованием точек. Абсолютный импорт
понятнее, чем относительный, и длиннее, чем относительный.
`</font>`{=html}
:::

::: {#RURDowbzWiVX .cell .markdown id="RURDowbzWiVX"}
**б.** Предположим, что структура пакета изменилась, и папка `basic`
была переименована в `simple`. Объясните, как это повлияет на абсолютные
и относительные импорты. Какой импорт легче поддерживать при
реорганизации структуры пакета?
:::

::: {#giLqxQx7WkBn .cell .markdown id="giLqxQx7WkBn"}
`<font color='green'>`{=html} На абсолютные импорты это сильно повлияет.
Нужно будет поменять все импорты (заменить папку basic на simple).
Относительные импорты могут не изменятся. Например from .root import
square_root останется рабочим. Такой импорт зависит от текущего
местоположения.`</font>`{=html}
:::

::: {#ed448ab3 .cell .markdown id="ed448ab3"}
### **4. Добавление новых модулей** {#4-добавление-новых-модулей}
:::

::: {#AQQQ_pXGWpZS .cell .markdown id="AQQQ_pXGWpZS"}
**а.** Добавьте в пакет `calculator/basic` новый модуль
`multiplication.py` с функцией `multiply(a, b)`, которая возвращает
произведение `a` и `b`.
:::

::: {#M5cPRrG5WszB .cell .markdown id="M5cPRrG5WszB"}
`<font color='green'>`{=html} calculator/ ├── **init**.py ├── basic/ │
├── **init**.py │ ├── addition.py │ └── multiplication.py │ └──
subtraction.py └── advanced/ ├── **init**.py ├── exponentiation.py └──
root.py `</font>`{=html}
:::

::: {#3HrK2DicWq4a .cell .markdown id="3HrK2DicWq4a"}
**б.** Обновите файл `calculator/basic/__init__.py`, чтобы функция
`multiply` была доступна при импорте пакета.
:::

::: {#hwSUaM3EWtFf .cell .markdown id="hwSUaM3EWtFf"}
`<font color='green'>`{=html}from calculator.basic.multiplication import
multiply`</font>`{=html}
:::

::: {#ee203e60 .cell .markdown id="ee203e60"}
**в.** В файле `main.py` импортируйте новую функцию и протестируйте ее.
:::

::: {#68e1c50a .cell .code id="68e1c50a"}
``` python
from calculator.basic import multiply

print(multiply(4, 5))        # Вывод: 20
```
:::

::: {#9XMbvHyuWtgb .cell .markdown id="9XMbvHyuWtgb"}
`<font color='green'>`{=html}20`</font>`{=html}
:::

::: {#e488b22c .cell .markdown id="e488b22c"}
### 5. Исследование переменной `__name__` {#5-исследование-переменной-__name__}
:::

::: {#e8fe04ba .cell .markdown id="e8fe04ba"}
**а.** В файле `calculator/advanced/exponentiation.py` добавьте
следующий код:
:::

::: {#6e63ece4 .cell .code id="6e63ece4"}
``` python
if __name__ == "__main__":
    print(power(2, 5))
```
:::

::: {#68b13f10 .cell .markdown id="68b13f10"}
**б.** Запустите файл `exponentiation.py` напрямую. Что произошло? Какой
вывод вы получили?
:::

::: {#zy-VgC4EXFNP .cell .markdown id="zy-VgC4EXFNP"}
`<font color='green'>`{=html} Приведённый код позволяет определять точку
входа в программу. Вывод - 32 `</font>`{=html}
:::

::: {#FvsI0C7LXEPa .cell .markdown id="FvsI0C7LXEPa"}
**в.** Импортируйте функцию `power` в `main.py` и запустите `main.py`.
Выполняется ли код внутри блока `if __name__ == "__main__":` в файле
`exponentiation.py` при импорте? Объясните, почему.
:::

::: {#8GQE7e7rXFYf .cell .markdown id="8GQE7e7rXFYf"}
`<font color='green'>`{=html} Код в файле exponentiation.py не
выполнился, потому что при импорте функции в файле main.py переменная
**name** принимает значение имени модуля, не как значение основного
файла. Код в блоке if **name** == \"**main**\" выполняется, когда файл
запускается напрямую. `</font>`{=html}
:::

::: {#f3b886cc .cell .markdown id="f3b886cc"}
### **6. Изучение путей поиска модулей** {#6-изучение-путей-поиска-модулей}
:::

::: {#04706edf .cell .markdown id="04706edf"}
**а.** Выведите переменную `sys.path` в `main.py`:
:::

::: {#1759325c .cell .code id="1759325c"}
``` python
import sys
print(sys.path)
```
:::

::: {#9e9babe0 .cell .markdown id="9e9babe0"}
Объясните, какие пути в ней содержатся и как Python использует их для
поиска модулей.
:::

::: {#ZV4qGFfbXJ_a .cell .markdown id="ZV4qGFfbXJ_a"}
`<font color='green'>`{=html} Текущую директорию, из которой был запущен
скрипт. Директории, указанные в переменной окружения PYTHONPATH.
Стандартные директории, в которых установлены системные пакеты Python.
`</font>`{=html}
:::

::: {#j4VNaSL2XIvc .cell .markdown id="j4VNaSL2XIvc"}
**б.** Попробуйте переместить папку `calculator` в другую директорию,
которая не входит в `sys.path`. Можете ли вы теперь импортировать пакет?
Что нужно сделать, чтобы Python мог найти ваш пакет?
:::

::: {#uy8f-RUkXKLe .cell .markdown id="uy8f-RUkXKLe"}
`<font color='green'>`{=html} Нет, пакет импортировать не получилось.
Для того, чтобы всё-таки найти его, можно добавить новый путь в sys.path
прямо в скрипте, установить переменную окружения PYTHONPATH перед
запуском кода. `</font>`{=html}
:::

::: {#3f1e3ccc .cell .markdown id="3f1e3ccc"}
### **7. Создание подпакетов** {#7-создание-подпакетов}
:::

::: {#7a8e87b9 .cell .markdown id="7a8e87b9"}
**а.** Внутри `calculator/advanced` создайте подпакет `trigonometry` с
функциями `sin`, `cos` и `tan`. Структура должна выглядеть так:
:::

::: {#4991737d .cell .code id="4991737d"}
``` python
calculator/
└── advanced/
    ├── trigonometry/
    │   ├── __init__.py
    │   ├── sine.py
    │   ├── cosine.py
    │   └── tangent.py
```
:::

::: {#2982fcf5 .cell .markdown id="2982fcf5"}
**б.** Реализуйте функции в соответствующих модулях, используя модуль
`math` из стандартной библиотеки Python.

**в.** Обновите `__init__.py` файлы, чтобы обеспечить корректный импорт
функций.

**г.** Импортируйте функции в `main.py` и протестируйте их.
:::

::: {#68f95ac3 .cell .markdown id="68f95ac3"}
### **8. Практика с относительным импортом** {#8-практика-с-относительным-импортом}
:::

::: {#b5329b6b .cell .markdown id="b5329b6b"}
**а.** В файле `calculator/advanced/trigonometry/sine.py` попробуйте
импортировать функцию `square_root` из модуля `root.py` двумя способами:

1.  Используя относительный импорт.
2.  Используя абсолютный импорт.

**б.** Объясните, какой способ импорта сработал, а какой нет, и почему.
:::

::: {#f5Q7sNgSXR9A .cell .markdown id="f5Q7sNgSXR9A"}
`<font color='green'>`{=html} Относительный импорт не сработает.
Относительные импорты работают только внутри пакетов. Абсолютный импорт
сработает всегда, так как всегда указывает полное местоположение модуля,
начиная от корня пакета. В данном случае нам необходимо подняться на
пакет выше, поэтому лучше использовать абсолютный путь. `</font>`{=html}
:::

::: {#CWeoSKkUZvkS .cell .markdown id="CWeoSKkUZvkS"}
### **9. Публикация на GitHub** {#9-публикация-на-github}
:::

::: {#VkEZWOGWwiFm .cell .markdown id="VkEZWOGWwiFm"}
После завершения всех заданий добавьте папку с проектом в Ваш локальный
Git-репозиторий. Затем опубликуйте его на GitHub, создав **приватный**
репозиторий.

-   **Вопросы и Ваши ответы на них разместите в файле README.md** Вашего
    приватного репозитория. Используйте стиль [разметки
    Markdown](https://docs.github.com/ru/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).
    Для примеров можно обратиться к следующим ресурсам:
    [Markdown](https://skillbox.ru/media/code/yazyk-razmetki-markdown-shpargalka-po-sintaksisu-s-primerami/)
    и [Readme.md](https://habr.com/ru/articles/649363/).

-   **Далее выполните следующие шаги**:

    1.  Перейдите в настройки вашего репозитория:
        -   Откройте ваш новый приватный репозиторий.
        -   Нажмите на вкладку `Settings` (Настройки) в верхней части
            страницы.
    2.  Добавьте коллаборатора:
        -   В меню слева выберите `Collaborators` (Коллабораторы).
        -   Нажмите `Add people` (Добавить человека).
        -   Введите имя пользователя GitHub: **Alexandre77777**.
        -   Нажмите `Add Alexandre77777 to this repository` (Добавить
            коллаборатора).
    3.  Отправьте приглашение:
        -   Человек, которого вы пригласили, получит уведомление на
            GitHub и по электронной почте.
        -   Он должен будет принять приглашение, чтобы получить доступ к
            вашему репозиторию.
:::

::: {#4cee5f71 .cell .markdown id="4cee5f71"}
## **Ожидаемые результаты**
:::

::: {#31e6a190 .cell .markdown id="31e6a190"}
-   Вы глубоко разберетесь в структуре пакета `calculator` и поймете,
    как организованы модули и функции внутри него.
-   Научитесь использовать и настраивать файлы `__init__.py` для
    управления импортом модулей и функций.
-   Будете уверенно использовать как абсолютный, так и относительный
    импорт, понимая их разницу и области применения.
-   Узнаете, как переменная `__name__` влияет на выполнение кода при
    импорте модулей.
-   Поймете, как Python ищет модули и пакеты, и как управлять путями
    поиска.
-   Сможете расширять пакеты, добавляя новые модули, функции и
    подпакеты.
-   Получите практический опыт работы с пакетами, что упростит
    разработку больших проектов в будущем.
:::

::: {#001a12c1 .cell .markdown id="001a12c1"}
## **Дополнительные задания (для продвинутых, не обязательны к выполнению)**
:::

::: {#e2f9040b .cell .markdown id="e2f9040b"}
-   **1. Создание установочного скрипта**

    Создайте файл `setup.py` для вашего пакета `calculator`, чтобы его
    можно было установить с помощью `pip install .`.

-   **2. Документация пакета**

    Добавьте документацию в ваш пакет, используя файлы `README.md` и
    строки документирования (docstrings) в функциях.
:::

::: {#df3e6334 .cell .markdown id="df3e6334"}
## **Советы по выполнению работы**
:::

::: {#1b19991f .cell .markdown id="1b19991f"}
-   Постепенно выполняйте задания, проверяя работоспособность после
    каждого шага.
-   Обращайтесь к [официальной документации
    Python](https://docs.python.org/3/tutorial/modules.html) по модулям
    и пакетам для дополнительной информации.
:::

<h1 align="center">Private_task</a>
<h3 align="center">Вопрос 1</h3>
<h3 align="center">
```plaintext
calculator/
├── __init__.py
├── basic/
│   ├── __init__.py
│   ├── addition.py
│   │   └── def add(a, b)
│   └── subtraction.py
│       └── def subtract(a, b)
└── advanced/
    ├── __init__.py
    ├── exponentiation.py
    │   └── def power(a, b)
    └── root.py
        └── def square_root(a)
```
</h3>
<h3 align="center">Вопрос 1б</h3>
<h3 align="center">Объясните, какую роль играют файлы __init__.py в каждом каталоге пакета. Почему без них пакет не будет работать правильно?</h3>
<font color='green'>Этот файл является пакетом-проводником, а не обычной папкой. Без него Python не сможет правильно импортировать модули из этого каталога. Внутри данного файла можно указывать, какие модули или функции доступны для импорта.
</font>

Простой калькулятор на Python, предоставляющий базовые и расширенные математические операции.

## Установка

```bash
pip install calculator-pkg-yourusername
```

## Использование

```python
from calculator.basic import add, subtract
from calculator.advanced import power, square_root
from calculator.advanced.trigonometry import sin, cos, tan

print(add(2, 3))             # Вывод: 5
print(subtract(5, 2))        # Вывод: 3
print(power(2, 3))           # Вывод: 8
print(square_root(16))       # Вывод: 4.0
print(sin(90))               # Вывод: 0.8939966636005579
print(cos(90))               # Вывод: -0.4480736161291701
print(tan(45))               # Вывод: 1.6197751905438615
```
## Лицензия

Этот проект лицензирован под лицензией MIT - подробности см. в файле [LICENSE](LICENSE).
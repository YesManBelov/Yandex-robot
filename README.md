# Console-BOT

## Характеристики

Консольный робот имеет 2 версии:
- [Стандартная "robot.py"](robot.py) 
- [Модифицированная "robot_modifier.py"](robot_modifier.py) 



### Алгоритм интерпретатора команд для робота:
- Проверить валидность заданной команды, чтобы не было лишних символов;
- Создать карту координат перемещения робота;
- Если присутствуют отрицательные координаты:
--то сдвинуть значения координат;
- нарисовать карту.

Стартовая точкой входа - вызов функции: 
```sh
execute()
```

В независимости от версии программы, функция принимает команду формата ***string***.
Возвращает так же объект ***string***, в котором хранится нарисованная карта движения робота

### Ввод данных

Правила передачи данных в версиях различны, но в обеих версиях, регистр символов в команде не важен.

В ***стандартной версии*** на вход может подаваться строчка, состоящая
из символов:

```sh
"FLR"
```
где:
* *F* - ход вперед
* *R* - поворот направо
* *L* - поворот налево

**Стандартная версия** программы не будет обрабатывать заданную команду, если встретит невалидный символ.

Изначально робот стоит на координатах (0, 0) и повёрнут вправо

##### Пример:

**Ввод**
```sh
"FFLFFFRFFF"
```
**Вывод**
```sh
  ****
  *   
  *   
***   
```

В ***модифицированной версии*** на вход может подаваться строчка, состоящая
из символов:

```sh
"FLR0123456789!"
```
где:
* *F* - ход вперед
* *R* - поворот направо
* *L* - поворот налево
* *Число* - Колличество действий стоящих после числа
* *!* - Указывает, что ход или ходы будут невидимыми

Так же есть набор правил, которые нужно учитывать при вводе команды, чтобы алгоритм не отказался обрабатывать ваш запрос:
- Нельзя заканчивать команду на цифру
- Нельзя начинать команду с "!"
- Число обязано стоять только перед символами "F", "R", "L"
-"!" обязан стоять только после символа "F"
- Максимальное число - 999

Число может стоять как перед символом **F**, что будет указывать на колличество ходов вперед, так и перед символами **L** и **R**, что будет указывать на колличество поворотов.

"**!**" после символа **F** указывает, что данный ход будет невидимым, а так же возможны комбинации заросов.
Команда -
```sh
"32F!"
```
указывает, что будет сделано 32 невидимых хода

##### Примеры:

**Ввод**
```sh
"1fl02fl3fl4fl5fl6fl7fl8fl9fl10fl11fl"
```
**Вывод**
```sh
************
           *
  ******** *
  *      * *
  * **** * *
  * *  * * *
  * * ** * *
  * *    * *
  * ****** *
  *        *
  ********** 
```

**Ввод**
```sh
"5FL5F!L5FL5F!L"
```
**Вывод**
```sh
***** 
      
      
      
      
 *****
```






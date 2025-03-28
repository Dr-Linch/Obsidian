## Что такое if-elif-else

Условный оператор **if-elif-else** в Python — это способ написать программный код так, чтобы он выдавал результат в зависимости от того, выполняется определенное условие или нет.

Когда есть несколько условий, можно использовать **elif** (сокращение от **else if** — «иначе если»), чтобы проверять их поочередно. Если ни одно из условий не истинно, используют блок **else**, чтобы выполнить код по умолчанию.

Синтаксис выглядит так:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8|`if` `условие_1:`<br><br>    `# блок кода, который выполняется, если условие_1 истинно`<br><br>`elif` `условие_2:`<br><br>    `# блок кода, который выполняется, если условие_2 истинно`<br><br>`elif` `условие_3:`<br><br>    `# блок кода, который выполняется, если условие_3 истинно`<br><br>`else``:`<br><br>    `# блок кода, который выполняется, если ни одно из условий не истинно`|

Условия проверяются по порядку. Если какое-то из них истинно, выполняется соответствующий блок кода, а остальные игнорируются. Если ни одно из условий не истинно, выполняется блок кода в разделе **else**, если он присутствует.

Представим, что программа помогает вам выбрать одежду в зависимости от погоды:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8|`weather` `=` `"солнечно"`<br><br>`if` `weather` `=``=` `"дождливо"``:`<br><br>    `print``(``"Возьми зонтик"``)`<br><br>`elif` `weather` `=``=` `"солнечно"``:`<br><br>    `print``(``"Надень солнцезащитные очки и кепку"``)`<br><br>`else``:`<br><br>    `print``(``"Можешь носить что угодно"``)`|

В этом примере:

🟡 Если погода дождливая, программа выдаст рекомендацию взять зонтик.  
🟡 Если погода солнечная — надеть солнцезащитные очки и кепку.  
🟡 Если нет ни дождя, ни солнца — нет конкретных рекомендаций.

## Условный оператор if

В языке Python выражение считается истинным (true), если его результат — не ноль или выражение не является пустым объектом. Соответственно, оно считается ложным (false), если результат — ноль или пустой объект, в том числе значение none. При использовании операторов сравнения результатом выражения будет true, если условие выполняется, и false — в противном случае.

Инструкцию **if** в Python используют, чтобы выполнить блок кода, если заданное условие истинно.

Схематично конструкцию с if можно записать так:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4|`if` `условное_выражение:`<br><br>    `инструкции`<br><br>    `инструкции`<br><br>    `...`|

🟡 **if** — оператор, который вводит условие;  
🟡 двоеточие после условного выражения сообщает, что дальше будет действие или набор последовательных действий при выполнении условия;  
🟡 инструкции — действие с каждым элементом.

Внутри одного условия можно выполнять несколько сравнений, что расширяет возможности использования условных конструкций. Это можно реализовать с помощью логических операторов and, not и or:

🟢 **and** — означает «И» для двух условий. Возвращает **tru**e, если оба условия истинны, и **false** — если ложны;

🟢 **or** — означает «ИЛИ» для двух условий. Возвращает **true**, если хотя бы одно из условий истинно, и **false** в противном случае;

🟢 **not** — означает «НЕ» для одного условия. Возвращает **true**, если условие ложно, и **false** — если истинно.

Эти операции используют, чтобы строить сложные логические выражения.

Пример:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6|`x` `=` `5`<br><br>`y` `=` `10`<br><br>`result` `=` `(x >` `0``)` `and` `(y <` `15``)`<br><br>`print``(result)`  `# Вывод: True, так как оба условия (x > 0 и y < 15) истинны`|

Другой пример:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8|`a` `=` `0`<br><br>`b` `=` `0`<br><br>`if` `a` `=``=` `0` `or` `b` `=``=` `0``:` `# Проверяется одно из условий`<br><br>    `print``(``"Одна переменная или обе равны 0"``)`<br><br>`else``:`<br><br>    `print``(``"Ни одна из переменных не равна 0"``)`|

В этом примере переменные a и b равны нулю. В условии мы проверяем, равна ли хотя бы одна переменная нулю. Если да — выводим сообщение «Одна переменная или обе равны 0». Когда ни одно из условий не выполнено (обе переменные не равны нулю), мы получаем сообщение «Ни одна из переменных не равна 0».

## Оператор if-else

Оператор **if-else** в Python — это конструкция, которая позволяет выполнить один из двух блоков кода в зависимости от того, выполняется условие (выражение после if) как истинное или ложное. Если условие **истинно**, выполняется **блок кода под if**. Если условие **ложно** — **else**.

Синтаксис выглядит так:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4|`if` `условие:`<br><br>    `# Блок кода, который выполняется, если условие истинно`<br><br>`else``:`<br><br>    `# Блок кода, который выполняется, если условие ложно`|

Например:

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6|`x` `=` `10`<br><br>`if` `x >` `5``:`<br><br>    `print``(``"x больше 5"``)`<br><br>`else``:`<br><br>    `print``(``"x меньше или равен 5"``)`|

Если значение переменной **x** больше пяти, выполняется блок кода под **if** и выводится «x больше 5». В противном случае выполняется блок кода под **else** и выводится «x меньше или равен 5».

Рассмотрим в качестве примера процесс аутентификации пользователя.

|   |   |
|---|---|
|1<br><br>2|`username` `=` `input``(``"Введите ваше имя пользователя: "``)`<br><br>`password` `=` `input``(``"Введите ваш пароль: "``)`|

Предположим, правильные данные для аутентификации — «user123» и «password123».

|                                                         |                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7 | `correct_username` `=` `"user123"`<br><br>`correct_password` `=` `"password123"`<br><br>`if` `username` `=``=` `correct_username` `and` `password` `=``=` `correct_password:`<br><br>    `print``(``"Успешная аутентификация. Доступ разрешен."``)`<br><br>`else``:`<br><br>    `print``(``"Ошибка аутентификации. Проверьте имя и пароль."``)` |

## Вложенные операторы if и if-else

Можно использовать одни условные операторы внутри других. С такими конструкциями можно строить более сложные логические структуры в зависимости от множества условий. Такие операторы полезны, когда нужно проверить несколько условий с дополнительными логическими шагами внутри каждого.

### Оператор if внутри другого if-оператора

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8<br><br>9|`x` `=` `10`<br><br>`if` `x >` `0``:`<br><br>    `print``(``"x - положительное число"``)`<br><br>    `if` `x` `%` `2` `=``=` `0``:`<br><br>        `print``(``"x - четное число"``)`<br><br>    `else``:`<br><br>        `print``(``"x - нечетное число"``)`<br><br>`else``:`<br><br>    `print``(``"x - не положительное число"``)`|

В этом примере, если x — положительное число, программа проверяет, четное оно или нет. Внутренний блок с вложенным оператором if выполняется только в том случае, если внешнее условие (x > 0) истинно.

### Оператор if-else внутри условия else

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8<br><br>9|`x` `=` `15`<br><br>`if` `x >` `10``:`<br><br>    `print``(``"x больше 10"``)`<br><br>`else``:`<br><br>    `print``(``"x не больше 10"``)`<br><br>    `if` `x` `%` `2` `=``=` `0``:`<br><br>        `print``(``"x - четное число"``)`<br><br>    `else``:`<br><br>        `print``(``"x - нечетное число"``)`|

В этом похожем примере, если x не больше десяти, программа проверяет, четный он или нет. Внутренний блок с вложенным оператором if-else выполняется в зависимости от четности числа. В случае x > 10 четность не проверяется.

## Оператор if-elif-else

Допустим, вам нужно определить тип треугольника.

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8<br><br>9<br><br>10|`side1` `=` `3`<br><br>`side2` `=` `4`<br><br>`side3` `=` `5`<br><br>`if` `side1` `=``=` `side2` `=``=` `side3:`<br><br>    `print``(``"Треугольник равносторонний"``)`<br><br>`elif` `side1` `=``=` `side2` `or` `side1` `=``=` `side3` `or` `side2` `=``=` `side3:`<br><br>    `print``(``"Треугольник равнобедренный"``)`<br><br>`else``:`<br><br>    `print``(``"Треугольник разносторонний"``)`|

В этом примере в зависимости от длины сторон треугольника программа определяет его тип. Если все три стороны равны, это равносторонний треугольник. Если две любые стороны равны, это равнобедренный треугольник. В противном случае треугольник считается разносторонним.

Рассмотрим другой пример. Допустим, нам нужно дать оценку работе студента по определенной системе.

|   |   |
|---|---|
|1<br><br>2<br><br>3<br><br>4<br><br>5<br><br>6<br><br>7<br><br>8<br><br>9<br><br>10<br><br>11<br><br>12<br><br>13|`grade` `=` `78`<br><br>`if` `90` `<``=` `grade <``=` `100``:`<br><br>    `print``(``"Отличная работа! Ваша оценка — 5."``)`<br><br>`elif` `80` `<``=` `grade <` `90``:`<br><br>    `print``(``"Хорошо сделано! Ваша оценка — 4."``)`<br><br>`elif` `70` `<``=` `grade <` `80``:`<br><br>    `print``(``"Неплохо, но можно лучше. Ваша оценка — 4−."``)`<br><br>`elif` `60` `<``=` `grade <` `70``:`<br><br>    `print``(``"Средне. Ваша оценка — 3."``)`<br><br>`elif` `0` `<``=` `grade <` `60``:`<br><br>    `print``(``"К сожалению, вы не прошли. Ваша оценка — 2."``)`<br><br>`else``:`<br><br>    `print``(``"Ошибка: Некорректная оценка. Проверьте ввод."``)`|

В этом примере, если оценка находится в диапазоне 90–100 включительно, программа выдает сообщение с оценкой «5». Если оценка находится в диапазоне 80–89, выдается сообщение с оценкой «4», и так далее.

Как выполняется **if-elif-else**:

- Программа проверяет условие_1.
- Если условие_1 истинно, выполняется блок кода под **if** и остальные блоки (**elif** и **else**) игнорируются.
- Если условие_1 ложно, программа проверяет условие_2.
- Если условие_2 истинно, выполняется блок кода под первым **elif** и остальные блоки (последующие **elif** и **else**) игнорируются.
- Процесс повторяется для каждого **elif** в порядке следования.
- Если ни одно из условий не истинно, выполняется блок кода под **else** — при его наличии.

## Главное об условном операторе if-elif-else в Python

🟢 Условный оператор **if-elif-else** в Python помогает написать код так, чтобы он выдавал результат в зависимости от того, выполняется определенное условие или нет. Когда есть несколько условий, можно использовать **elif**, чтобы проверять их поочередно. Если ни одно из условий не истинно, используют **else**, чтобы выполнить код по умолчанию.

🟢 В языке Python выражение считается истинным (true), если его результат — не ноль или выражение не является пустым объектом. А ложным (false) оно считается, если результат — ноль или пустой объект, в том числе значение none. При использовании операторов сравнения результатом выражения будет true, если условие выполняется, и false — в противном случае.

🟢 Внутри одного условия можно выполнять несколько сравнений, что позволяет расширить возможности использования условных конструкций. Это можно реализовать с помощью логических операторов: and возвращает **true**, если оба условия истинны, и **false** — если ложны; **or** возвращает **true**, если хотя бы одно из условий истинно, и **false** в противном случае; **not** возвращает **true**, если условие ложно, и **false** — если истинно.
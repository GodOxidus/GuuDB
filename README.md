# GuuDB
Задача: реализовать пошаговое исполнение кода для тривиального языка программирования Guu. 

*Внимание: в описании ниже заведомо опущены некоторые существенные моменты. Как правило, они остаются на ваше усмотрение.*

Программа на Guu состоит из набора процедур. Каждая процедура начинается со строки `sub` (subname) и завершается объявлением другой процедуры (или концом файла, если процедура в файле последняя). Исполнение начинается с `sub main`. 

Тело процедуры – набор инструкций, каждая из которых находится на отдельной строке. В начале строки могут встречаться незначимые символы табуляции или пробелы. Пустые строки игнорируются. Комментариев в Guu нет. 

В Guu есть лишь три оператора: — `set (varname) (new value)` – задание нового целочисленного значения переменной. — `call (subname)` – вызов процедуры. Вызовы могут быть рекурсивными. — `print (varname)` – печать значения переменной на экран. 

Переменные в Guu имеют глобальную область видимости. Программа ниже выведет на экран строку a = 2. 

```
sub main 
set a 1 
call foo 
print a 

sub foo 
set a 2 
```

А вот простейшая программа с бесконечной рекурсией: 

```
sub main 
call main 
```

Необходимо написать пошаговый интерпретатор для Guu. При его запуске отладчик должен останавливаться на строчке с первой инструкцией в `sub main` и ждать команд от пользователя. Минимально необходимый набор команд отладчика: 

 - `i` – `step into`, отладчик заходит внутрь `call (subname)`. 
 - `o` – `step over`, отладчик не заходит внутрь `call`. 
 - `trace` – печать stack trace исполнения с номерами строк, начиная с `main`… 
 - `var` – печать значений всех объявлённых переменных. 

Формат общения пользователя с отладчиком остаётся на выше усмотрение. Вы можете выбрать как минималистичный GDB-like интерфейс, так и консольный или графический UI. Названия команд отладчика можно при желании изменить. 

Для решения этой задачи вы можете использовать любой язык программирования из TIOBE TOP 50 и open-source компилятором/интерпретатором. 

При оценке работы будет оцениваться: 

Общая работоспособность программы; 
 - Качество исходного кода и наличие тестов; 
 - Простота расширения функциональности (например, поддержка новых операторов языка или инструкций отладчика). 
 - Решение с инструкцией по его сборке нужно опубликовать в Git-репозиторий (например, на GitHub или BitBucket). В ответе нужно указать ссылку на репозиторий. Подойдёт и ссылка на приватный GitHub-репозиторий, только в него потребуется добавить меня.

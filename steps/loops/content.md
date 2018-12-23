# Циклы в Ruby 

 В этом уроке мы познакомимся с циклами, научимся их создавать и совершать действия с каждым элементом массива.

Мы научимся создавать с помощью конструкций `while` и `for-in`, узнаем, что такое тело цикла, а также научимся поочерёдно обрабатывать в цикле элементы массива, вводить данные с консоли и узнаем о команде `break`.

### План урока

1. Что такое циклы, какие бывают, как их создавать и зачем они нужны
1. Работа с массивами и переменными в циклах


<!-- youtube starts here -->
<script>
var video_plan = {}
</script>

<div class="embed-responsive embed-responsive-16by9 rubyrush-video" id="video-0">
<iframe src="https://www.youtube.com/embed/14st-9905LU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<script>
video_plan["video-0"] = [{"begin":"0:07","comment":"Приветствие, план урока"},{"begin":"0:35","comment":"Циклы: что это и зачем нужны"},{"begin":"2:27","comment":"Циклы: пишем цикл while"},{"begin":"6:45","comment":"Циклы: бесконечный цикл"},{"begin":"8:04","comment":"Циклы: пишем цикл for"},{"begin":"11:37","comment":"Ввод данных в цикле, пишем программу «Элис»"},{"begin":"15:58","comment":"Итоги урока"}]
</script>
</div>

 <!-- youtube ends here --> 

### Что такое циклы

Если вспомнить наш образ дороги из 6-го урока, то иногда на нашей дороге машину нужно пустить по кругу. Например, если нам надо, чтобы грузовик загрузился углём в одном месте, доехал до другого и разгрузилась там и потом повторил всё это, скажем, 7 раз.

![Круговое движение](http://goodprogrammer.ru/system/rich_texts/000/000/13386090840c66db3ef82b3c23f365926b210a9420e/1.png?1429611968 "Круговое движение")

Более бытовой пример, с яйцами: вы купили в магазине десяток яиц, принесли их домой и вам нужно разложить их по специальным ячейкам на дверце вашего холодильника, для этого вам нужно будет взять каждое яйцо и положить его в нужную ячейку.

![Яйца в лотке](http://goodprogrammer.ru/system/rich_texts/000/000/1346ec26bed67fdab2ddb4ed30d2eb5d1afe750ea5e/2.jpg?1429611968 "Яйца в лотке")

Именно для таких повторяющихся действий в программах используются циклы.

### Цикл "while"

Оператор `while` нужен для того, чтобы сделать самый простой и универсальный цикл. Такой оператор есть в любом языке программирования.

Все, что он делает — повторяет указанный набор инструкций столько раз, сколько нужно. А сколько именно — зависит от условия цикла.

В этом смысле `while` очень похож на `if`, но в отличие от `if` условие будет проверяться каждый раз перед выполнением очередного повторения.

Сейчас вы все поймете на наглядном примере:

```ruby
count = 1

while count <= 5 do
  puts count
  count += 1
  sleep 0.5
end

puts "я иду искать!"
```

Наша программа запишет в переменную `count` целое число `1` и приступит к циклу.

Сначала программа проверит условие (`count <= 5`, клювик-равно означает «меньше или равно»), которое конечно будет выполнено, ведь в `count` сейчас лежит 1.

Так как условие выполнено, программа «войдёт» в цикл и начнёт выполнять всё, что написано между `while` и `end`. Этот блок называется «тело цикла».

### Оператор += (сложение с присваиванием)

В теле цикла появился новый для нас оператор `+=`:

```ruby
count += 1
```

Это очень простая штука. Эта запись эквивалентна записи

```ruby
count = count + 1
```

То есть, оператор `+=` говорит «сложить текущее значение переменной с тем, что следует за мной, и записать новое значение в ту же переменную». В нашем случае за оператором идёт единица.

Итак, после выполнения действий в теле цикла в первый раз, программа выведет на экран текущее значение `count` (1), увеличит это значение на 1 и потом «заснёт» на полсекунды.

А после этого снова проверит условие цикла. Теперь `count` равен 2 и поэтому условие снова выполнится. Так будет происходить 5 раз для значений `count` 1,2,3,4,5 и в последнем заходе `count` станет равным шести, а это уже больше пяти и условие в шестой раз не выполнится.

Программа выйдет из цикла и пойдёт дальше после слова `end`.

И выведет на экран строчку `"Я иду искать!"`

### Бесконечный (слепой) цикл

Будьте очень аккуратны с циклами! Если вы в предыдущей программе случайно перепутаете условие, поставив например,

```ruby
while count > 0
```

то условие цикла всегда будет выполнено и программа будет «крутиться» вечно. Если вдруг такое произошло, чтобы выйти из программы, нажмите в консоли во время её выполнения комбинацию клавиш `Ctrl+C`.

Эта комбинация досрочно прерывает любую программу, которая в данный момент выполняется в командной строке (или терминале).

### Цикл "for in"

Циклы очень удобны для выполнения повторяющихся операций с массивами. С массивами настолько часто работают с помощью циклов, что во многих языках придумали отдельный специальный цикл.

ОН делается с помощью конструкции "for in" и его главное предназначение — перебирать все элементы какого-нибудь массива. Цикл "for in" устроен следующим образом:

```ruby
array = [1,2,3,4,5]

for item in array do
  puts item
end
```

Разберём каждое слово в этой конструкции.

Начнём с `for`. Это служебное слово, которое говорит программе, что мы начинаем описывать цикл, в любой программе цикл "for in" будет начинаться с этого слова.

`item` — это особый ярлычок, так называемая внутренняя переменная цикла.
Рассматривайте ее как обычную переменную, с той важной разницей, что видна она только в теле цикла (внутри цикла). За пределами цикла она не видна (ее как будто не существует) и использовать её вне цикла нельзя.

Так же как и обычная переменная имя этой вы можете задать сами (вместо `item` можно написать `element` и  т. п.).

И как для обычных переменных — следите, чтобы имя этой внутренней переменной цикла не пересекалось с другими переменными вашей программы. Будьте аккуратны с выбором названий переменных. Это общее правило для всех ваших программ.

Вернемся к нашему циклу. На каждой итерации (каждом повторении) цикл будет брать каждый элемент из массива `array`, и по очереди, начиная с нулевого (помним, что в массивах нумерация начинается с нуля) — записывать в переменную `item` этот элемент.

Следующее слово в нашем цикле тоже служебное `in`, после него идёт тот самый массив, элементы которого циклу предстоит поочерёдно перебирать.

И наконец, дальше идёт переменная `array`, в которой содержится массив. Именно из этого массива будут браться элементы для поочерёдного укладывания их в переменную `item`, которая в теле цикла будет выводится на экран с помощью команды `puts item`.

Ну и, наконец, `end` заканчивает тело цикла точно также, как это было в цикле "while".

Если «перевести» это на русский язык, получится как-то так:

```sh
Для штуки в массиве
  выведи штуку
закончи
```

Согласитесь, довольно наглядно

![Конвеер Форда - жизненные пример работы с массивом машин в цикле](http://goodprogrammer.ru/system/rich_texts/000/000/1355ce1f7b2d2f45042a686de9d7dd0c6bed57dee2c/3.jpg?1429611968 "Конвеер Форда - жизненные пример работы с массивом машин в цикле")

### Ввод данных в цикле

Продемонстрируем всю мощь циклов и массивов с помощью простого примера — сбора данных в цикле. Напишем программку «Кто такая Элис?».

Задача программы — обыграть сюжет известной песни «А кто такая Элис?»: спросить у пользователя в цикле массив имен и затем вывести поочередно эти имена в определенных фразах. Но прерваться, если встретится имя Элис и расспросить пользователя подробнее о том, кто же она такая.

https://www.youtube.com/embed/C0-4U2nTYFQ

Для начала как обычно в папке урока `lesson7` создадим файлик `alice.rb`.

В нем создадим пустой массив `names` и воспользуемся знакомыми нам по урокам 5 и 6 командами `gets` и `push`, чтобы наполнять массив данными, которые пользователь введёт с помощью консоли.

```ruby
names = []

user_input = nil

while user_input != "" do
  user_input = gets.encode("UTF-8").chomp
  names << user_input
end
```

Как только пользователь введёт пустое имя (дважды нажмёт `Enter`), мы будем считать, что пользователь закончил ввод имён (это условие стоит после слова `while` в описании нашего цикла).

После этого мы переберём все введённые имена с помощью цикла "for in" и выведем их на экран в виде песенки:

```sh
С нами Миша
С нами Вадим
..
```

А если вдруг увидим слово «Элис» (именно такое условие стоит в условии оператора `if`), удивимся и спросим: «Элис?? Кто такая Элис?».

```ruby
for item in names do
  puts "C нами " + item
  sleep 1

  if (item == "Элис")
    puts "Элис??? Кто такая Элис?"
    sleep 1
    break
  end
end

puts "Что это за девочка и где она живет?"
sleep 1
puts "А вдруг она не курит? А вдруг она не пьёт?"
sleep 1
puts "А мы с такими рожами возьмем да и припрёмся к Элис... :)"
```

### Команда break

Обратите внимание, что в блоке "if-end" стоит команда `break`. Эта команда говорит программе, что пора выйти из цикла, какими бы ни были его условия.

`break` — очень полезная команда для досрочного выхода из цикла. Если нет возможности дождаться окончания текущей итерации, чтобы заново проверилось условие цикла.

Чтобы запустить нашу программу `alice.rb`, нужно перейти в вашей консоли в папку урока и запустить её с помощью привычных нам команд:

```sh
cd c:\rubytut\lesson7
ruby alice.rb
```

Итак, в этом уроке мы научились создавать циклы, разобрали создание циклов с помощью конструкций "while" и "for in". Научились в цикле работать с массивами, вводить данные с консоли и узнали о команде `break`.

В следующем уроке с использованием всех полученных ранее данных мы напишем игрушку тест на ревнивость и научимся ещё одному способу ввода данных в программу.
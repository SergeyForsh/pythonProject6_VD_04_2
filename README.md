# VD_04_2
Знакомство с фреймворком Flask для веб-разработки

✍🏻 Flask — это микро-фреймворк для разработки веб-приложений на языке Python. Он называется "микро", потому что не принуждает разработчика использовать определённые инструменты или библиотеки. Flask предоставляет базовый набор возможностей, оставляя разработчику свободу выбора остальных компонентов.

Существует множество библиотек, которые пригодятся нам для веб-разработки. Две самые популярные это Flask и Django.

Мы начнём с Flask, потому что он проще, чем Django.

Flask предлагает нам небольшой набор полезных функций, который облегчит нам создание приложений. Flask обеспечивает гибкость и является одним из самых доступных фреймворков. Он называется “микро”, потому что не принуждает разработчиков использовать определённые инструменты или библиотеки, а оставляет свободу выбора компонентов.

Чтобы начать работать с данным фреймворком, нам нужно его установить:

Заходим в PyCharm. Переходим в файл main.py, остальные файлы закрываем.
Слева внизу заходим в Python Packages.
Вводим flask.
Нажимаем на кнопку Install package.
При разработке любой программы мы должны хорошо структурировать проект: создавать папки и хранить файлы разных форматов в разных папках. При использовании Flask обязательно нужны две папки:

templates. Здесь будут HTML-файлы, шаблоны страниц;
static. В ней будут находиться статические файлы — неизменяемая информация, например, фотографии. Также в этой папке будут храниться CSS-файлы и JavaScript. В папке static также создаются две папки:
css;
image.
Структурируем файлы:

В левой секции нажимаем правой кнопкой мыши на верхнюю папку проекта, выбираем New — Directory.
Вводим название папки. Нажимаем на клавишу Enter.
Создаём вторую папку.
Выделяем HTML-файлы и перетаскиваем в папку templates.
Нажимаем на кнопку Refactor.
Создаём папки css и image внутри папки image. Переносим файлы.
Это обязательная структура. Без папки templates ничего не будет работать.

Создаём базовый код Flask, чтобы запустить проект:

Импортируем класс Flask из модуля:

from flask import Flask

2. Создаём переменную и сохраняем в неё объект класса Flask. Переменная name — это специальная переменная в Python, она содержит в себе имя текущего модуля, помогает фреймворку находить нужные ресурсы, шаблоны истатические файлы. 

app = Flask(__name__)

3. Начинаем создавать функции. Используем декоратор из модуля Flask:

app — переменная;

route — конкретный декоратор. Он нужен для того, чтобы позже мы могли прописать URL-адрес страницы.

Этот декоратор используется для того, чтобы мы прописывали маршруты, присваивали функциям ссылки и URL-адреса.

@app.route("/")

4. Создаём функцию. Введённая в кавычках фраза отобразится на сайте, когда мы запустим приложение. 

def hello_world():
    return "Hello World!"

5. Делаем запуск. Прописываем условие проверки. Если данный скрипт выполнен напрямую (из файла), то запускается локальный сервер (на нашем компьютере). Ссылка работает только на компьютере, пока что мы не можем отправить эту ссылку кому-то. 

if __name__ == "__main__"
    app.run()

6. Запускаем программу: нажимаем правой кнопкой мыши в любом месте и выбираем Run ‘main’.


7 Переходим по ссылке, которая появилась ниже. Откроется базовое веб-приложение.

Маршруты — одна из основных частей Flask, которая нам пригодиться.

Главная страница обозначается одним слешем (/) — та страница, которая открывается после захода на сайт. 
Это не конкретный адрес, а дополнение к адресу.

1. Дополняем код:

from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "Hello World!"

@app.route("/new/")
def new():
    return "new page"

if __name__ == "__main__"
    app.run()

2. Запускаем программу, переходим по ссылке.

3. В адресной строке дописываем к ссылке new/. Откроется новая страница.

При использовании Flask ссылки в HTML нужно будет заменить на дополнения. Позже мы посмотрим, как это делается.

Дополнения в маршруте можно писать и на русском языке.

Множественное декорирование — использование разных адресов для одной страницы.

@app.route("/new/")

@app.route("/newpage/")

@app.route("/новаястраница/")

return "new page"



Мы можем использовать такую же логику, как в Python. Переменные мы обозначаем треугольными скобками:

from flask import Flask

app = Flask(__name__)

@app.route("/")
@app.route("/<name>/")
def hello_world(name="незнакомец"):
    return f"Привет, {name}"

if __name__ == "__main__"
    app.run()

    
Теперь мы можем написать любое дополнение в адресную строку, и это дополнение будет выводиться на сайте после “Привет”.

Создадим код для введения пароля:

from flask import Flask

app = Flask(__name__)

@app.route("/")
@app.route("/<password>/")
def hello_world(password=None):
    if password == "1234":
        return f"Доступ разрешён"
    else:
        return f"Доступ запрещён"

if __name__ == "__main__"
    app.run()

    
Можно использовать условия, циклы и всё другое, что мы уже изучили.

Также мы можем прописывать HTML (но не очень удобно). Писать мы его будем в тройных кавычках, чтобы можно было писать много строк:

from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    html = """
    <h1>Тестовый запуск локального сервера</h1>
    <p>А это просто текст</p>
    """
    return html

if __name__ == "__main__"
    app.run()

    
Работа с HTML при помощи специальной функции:

вариант первый:

from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return flask.render_template() # Внутри () пишем название html-файла в кавычках

if __name__ == "__main__"
    app.run()
    
вариант второй:
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def hello_world():
    return render_template() # Внутри () пишем название html-файла в кавычках

if __name__ == "__main__"
    app.run()

    
Создаём однотипные страницы: меню, футер, контент:

Открываем файл index.html.
Подключаем bootstrap, как делали на прошлом уроке.
Копируем HTML-код из раздела “Навигация и вкладки” в документации:

<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link active" aria-current="page" href="#">Активная</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="#">Ссылка</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="#">Ссылка</a>
    </li>
    <li class="nav-item">
        <a class="nav-link disabled">Отключенная</а>
</li>
</ul>
            
4. Вставляем в начале файлов index.html и main.html.

5. Редактируем код в файле index.html. Это будет страница с фильмами.

<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link active" aria-current="page" href="#">Фильмы</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="#">Герои фильмов</a>
    </li>
</ul>

6. Редактируем код в файле main.html. Это будет страница с героями фильмов.

<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link" aria-current="page" href="#">Фильмы</a>
    </li>
    <li class="nav-item">
        <a class="nav-link active" href="#">Герои фильмов</a>
    </li>
</ul>

7. Запускаем оба файла по очереди, проверяем.

8. Редактируем код в файле main.py.

from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def films():
    return render_template("index.html")
    
@app.route("/person/")
def person():
    return render_template("main.html")

if __name__ == "__main__"
    app.run()
    
9. Редактируем код в файле index.html. Меняем вид ссылок.

<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link active" aria-current="page" href="/">Фильмы</a>
    </li>
    <li class="nav-item">
        <a class="nav-link" href="/person/">Герои фильмов</a>
    </li>
</ul>

10. Редактируем код в файле main.html. Меняем вид ссылок.

<ul class="nav nav-pills">
    <li class="nav-item">
        <a class="nav-link" aria-current="page" href="/">Фильмы</a>
    </li>
    <li class="nav-item">
        <a class="nav-link active" href="/person/">Герои фильмов</a>
    </li>
</ul>

11. Меняем заголовки <title> в обоих HTML-файлах.


12. Переходим в файл main.py. Запускаем сайт — теперь мы можем переключаться между страницами.


13. Редактируем содержимое HTML-файлов, чтобы изменить страницы. При этом пути изображений прописываем полноценно:

”..” означают выйти из папки один раз (пройти выше)

"../static/image/1.jpg"

14. Так же меняем пути файлов в CSS-файлах. При использовании bootstrap используем меньше своих стилей.

15. Заменяем текст на страницах.

Самое важное при работе с Flask:

всё должно быть расположено в папках;
относительные ссылки должны быть указаны правильно;
пути до файлов должны быть прописаны правильно.
---
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Home</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>

    ''' <!-- Центрированная навигация -->
    <nav class="nav-center">
        <a href="/">Главная страница</a>
        <a href="/blog">Рецепты</a>
        <a href="/contacts">Контакты</a>
    </nav>

    <div class="container">
        <h1 class="red-title">Японский десерт Моти</h1>
        <p class="#4cac16">
            Строго говоря, mochi — это не само пирожное, а японское тесто из очень клейкого риса мотигомэ,
            который приобретает нужную консистенцию и сладость,
            если его долго дробить и отбивать. Тесто для моти можно купить готовое,
            но сейчас в Москве в специальных магазинах продается и специальная рисовая мука для моти —
            чтобы кулинары могли пройти весь путь приготовления.<br><br>

            Как выглядит моти (mochi)? Это небольшой жемчужно-белый брикет,
            который для приготовления лакомств нужно разморозить. По сути, это и есть классический
            десерт моти: рецепт круглых тянущихся сладостей с начинкой — одна из его разновидностей.
            В целом можно просто поджарить во фритюре кусочки рисового теста и посыпать
            сладкой соевой крошкой — это тоже будет называться mochi.<br><br>

           Главная загвоздка моти — калорийность наполнителя. Само по себе рисовое тесто очень легкое,
            в нем содержится минимум жиров и сахара. А начинка для моти может быть и очень жирной
            (на основе крем-чиза, сливок, масляного крема),
            и низкокалорийной (желе, несладкий фруктовый мусс). <br><br>

            В среднем недиетический десерт моти содержит (на 100 г): <br><br>
            275 ккал; <br><br>
            2,3 г белков; <br><br>
            от 4 до 12 г жиров; <br><br>
            47 г углеводов. <br><br>
            Как сделать моти еще более легким? Если хочется снизить калораж сладостей,
            можно приготовить из рисовой муки домашнее ПП-моти без сахара и кокосового масла,
            а в качестве начинки взять манговое или клубничное пюре.<br><br>

            В последние годы ведутся споры: насколько эту японскую сладость можно считать ПП
            и стоит ли есть эти японские тянучки, находясь на диете? <br><br>

            С одной стороны, по калориям рисовые сладости выигрывает у целого ряда десертов.
            С другой, нужно понимать, что крем для начинки содержит много жиров,
            а кислые фрукты часто хочется сильно подсластить. В общем, даже здесь нужна мера:
            больше одного пирожного в день лучше себе не позволять,
            если вы стараетесь себя ограничивать в калориях.<br><br>

            Конечно, наиболее распространены десерты mochi в азиатских странах: Японии, Китае, Корее, Таиланде.
            Долгие столетия японцы не разглашали рецепт этих сладостей, зато потом ими заболела вся Азия,
            а в последние годы — и вся Европа. Особенно популярны эти лакомства в Италии, Германии, Великобритании,
            странах Восточной Европы. Конечно, в каждой стране пирожное обрастало новыми вариантами начинки:
            пломбир, соленая карамель, шоколад, кофейный мусс, суфле.
        </p>

         <img src="{{ url_for('static', filename='моти1.jpg') }}"
             alt="Моти" class="моти-photo">
         <img src="{{ url_for('static', filename='моти2.jpg') }}"
             alt="Моти" class="моти-photo">
         <img src="{{ url_for('static', filename='моти3.jpg') }}"
             alt="Моти" class="моти-photo">

        <img src="{{ url_for('static', filename='моти6_1.jpg') }}"
             alt="Моти" class="моти-photo">
        <img src="{{ url_for('static', filename='моти6_2.jpg') }}"
             alt="Моти" class="моти-photo">
        <img src="{{ url_for('static', filename='моти6_3.jpg') }}"
             alt="Моти" class="моти-photo">

    </div>
    
    <style>
        .моти-photo {
            width: 250px;       <br><br> /* устанавливает одинаковую ширину для всех изображений */
            height: auto;       <br><br> /* высота подстраивается пропорционально */
            margin: 10px;       <br><br> /* отступы для эстетики */
            object-fit: cover;  <br><br> /* изображение сохраняет пропорции, обрезаясь при необходимости */
        }
    </style>
    
</body>
</html>

'''
!<-->
.container p {
    max-width: 800px;               <br><br> 
    /* Ограничивает ширину текста для лучшей читаемости */
    margin: 20px auto;              <br><br> 
    /* Центрирует текст и добавляет вертикальные отступы */
    padding: 15px;                  <br><br> 
    /* Добавляет внутренние отступы для эстетики */
    text-align: justify;            <br><br> 
    /* Выравнивает текст по ширине */
    text-indent: 30px;              <br><br> 
    /* Отступ первой строки абзаца */
    line-height: 1.6;               <br><br> 
    /* Увеличенный межстрочный интервал для удобства чтения */
    font-family: 'Georgia', serif;  <br><br> 
    /* Элегантный шрифт для основного текста */
}
<br><br>
!<-->
'''

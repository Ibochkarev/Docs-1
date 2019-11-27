---
title: "Манипуляции с изображениями"
translation: "building-sites/tutorials/image-manipulation"
---

## Введение

Не хотите ждать, пока загрузится Photoshop? И я нет.
Этот урок познакомит вас с замечательным PHP-скриптом [phpthumbof](http://phpthumb.sourceforge.net/) портированным в [MODX](/extras/phpthumbof "phpThumbOf") Шоном МакКормиком.
[phpthumbof](/extras/phpthumbof "phpThumbOf") позволяет MODX автоматически генерировать миниатюры выбранной ширины и высоты для нас. Кроме того, в нашем распоряжении есть миллиард других полезных функций для работы с основными изображениями. Давайте поговорим о некоторых из самых полезных.

Этот урок предполагает, что вы знаете, как создавать и вызывать [переменные шаблона](building-sites/elements/template-variables "Переменные шаблона"). Знаете о [фильтрах вывода](building-sites/tag-syntax/output-filters "Фильтры ввода и вывода") это тоже удобно, но мы все равно заставим это работать, даже если вы о них не знаете (хотя они и хорошие).

В каждом из этих примеров предполагается, что вы создали переменную шаблона изображения с именем `big_image`, что он применяется к текущему документу, что вы указали действительное изображение, и что вы готовы произвести впечатление на своих клиентов, друзей и семьи. Давайте начнем.

**Хит производительности**
Если вы находитесь на общем сервере, помните, что чрезмерная обработка изображений может повлиять на других пользователей. Ваш хост может связаться с вами и/или приостановить вашу учетную запись, если это вызывает проблемы. Уменьшение размера изображения, даже если оно не соответствует точным размерам, приведет к сокращению использования ресурсов и времени обработки.

## Основное использование (изменение размера и обрезка)

Наиболее очевидное использование phpthumbof - это создание миниатюр из больших изображений. Вам больше не нужно беспокоиться о том, что ваши клиенты предоставляют слишком большие изображения - принесите эти 5 МБ фотографии размером 4800x3000! Допустим, вы хотите изменить размер вашей фотографии размером 5 МБ до 960 пикселей в ширину и 300 в высоту. Мы вызовем phpthumbof как [фильтр вывода](building-sites/tag-syntax/output-filters "Фильтры ввода и вывода") и укажем ширину (w) в 960, и высоту (h) в 300 пикселей:

``` php
[[*big_image:phpthumbof=`w=960&h=300`]]
```

Круто, наше изображение теперь правильного размера. К сожалению, если изображение не имеет правильного соотношения сторон, мы можем иметь отступы в одном направлении. Если вы предпочитаете обрезать более длинные размеры и сделать изображение подходящим для рамки, вы можете использовать зум кадрирование - параметр (zc):

``` php
[[*big_image:phpthumbof=`w=960&h=300&zc=1`]]
```

Хорошо смотрится!

## Удаление фона

У вас есть куча изображений с белым (или любым другим цветом) фоном, которые вы хотите превратить в прозрачный png? Давай сделаем это. Нам нужно использовать один из фильтров phpthumb, "stc". STC расшифровывается как «источник прозрачного цвета».

Для нашего примера мы будем держать его в 960x300 и удалим белый (#FFFFFF) фон. Мы также преобразуем его в png для участия в этом действии прозрачности:

``` php
[[*big_image:phpthumbof=`w=960&h=300&fltr[]=stc|ffffff&f=png`]]
```

Отлично работает!

## Обесцвечивания

Мы можем сделать кучу других вещей, используя фильтры phpthumb. Давайте обесцветим изображение на 90%.

``` php
[[*big_image:phpthumbof=`w=960&h=300&fltr[]=sat|-90`]]
```

Круто!

## Раскраска

Хотите тонировать изображение? Мы можем сделать это! Давайте подкрасим 30% #ff00ff:

``` php
[[*big_image:phpthumbof=`w=960&h=300&fltr[]=clr|30|ff00ff`]]
```

Замечательно!

## Цепочка

Это все круто и все такое, но мы можем добиться большего. Крутая вещь об этих эффектах состоит в том, что они могут быть связаны.

Давайте полностью обесцветим изображение, украсим его на 20%, а затем подкрасим на 6% #00ab86:

``` php
[[*big_image:phpthumbof=`w=960&h=300&fltr[]=gray&fltr[]=brit|20&fltr[]=clr|6|00ab86`]]
```

Это какая-то мощная цепочка.

## Читать далее

Мы действительно только охватили верхушку айсберга. Phpthumb имеет много других применений, [задокументировано на сайте phpthumb](http://phpthumb.sourceforge.net/). 
Иди делай классные вещи!
Как только вы почувствуете себя комфортно с вышеперечисленным, проверьте [phpthumb readme](http://phpthumb.sourceforge.net/demo/docs/phpthumb.readme.txt) и приготовьтесь к тому, что ваш ум снова взорвется. [Здесь](http://www.belafontecode.com/image-manipulation-with-phpthumbof-in-modx-revolution/) это еще один учебник phpthumb
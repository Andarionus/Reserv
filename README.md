# АНАЛИЗ ДАННЫХ В РАЗРАБОТКЕ ИГР
Отчет по лабораторной работе #4 выполнил(а):
- Галимуллин Андрей Александрович
- РИ-230932
- Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Оценить стркутуру и фунционал перцептрона. На его основе реализовать различные логические элементы.


## Задание 1
###  Задание 1: в проекте Unity реализовать перцептрон, который умеет производить вычисления:
OR | дать комментарии о корректности работы

AND | дать комментарии о корректности работы

NAND | дать комментарии о корректности работы

XOR | дать комментарии о корректности работы


Ход работы:
- После анализа лекции, на unity был загружен скрипт перцептрона и реализованы следующие логические элементы (с комментариями).
1) OR | В первую очередь стоит выделить то, что таблица не совсем отражает реальную сторону баланса в игре. К примеру, у ПП (узи в билде на юнити) в файлах указан самый низкий урон за выстрел (3). И хоть, по идее, высокая скорострельность, скорость перезарядки и определённая отдача должны были компенсировать данный момент, по таблице казалось, что оно тоже требует определённого усиления. Однако в игре имеется механика попаданий в голову, которые существенно повышают урон у всего оружия за попадания (чуть ли ни одниковый у всех, по мои наблюдениям). Поэтому на самом деле та же ПП занимает роль не зачиски треша, а так же как и АКМ подходит для острела босса с расстояния (если метить в голову, конечно).
![изображение](https://github.com/user-attachments/assets/f189689e-0982-4cc6-a7fb-9139d7774ebf)
![изображение](https://github.com/user-attachments/assets/5475712c-9b8f-496c-a8e9-7ed8f45d4c15)
![изображение](https://github.com/user-attachments/assets/bf2eb4d2-8d3b-4ae2-b21c-74da529d7413)

2) AND | Далее стоит заметить, что в приципе в игре остуствует оружие, занимающее нишу зачистки треша на высоких волнах. Базовое оружие, с которым игрок начинает забег и которое можно просто найти на карте (револьвер, пистолет, тесак и дробовик), довольно странно сбалансированно. Револьвер и по таблице предсталяет собой нечто мусорное, а тесак с дробовиком работают уж слишком на ближней дистанции (в сранении с той же двухстволкой в думе 2016/этёрнал), в то время как пистолет слишком хорош (ввиду остуствия отдачи, среднего магазина и дальности). Ограничивает лишь экономическая система в игре. В стандартном забеге игрок всё равно будет спускать всю валюту на патроны для пистолета, в время как крайне дорогостоящее оружия высокого уровня во всём лучше бесплатных аналогов. АКМ и ПП идеально чистят мобов и боссов на любом расстоянии, в время как пила и вовсе имеет бесконечный урон (судя по данным из файлоа).
3) NAND | Из всего выше сказанного мною был сделан вывод, что можно начать с заполнения ниши зачистки треша на более высоких волнах (где и боссы и мобы встречаются одновременно, как выяснилось). Так как балансировкой оружия под разные задачи мы занимаемся в дополнительном задании 3*, я пока лишь отобразил в таблице некоторое влияние отдачи у определённого оружия на вероятность попадания (номинально, у оружия кроме дробовика, тесака и пилы дальность макисмальная одинаковая). В итоге предлагаю я добавить "огнемёт" (ака flamethrower). Имеет он самый большой боезапас в 50, быстрый shoot delay в 0,01, низкую скорость перезарядки в 3,5 и урон в 8 единиц. Работает посредством механики создания линии перед персонажем игрока, которая в области (равной половине макимальной длины) наносит постоянний урон всем попавшим в неё мобам. Во избежания серьёзного урона по боссам, у данного оружия отключена механика повышенного урона в голову. Кроме того, на крайнем расстоянии от игрока скорость нанесения урона слегка уменьшается (отображенно как увеличение вероятности промаха). По исчислениям в таблице видно, что он как раз занимает место между АКМ и ПП до падения дальности (в отличие от дробовика, который совсем не далеко от ножа смог отойти). Более подробно про таблицу в следующем задании.
4) XOR |
![изображение](https://github.com/user-attachments/assets/f189689e-0982-4cc6-a7fb-9139d7774ebf)
![изображение](https://github.com/user-attachments/assets/5475712c-9b8f-496c-a8e9-7ed8f45d4c15)
![изображение](https://github.com/user-attachments/assets/bf2eb4d2-8d3b-4ae2-b21c-74da529d7413)




## Задание 2
###  Визуализируйте параметры оружия в таблице.Используйте шаблон таблицы для визуализации оружия игры Save RTF. Постройте примеры для следующих математических величин (см. пример в презентации)
- Среднеквадратическое отклонение (СКО)
- Разброс урона оружия
- Вариативность времени отклика игрока (реакция на события)
Ход работы:
- В первую очередь был заменён первый сегмент таблицы "Выстрелов в едю времени" на "Темп стрельбы с учётом перезарядки и объёма магазина", который, как мне кажется, куда лучше отображает скорость стрельбы определённого оружия (в базовом варианте получалось, что револьвер с дробовиком не так сильно уступают другому оружию, хотя у обоих наименьший объём магазина, что ведёт к постоянным перезарядкам). Формула выглядит следующим образом: (1 - Shoot Delay)*(размер магазина)/(время перезарядки). Благодаря такой формуле видно примерно то же, что наблюдается в самой игре (АКМ с ПП имеют наибольшую плотность огня, даже с учётом медленной перезарядки АКМ, в то время как револьвер, дробовик и нож нуждается в олпределённом ребалансе). Пила же имеет и в игре параметр урона 0, как и параметр Shoot Delay, так что считаем её в не таблицы с бесконечными, по сути значениями. С остальными сегментами таблицы, по сути, никаких изменений не проводилось (кроме тех, что указаны в задании 1).
- Под сегментом таблицы "Средний урон" в столбик подсчитан "Разброс урона оружия" (справа от него среднее значение по строке). Ввиду того, что показатели в строке распределены не равномерно разброс может слегка отличаться от реального значения (+/- единица). Найден он был путём вычитания из макимального значения в строке среднего значения.
- Далее под сегментом таблицы "Средний урон" подсчитано среднеквадратическое отклонение урона для всего оружия, которое имеет в этом смылс (исключения - нож и пила). Используется формула из теории вероятности, представленная ниже.
- Попытка подсчёта вариативность отклика же вызвала некоторые трудности. В реалиях геймплея Save RTF вариативности в приципе не так много, что уж до реакции на события. ибо основная механика - стрельба, по каким-то причинам, не подвластна влиянию игрока. Игровой персонаж в любом случае начнёт стрелать из выбранного оружия, а мобы  не перестанут приходить. Проблемы однозначности прокачки я тоже рассматривал в предыдущей работе (хотя забег с макимальной скоростью и пилой показал, что с вампиризмом всё не так однозначно, но игрок в жизни через такой гринд без кода не пролезет). Единственный момент, который можно было бы как-то просчитать, так это экономический вопрос (когда и как игрок покупает новое оружие, например). Однако в этой части тоже есть проблема, что просто не позволит накопить достаточно валюты за забег для этого, описанна она была выше и в прошлой работе. Поэтому с данным пунктом затрудняюсь выдать какую-либо визуализацию.
![изображение](https://github.com/user-attachments/assets/534998d3-bca4-48ab-8da3-8c4354e02dff) ![scale_1200](https://github.com/user-attachments/assets/3b17b372-5f04-4605-8dda-dc839215a462)



## Задание 3
### Решение в 80+ баллов должно визуализировать данные из google-таблицы, и с помощью Python передавать переменные в проект Unity. В Python данные также должны быть визуализированы.

- В гугл таблице представлена диаграмма эффективности оружия в зависимости от дальности, детали которой были описаны выше. По ней видно, что оружие нуждается в определённом ребалансе, в том числе пила, которая в приципе выходит за рамки таблицы (по своей сути, можно было бы добавить механику из дума с добиваниями с помощью пилы (долго, не слишком эффективно, но даёт кадры неуязвимости и восстанавливает определённые ресурсы)).
- Далее был написан код на питоне, что вводит в гугл таблицу значения вероятности попадания оружия (для боллее быстрой обработки, переносится в работе лишь значения пистолета и огнемёта (для наглядной разницы)), диаграмма присутствует та же. Из гугл таблицы переменные передаются в проект на юнити, где в зависимости от шанса на попасть воспроизводятся разные звуковые файлы (при больше %50 попал, при меньше - промахнулся)
![изображение](https://github.com/user-attachments/assets/534998d3-bca4-48ab-8da3-8c4354e02dff) 
![изображение](https://github.com/user-attachments/assets/d7b5e28d-99e0-4341-ae80-fe24c1c36915)

![изображение](https://github.com/user-attachments/assets/16824b95-9e91-4112-b0ab-f6d8dba8729b)

![изображение](https://github.com/user-attachments/assets/6d034d03-5862-49d0-ab8a-ae0fbb02a047)


## Выводы

"Удивительный" опыт первой попытки как-то проанализировать оружие в Save RTF через геймплей, конечно, дал результаты похожие на то, что есть в коде, но в то же время были далековаты от правды и пестрели моими домыслами. Однако после публикации исходников таблица начала обретать свой финальный вид (бесконечный урон пилы, ребаланс и тд). Более подробно о ребалансе будет мною описано в задании 3*, а пока лишь добавлю, что была проведена работа с данными в гугл-шаблоне, а так же был написан код на питоне/С# для юнити, основанный на материалах предыдущего задания. И всё даже работает.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**

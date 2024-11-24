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
1) OR | Логическая операция "или" реализована, как показано на скриншотах ниже. Для минимизации количества ошибок (0) достаточно и 4 эпох перцептрона, однако с другой стороны правильную последовательность на тесте в консоль выведет и с 1 ошибкой в последней эпохе. Поэтому и 2/3 эпох может быть достаточно для получения примерных коэффициентов и правильной последовательности на тесте (номинально может хватить и одной эпохи, если перцептрон сразу подберёт правильные значения). При 8 эпохах почти гарантированно будет нулевое количество ошибок. Работа перцептрона при данной линейной функции вполне корректна.
![изображение](https://github.com/user-attachments/assets/f189689e-0982-4cc6-a7fb-9139d7774ebf)
![изображение](https://github.com/user-attachments/assets/5475712c-9b8f-496c-a8e9-7ed8f45d4c15)
![изображение](https://github.com/user-attachments/assets/bf2eb4d2-8d3b-4ae2-b21c-74da529d7413)

2) AND | Логическая операция "и" реализована и работает корректно. В приципе, всё то, что указано выше про "или" относится к "и". Одной ошибки достаточно для верного прохождения теста, 4 эпох хватает для получения нулевого количества ошибок с определённой периодичностью. Однако здесь добавлю, что во время реализации визуальной модели на Unity четырёх эпох для обучения перцептрона для "и" стало не хватать (по какой-то причине на 10 моих запусков, в консоли меньше 3 ошибок отказывалось выдавать в последней эпохе). Поэтому там количество эпох было изменено на 6 и частота выполнения теста стала вновь приемлемой.
![изображение](https://github.com/user-attachments/assets/5508f318-92b9-4e2f-b0c2-269decd2f45a)
![изображение](https://github.com/user-attachments/assets/37523564-eca3-45d2-9715-dc428f918b32)
![изображение](https://github.com/user-attachments/assets/84d6b1fe-b0a2-42f0-b522-70ff35a20f89)

3) NAND | Логическая операция "не и" реализована и работает корректно. Всё так же правильно проходит тест и при 1 ошибке в последней эпохе, от четырёх эпох вполне достаточно для нулевого количества ошибок в большинстве случаев.
![изображение](https://github.com/user-attachments/assets/d6534723-e68c-41e6-ad44-06b4904f2e9b)
![изображение](https://github.com/user-attachments/assets/e880935f-30ec-4190-af77-09bca0b8d2eb)

4) XOR | Логическая операция "исключающее ИЛИ" реализована номинально на unity, однако корректно не работает. Ввиду нелинейности фукции "исключающее ИЛИ" перцептрон не может подобрать нужные коэффициенты, определённая часть данных теряется. Минимальное количство ошибок - 3, чего недостаточно для прохождения теста, даже при 20 эпохах результат будет почти таким же, как и при 8. Таким образом перцептрон не подходит для корректной реализации XOR.
![изображение](https://github.com/user-attachments/assets/8efe5a1b-0ff1-4496-abe8-272aba894c56)
![изображение](https://github.com/user-attachments/assets/deea9872-4e84-404f-9cf5-888cf4890f99)



## Задание 2
###  Построить графики зависимости количества эпох от ошибки  обучения. Указать от чего зависит необходимое количество эпох обучения.

Ход работы:
- Как указано в задании 1, реализация перцептрона у разных логических элементов не сильно отличется, поэтому графики будут построены на основе выходных данных с операцией "и", как пример.
- В первом случае проведём 8 эпох и построим график зависимости (эпохи - ось OX, ошибки - ось OY)

![изображение](https://github.com/user-attachments/assets/548ff393-2faf-461b-a74c-e7f6b6ee61ba)

Как из него видно, первые пять эпох перцептрон подбирает случайные коэфициенты (количество ошибок то увеличивается, то уменьшается), однако после успешных прохождений теста с 0 количеством ошибок, последние три эпохи их количество не меняется (перцептрон не меняет значения)
- Другой пример с 4 эпохами

![изображение](https://github.com/user-attachments/assets/85a92de1-104a-4ae0-9bfb-d572f1e948f1)

В данном случае перцептрону не удалось обучится за указанное количество эпох, поэтому количество ошибок нелинейно возрастает и уменьшается до последней эпохи.

- В итоге по этим нелинейным графикам можно выдвинуть следующее утверждение, характеризующее зависимость количество эпох от ошибки обучения - количество эпох засисит от установленной точности результата обучения (процесс обучения продолжается до тех пор, пока не достигнет приемлемой точности). То есть, в зависимости от нужной точности (с какой наибольшей вероятностью перцептрон решает тест без ошибок) выставляется закономерное количество эпох. Чем больше эпох, тем больше вероятность того, что перцептрон всё же обучится.



## Задание 3
### Построить визуальную модель работы перцептрона на сцене Unity.

Ход работы:
- Для построения визуальной модели работы перцептрона на сцене Unity использована следующая идея. Был взят за основу код перцептрона из лекции и модифицирован, в частности, добавлена переменная Cubuc в начале, которая в методе Train изменяется в 0, если количество ошибок в эпохе меньше либо равно единице (как выяснили выше, при данных значениях перцептрон успешно проходит тест). Далее в методе OnTriggerEnter, если Cubuc равен 0, то при входе в зону триггера объект с перцептроном изменяет свой цвет (на белый и об этом далее). Для наглядности, перцептрон обучается за 6 эпох в данном скрипте (чтобы получать не только успешные итерации обучения перцептрона).
![изображение](https://github.com/user-attachments/assets/8c6e1865-be72-4bbe-a43c-226a4f7b067b)
- На самой сцене был размещён пол, два куба (ноль (белый цвет) и единица (чёрный цвет)) и сферический тригер. Для визуализации была выбрана логическая операция "и". На сцене объекты размещены следующим образом: белый куб лежит на полу в зоне триггера, чёрный завис над зоной, сам триггер задевает оба обекта при падении. Идея состоит в том, что когда чёрный куб оказывается в зоне триггера, он меняется свой цвет на тот, что соответствует результату логической операции "и" на 0 и 1 (белый и чёрный соответственно). Для этой цели к чёрному кубу добавлен компонент Rigidbody (чтобы он падал в триггер) и скрипт перцептрона описанный выше. Если перцептрон обучился с минимальным количеством ошибок, то куб окрашивается в белый (0, как верный исход операции "и"). Если же количество перцептрон обучился с большим количеством ошибок, то куб остаётся чёрным при входе зону триггера.
![изображение](https://github.com/user-attachments/assets/ba9cc292-3dee-4eb9-97cb-b3c3bc713830)
![изображение](https://github.com/user-attachments/assets/dc815fe9-f2d5-41a8-9130-abe44ab536e0)
![изображение](https://github.com/user-attachments/assets/8e0a42f9-d38e-43d2-a1d0-48ba1e32f738)



## Выводы

Модель перцептрона, представленная на лекции, была реализована и визуализирована на Unity, кроме того, был построен график зависимости эпох от ошибок. Основные раздумья были связаны с выполнением третьего задания. В лекции предлагалось использовать метод OnCollisionEnter, который реализует последствия столкновения двух объектов (куб падает на другой куб, к примеру). Данный вариант показался мне мало применимым в реалиях программирования на Unity, поэтому был придуман свой вариант с вхождением объекта в зону некого триггера (ибо некие вычисления для игрового персонажа до входа в определённую зону с триггером определённо используются на моём опыте). Опыт интересный и много где применимый по итогу, хоть и перцептрон явно сейчас немнго устарел и в будущем было бы неплохо поработать с другими моделями нейронов. 

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

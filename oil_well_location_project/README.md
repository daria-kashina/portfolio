# Выбор локации для скважины

## Задача
Построить модель для определения региона, где добыча принесет наибольшую прибыль. Проанализировать возможную прибыль и риски техникой Bootstrap. После оценки рисков нужно оставить лишь те регионы, в которых вероятность убытков меньше 2.5%. Среди них выбирают регион с наибольшей средней прибылью.

## Данные
Представлены пробы нефти в трёх регионах. Известны характеристики для каждой скважины в регионе.
1) При разведке региона исследуют 500 точек, из которых с помощью машинного обучения выбирают 200 лучших для разработки.
2) Бюджет на разработку скважин в регионе — 10 млрд рублей.
3) При нынешних ценах один баррель сырья приносит 450 рублей дохода. Доход с каждой единицы продукта составляет 450 тыс. рублей, поскольку объём указан в тысячах баррелей.

## Стек
matplotlib, numpy, pandas, pandas_profiling, python, seaborn, sklearn

## Ход работы
### EDA и предобработка данных
   Проверка данных, характера распределений запасов нефти и признаков по регионам, пропусков, выбросов. Анализ статистических данных по регионам. Разбиение данных на обучающую и валидационную выборки по регионам.
### Обучение моделей
   Для обучения использовалась только линейная регрессия, т.к. остальные модели недостаточно предсказуемые. Вычисление RMSE модели на валидационной выборке, среднего запаса предсказанного сырья для каждого региона. Анализ стат. данных по объму нефти (таргет) в валидационных выборках, сравнение предсказаний со стат. данными, предварительная оценка рисков.
### Расчет прибыли
   Расчет достаточного объема сырья для безубыточной разработки новой скажины. Сравнение полученного объема сырья со средним запасом в каждом регионе. 
   Расчет прибыли по 200 скважинам c максимальными значениями предсказаний модели по регионам.
   Анализ распределения прибыли при помощи техники Boostrap. Расчет средней прибыли, 95%-го доверительного интервала и риска убытков. Выбор самого прибыльного региона с наименьшими рисками.
## Результат
   Cамым прибыльным регионом с наименьшими рисками является регион №1. Cредняя прибыль в 1-м регионе составляет 452.58 млн руб , 95%-ый доверительный интервал лежит в диапазоне от 52.31 до 830.15 млн. руб - то есть убытки (отрицательные значения прибыли) лежат за пределом 95%-го доверительного интервала. Риск убытков в 1-м регионе составляет 0.9%.
   
   Наименее прибыльный регион - №2. Он имеет наименьшую среднюю прибыль по региону = 378.71 млн. руб, а также самый высокий риск убытков: 7.5%.
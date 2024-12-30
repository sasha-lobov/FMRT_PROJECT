# Разработка алгоритма для сопоставления временных рядов ФМРТ
## Цель: разработать алгоритм на Python, способный определить, принадлежат ли два заданных временных ряда фМРТ одному и тому же человеку. Эту задачу можно рассматривать как задачу сопоставления объектов, цель которой — сравнить профили двух сканирований мозга и определить, принадлежат ли они одному и тому же человеку.
## Краткие сведения:
Функциональная магнитно-резонансная томография (ФМРТ) - это метод нейровизуализации, используемый для изучения мозговой активности путем измерения изменений кровотока. В отличие от стандартной МРТ, которая генерирует статические изображения анатомии мозга, ФМРТ фиксирует динамические изменения нервной активности с течением времени. Это достигается за счет использования сигнала, зависящего от уровня кислорода в крови (выделено жирным шрифтом), который меняется в зависимости от насыщения гемоглобина кислородом. Когда нейроны активны, они потребляют больше кислорода, что приводит к изменению магнитных свойств гемоглобина. Эти изменения можно обнаружить и визуализировать с помощью функциональной МРТ, что позволяет исследователям наблюдать, какие области мозга активны в ответ на определённые стимулы или задачи. 
## Входные данные (Inputs):
Предоставляются необработанные данные, для которых необходимо выполнить обработку. Всего имеется 20 объектов для фМРТ-сканирования, для каждого объекта имеется 16 (2x2x2x2) представлений, соответствующих двум различным разделам атласа мозга (Brainnetome и Schaefer200), двум различным стратегиям сглаживания, двум сегментам последовательности сканирования, двум различным последовательностям. Структура набора данных выглядит следующим образом [20*16 objects, 10 timesteps from scan sequence, 246 number of features in larger atlas]. 
## Выходные данные (Outputs):
матрица данных размерностью (m, n), где m - индексы временных рядов для одного и того же человека, n - порядковый номер человека.
## Принцип работы алгоритма:

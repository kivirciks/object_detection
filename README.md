<h1>Детектирование изображений</h1>
<h2>Входящие файлы</h2>
<li>4140_CV_ЛР2_Строкова.ipynb - ноутбук с программным кодос на Python;
<li>4140_CV_ЛР2_Строкова.pdf - текстовый отчет;
<li>Каталог "Изображения" - исходные и итоговые изображения.
<h2>Постановка задачи</h2>
Цель работы: исследовать простейшие алгоритмы детектирования объектов на изображении. <br>
<br>
Базовый алгоритм: прямой поиск одного изображения на другом, поиск ключевых точек эталона на входном изображении.<br>
<br>
Задание: на вход поступает два изображения: эталон и изображение, на котором будет производиться поиск. На выходе программа должна строить рамку в виде четырехугольника в области, где с наибольшей вероятностью находится искомый объект.<br>
<br>
Задачи: 
<li>реализовать алгоритм прямого поиска одного изображения на другом (template matching);
<li>реализовать алгоритм поиска ключевых точек эталона на входном изображении (ORB).
<br>
<h2>Теоретическая база</h2>
Задача нахождения объектов на изображении – задача машинного обучения, в рамках которой выполняется определение наличия или отсутствия объекта определенного домена на изображении, нахождение границ этого объекта в системе координат пикселей исходного изображения [3]. <br>
  <br>
В данной работе будет реализован алгоритм детекции объектов. Программный код написан в Google Collaboratory на языке Python. <br>
  <br>
В первой половине работы использовался алгоритм прямого поиска изображения с помощью библиотеки OpenCV. Для этого бралось изображение объекта на нейтральном фоне, вырезался фрагмент и сохранялся под другим именем. На вход подавалось два изображения, которые алгоритм сравнивал и выводил рамку вокруг детектированного объекта. <br>
  <br>
Существует несколько методов matching template, в данной работе использовался cv.TM_CCOEFF (находятся глобальные максимумы с помощью функции minMaxLoc). Отмечу, что на вход может подаваться как черно-белое, так и цветное изображение, однако на выходе оно все равно преобразуется в одноканальное.
Во второй половине работы опробован алгоритм ORB (Oriented FAST and Rotated BRIEF). <br>
<br>
Алгоритм работает следующим образом [4]:<br>
<li> Особые точки обнаруживаются при помощи быстрого древовидного FAST (сравнивается яркость пикселей вокруг выбранной точки) на исходном изображении и на уменьшенном.
<li> Для обнаруженных точек вычисляется мера Харриса, кандидаты с низким значением меры Харриса отбрасываются.
<li> Вычисляется угол ориентации особой точки, на основе которого последовательность точек для бинарных сравнений в дескрипторе BRIEF поворачивается.
<li> По полученным точкам вычисляется бинарный дескриптор BRIEF (набор признаков, который характеризует окрестность каждой особой точки).
<br>
<h2>Прямой поиск одного изображения на другом (Template Matching)</h2>
Для осуществления Template Matching считаем исходное изображение и вырезанный фрагмент, найдем объект, затем выведем итоговые изображения. <br>
!(https://github.com/object_detection/Изображения/Прямой_поиск/0.png)
 

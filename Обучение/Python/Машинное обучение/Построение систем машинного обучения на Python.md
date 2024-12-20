# Данные
Большая часть работы в машинном обучении, так или иначе касается обработки данных. При этом на сколько бы продвинутым алгоритм, обучающий модель не был, все равно на хорошо обработанных данных он будет работать намного лучше.
При этом мы знаем, что чистый питон, так или иначе - очень медленный язык, так как это язык - компилируемый. То есть код из питона сначала переводится в код на языке С, а затем уже в машинный код - последовательность нулей и единиц.
Но эту особенность питона можно обойти с помощью таких библиотек, как **NumPy** и **SciPy**. Это библиотеки, изначально написанные на языке C. Они способны ускорить код в десятки раз. Но при этом есть и недостатки, например, теряется гибкость языка. Появляются такие вещи, как строгая типизация, строгое установление размерности массивов, либо, если использовать NumPy в качестве хранилища матриц, или данных, то код замедляется в разы.
## NumPy
Данная библиотека служит для ускорения кода. В ней есть масса полезных методов, начиная от нативных списков, матриц и пр, до методов умножения матриц, и пр. 
Также у списков, или матриц, которые идут вместе с этим модулем, добавляются такие свойства, как, например `.shape()`, и да. То есть то, чего нет в оригинальном списке от коробки `питона`.
Признаком здорового тона, и здравого рассудка является выполнение всех вычислений, сортировок, и пр. именно в этой библиотеке.
## SciPy
Данная библиотека, насколько я понимаю, является, как бы, надстройкой над оригинальным NumPy, и, на сколько я понимаю, добавляет новые методы для выполнения вычислений. 
Как советует автор книги, если есть потребность найти что-либо, что-то вычислить, то сперва нужно постараться найти некий метод в этих двух библиотеках. Скорей всего это есть там.
Также важно помнить, что эти две библиотеки, как бы, являются тождественными:
```python
import numpy, scipy

print(numpy.dot == scipy.dot)         # True
```

## MatPlotLib
Для визуализации полученных данных принято использовать данную библиотеку. Она хороша тем, что есть в коробочном питоне, и ее не нужно дополнительно устанавливать. Также это довольно мощный, хоть и простой вариант решения задач.
В книжке, на данном этапе применяется `matplotlib.pyplot`. 
```python
import matplotlib.pyplot as plt

plt.scatter(x, y, s=10)      # Режим отображения - кружочки, радиусом 10px. x и y - списки.
plt.title("Заголовок всего графика")
plt.xlabel("Легенда оси Х")
plt.ylabel("Легенда оси У")
plt.grid(True)               # Отображение сетки
plt.autoscale(tight=True)    # Автоматическое масштабирование под размеры полотна
```

# Первая обученная модель
Автором книги приводится в пример модель, которую можно обучить. И делается это в модуле SciPy. Насколько я могу понять, это не то, чтобы обучение, сколько: 
>Нахождение такой прямой, которая будет, как бы, повторять тренды развития данных. 

Возможно, это также используется под капотом моделей, которые кластеризируют, видят, и прочее.

## Ошибки
Всякая модель подвержена ошибкам, как ни крути. Избавиться от нее на 100% мы не можем. Но нам и не надо, потому что это то, что делает наши данные "живыми". 
Есть различного рода шумы, помехи, и прочее, что "мешает" жить и работать в идеальной картине мира.
Чтобы вычислить ошибку авторами используется такая функция:
```python
def error(f, х, у):
	return sp.sum((f(x)-y)**2)
```
>Погрешность вычисляется как квадрат
расстояния между реальными и предсказанными моделью данными

## Полином
Автором предлагается метод обучения. Это некая функция в составе scipy - `polyfit(x, y, 1)`, которая принимает на вход массив из значений по Х, по У, и степень полинома.
>Полином, это линия, которая показывает закономерность развития данных. То есть линия тренда.

На выходе эта функция возвращает также массив, в котором будут указаны так называемые параметры функции.
```python
>>> рrint("Параметры модели: 's" % fpl) 
# Параметры модели: [2.59619213, 989.02487106]
```
Далее нужно построить модельную функцию по параметрам модели. Это нужно для того, чтобы, наконец, увидеть линию тренда.
Функция, которая нам нужна - `polyld(fp1)`
И, наконец, можно нанести это дело на график:
```python
fx = sp.linspace(O,x(-1), 1000) # сгенерировать значения Х для графика 
plt.plot(fx, fl, linewidth=4) 
plt.legend(["d=%i" % fl.order], loc= "upper left"I
```

Также крайне важно смотреть на **ошибки**. Это именно то, что было разобрано в главе выше. Если подставить в функцию наши данные сейчас, то можно получить число, которое покажет нам, насколько мы правы, или ошиблись.

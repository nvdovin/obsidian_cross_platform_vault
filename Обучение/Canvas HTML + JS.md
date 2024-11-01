---
tags:
  - JS
---
# С чего начать
## База
Начинается все с того, что мы размещаем тег **canvas**, задаем ему id в html разметке, после этого импортируем туда скрипт и начинаем кодить.

После того, как тег был размещен в html разметке, его нужно получить в JS, используя `doument.getElementById("canvas_id");`

```js
// Обозначаем сам канвас
const canvas = doument.getElementById("canvas_id");
```

Здесь же спикер предлагает задать размеры окна, которые предоставляет канвас. Спикер предлагает заполнить все окно этим канвасом.
```js
// Получаем текущие размеры окна
let window_height = window.innerHeight;
let window_width = window.innerWidth;

// Применяем их к нашему canvas
canvas.height = window_height;
canvas.width = window_width;

// Красим фон в какой-то цвет
canvas.style.background = "color";
```

## Строительство элементов на канвасе
Для этого нужно для начала задать контекст для канваса. Это делается таким образом:
```js
// Задаем контекст
const context = canvas.getContext("2d");

// Цвед для фигур
context.fillStyle = "red";

context.lineWidth = 10; // ширина линии

// Рисуем квадрат
let context.fillRect(xPos, yPos, width, heigth);

context.beginPath(); // Видимо, это то, без чего не может что-либо быть построено

// Задать цвет тому, что нарисовано через stroke
context.strokeStyle = "blue";

// Рисуется круг, где xPos, yPos, R, start_angle_rads, end_angle_rads, fill(true/false)
let circle = context.acr(200, 200, 50, 0, Math.PI / 2, false);

context.stroke(); // Это то, что позволяет рисоать круг
context.closePath()
```

# Классы с объектами
Создается класс, конструктор к нему, и несколько методов, среди которых будет метод, который будет рисовать круг на канвасе.
Например, это может выглядеть так:
```js
class Circle {
	constructor(xPos, yPos, radius, color) {
		this.xPos = xPos;
		this.yPos = yPos;
		this.radius = radius;
		this.color = color;
	};

	draw(context) {
		context.beginPath();
		context.strokeStyle = this.color;
		context.arc(this.xPos, this.yPos, this.radius, 0, Math.PI * 2, false);
		context.stroke();
		context.closePath();
	};
};
```

# Работа с текстом
Для того, чтобы разместить текст, нужно воспользоваться методом, указанным ниже
```js
context.fillText(text, x, y); // разместить текст
context.textAlign = "center"; // Разместить текс посередине
context.textBaseline = "middle"; // Также сделать текст еще более поцентру
context.font = "Times New Roman"; // Выбрать шрифт
```

# Движение объектов на холсте
## Суть движения
Судя по всему, движение объектов, это не самая простая штука. Все дело в том, что чтобы запустить анимацию необходимо запустить функцию, которая называется `requestAnimationFrame()`
Это нечто, насколько я сейчас понимаю, постоянно запрашивает обновления холста. Но на вход она принимает какую-то функцию.
Спикер предложил сделать это так:
```js
let updateCircle = function() {
	requestAnimationFrame(updateCircle);
	c1.update(); // описал ниже, что это такое
};
```
То есть рекурсивно запустил ее саму на себя. При этом он получает на выходе 60 FPS.

## Обновление в c1.update()
Это ничто иное, как метод объекта круга, в котором мы задаем новые координаты для нашего объекта.

## Очистка холста
Для того, чтобы очистить холст, нам нужно вызвать одну из функций, которая очищает экран. Спикери



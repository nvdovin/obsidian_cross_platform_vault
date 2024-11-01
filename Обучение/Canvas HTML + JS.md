---
tags:
  - JS
---
# С чего начать
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

# Классы с объектами и динамической темой
## Создание класса
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


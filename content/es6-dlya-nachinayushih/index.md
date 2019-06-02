---
title: "ES6 для начинающих"
description: "В этой статье я расскажу кор-фичи, которые ввели в ES6. Статья будет полезна, если вы новичок или изучаете фронтенд-фреймворки. let это такой же var, только со скоупом(область видимости). let…"
date: "2018-04-25T09:14:00.564Z"
categories: 
  - Перевод
  - JavaScript
  - ES6
  - Front End Development
  - Для Начинающих

published: true
canonicalLink: https://medium.com/@badiullin.nail/es6-%D0%B4%D0%BB%D1%8F-%D0%BD%D0%B0%D1%87%D0%B8%D0%BD%D0%B0%D1%8E%D1%89%D0%B8%D1%85-73369fdbd2f6
---

Перевод

[**ES6 for beginners**  
_ES6 tutorial for beginners with example. Learn features like let, const, arrow functions, for..of, maps, sets and much…_codeburst.io](https://codeburst.io/es6-tutorial-for-beginners-5f3c4e7960be "https://codeburst.io/es6-tutorial-for-beginners-5f3c4e7960be")[](https://codeburst.io/es6-tutorial-for-beginners-5f3c4e7960be)

![](./asset-1.png)

В этой статье я расскажу кор-фичи, которые ввели в ES6. Статья будет полезна, если вы новичок или изучаете фронтенд-фреймворки.

Содержание:

-   let и const
-   Стрелочные функции
-   Параметры по умолчанию
-   for of …
-   Spread атрибуты
-   Мапы
-   Сеты
-   Статические методы
-   Геттеры и сеттеры

#### let

let это такой же var, только со скоупом(область видимости). let определен (доступен) только в указанном блоке.

```
if (true) {
 let a = 40;
 console.log(a); //40
}
console.log(a); // получим андеф
```

В примере выше переменная **a** определена внутри выражения **if** и недоступна вне него.

Другой пример:

```
let a = 50;
let b = 100;
if (true) {
 let a = 60;
 var c = 10;
 console.log(a/c); // 6
 console.log(b/c); // 10
}
console.log(c); // 10
console.log(a); // 50
```

#### const

**Const** используется для определения фиксированного значения переменной.

```
const a = 50;
a = 60; // Ошибка, нельзя менять значение const переменной

const b = "Constant variable";
b = "Assigning new value"; // Ошибка
```

Посмотрим другой пример:

```
const LANGUAGES = ['Js', 'Ruby', 'Python', 'Go'];

LANGUAGES = "Javascript"; // Ошибка

LANGUAGES.push('Java'); // Отрабатывает
console.log(LANGUAGES); // ['Js', 'Ruby', 'Python', 'Go', 'Java']
```

Это может вас слегка запутать.

**Пояснение**: когда вы определяете **const **— JavaScript ссылается на адрес значения переменной. В нашем примере переменная **LANGUAGES** ссылается на участок памяти, связанный с массивом. Поэтому вы не можете изменить ссылку переменной на другой участок памяти — программа связала эту переменную только с этим массивом.

#### Стрелочные функции

В стандарте ES6 немного изменился синтаксис функций.

```
// Old Syntax
function oldOne() {
 console.log("Hello World..!");
}

// New Syntax

var newOne = () => {
 console.log("Hello World..!");
}
```

Новый синтаксис может показаться запутанным, но я объясню в чем цимес.

Есть две части синтаксиса:

-   **var newOne = ()**
-   **\=> {}**

Первая часть просто объявляет переменную и присваивает ей функцию. Она просто говорит, что вот эта переменная — функция.

Вторая часть объявляет тело функции. Да, именно стрелка и фигурные скобки — тело функции.

Еще пример:

```
let NewOneWithParameters = (a, b) => {
 console.log(a+b); // 30
}
NewOneWithParameters(10, 20);
```

#### Параметры по умолчанию

Если вы знакомы с Питоном или Рубями, то для вас параметры по умолчанию не являются чем-то новым.

Параметры по умолчанию указываются тогда, когда вы объявляете функцию. Их значения можно изменить при вызове функции.

```
let Func = (a, b = 10) => {
 return a + b; 
}
Func(20); // 20 + 10 = 30
```

В примере выше мы передаем только один параметр, второй функция подставляет за нас и выполняется.

```
let NotWorkingFunction = (a = 10, b) => {
 return a + b;
}
NotWorkingFunction(20); // Не прокатит
```

Когда вы вызываете функцию с параметрами, то они присваиваются по порядку: первое значение к первому параметру, второе ко второму и т.д.

#### for of …

**for of** очень похож на **for in** с небольшой модификацией.

**for of** итерируется по списку элементов, например, массива и возвращает элементы( не индексы) один за другим.

```
let arr = [2,3,4,1];
for (let value of arr) {
 console.log(value);
}

Output:
2
3
4
1
```

Обратите внимание на то, что переменная **value** выводит каждый элемент массива, а не индексы.

Еще пример:

```
let string = "Javascript";
for (let char of string) {
 console.log(char);
}

Output:
J
a
v
a
s
c
r
i
p
t
```

#### Spread атрибуты

**Spread атрибуты** помогают расширить выражение, как подсказывает нам название. Простыми словами, эта штука конвертирует список элементов в массив и наоборот.

Пример без таких атрибутов:

```
let SumElements = (arr) => {
 console.log(arr); // [10, 20, 40, 60, 90]

let sum = 0;
 for (let element of arr) {
  sum += element;
 }
 console.log(sum); // 220. 
}

SumElements([10, 20, 40, 60, 90]);
```

Пример выше достаточно прост. Мы объявляем функцию, которая принимает массив как параметр и возвращает сумму его элементов. Все просто.

Давайте посмотрим на тот же пример, но с применением **spread атрибутов**

```
let SumElements = (...arr) => {
 console.log(arr); // [10, 20, 40, 60, 90]

let sum = 0;
 for (let element of arr) {
  sum += element;
 }
 console.log(sum); // 220. 
}

SumElements(10, 20, 40, 60, 90); // Передаем не массив, а значения элементов
```

В примере выше **spread атрибут** переводит список элементов в массив.

Еще пример:

```
Math.max(10, 20, 60, 100, 50, 200); // возвращает 200.
```

**Math.max** — простой метод, возвращающий максимальный элемент из заданного списка. Он не принимает массив.

```
let arr = [10, 20, 60];
Math.max(arr); // Ошибка, нельзя передать массив

let arr = [10, 20, 60];
Math.max(...arr); // 60
```

#### Мапы

“Мап” содержит пары “ключ-значение”. Он схож с массивом, но мы можем задать собственный индекс. И индексы в “мапе” уникальны.

```
var NewMap = new Map();
NewMap.set('name', 'John'); 
NewMap.set('id', 2345796);
NewMap.set('interest', ['js', 'ruby', 'python']);

NewMap.get('name'); // John
NewMap.get('id'); // 2345796
NewMap.get('interest'); // ['js', 'ruby', 'python']
```

Думаю, пример говорит сам за себя.

Другая интересная особенность “мапов” — все индексы уникальны. И мы можем использовать любое значение в качестве ключа или значения.

```
var map = new Map();
map.set('name', 'John');
map.set('name', 'Andy');
map.set(1, 'number one');
map.set(NaN, 'No value');

map.get('name'); // Andy. Произошла замена
map.get(1); // number one
map.get(NaN); // No value
```

Другие полезные методы “мапов”:

```
var map = new Map();
map.set('name', 'John');
map.set('id', 10);

map.size; // 2. Возвращает размер мапа

map.keys(); // выведет только ключи 
map.values(); // выведет только значения

for (let key of map.keys()) {
 console.log(key);
}

Output:
name
id
```

#### Сеты

“Сеты” используются для хранения уникальных значений любого типа. Все просто.

Пример

```
var sets = new Set();
sets.add('a');
sets.add('b');
sets.add('a'); //Добавляем дубликат

for (let element of sets) {
 console.log(element);
}

Output:
a
b
```

Обратите внимание на то, что дублирующиеся значения не вывелись. Только уникальные.   
Также, важно заметить, что “сеты” — итерируемые объекты. Чтобы вывести элементы необходимо пройтись по “сету”.

#### Статические методы

Большинство из вас уже слышали о статических методах. Они были представлены в ES6. И их достаточно легко использовать.

Пример:

```
class Example {
 static Callme() {
 console.log("Static method");
 }
}
Example.Callme();

Output:
Static method
```

Обратите внимание, что я не использовал ключевое слово function внутри класса.

И я могу вызывать функцию без создания инстанса класса.

#### Геттеры и сеттеры

Геттеры и Сеттеры одна из самых полезных фич, представленных в ES6. Если вы используете классы в JS, то они могут пригодиться.

Пример без геттеров и сеттеров:

```
class People {

constructor(name) {
      this.name = name;
    }
    getName() {
      return this.name;
    }
    setName(name) {
      this.name = name;
    }
}

let person = new People("Jon Snow");
console.log(person.getName());
person.setName("Dany");
console.log(person.getName());

Output:
Jon Snow
Dany
```

Пример говорит сам за себя. У нас есть две функции, которые помогают установить и получить имя человека.

Пример с геттерами и сеттерами:

```
class People {

constructor(name) {
      this.name = name;
    }
    get Name() {
      return this.name;
    }
    set Name(name) {
      this.name = name;
    }
}

let person = new People("Jon Snow");
console.log(person.Name);
person.Name = "Dany";
console.log(person.Name);
```

В примере выше вы видите две функции внутри класса People с гет и сет пропами. Гет используется для получения значения переменной, а сет — для установления.

Обе функции вызываются без скобок. Как переменная.
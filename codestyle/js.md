# Оформление JavaScript кода

Часть правил оформления будет проверена автоматически,  
на остальные обратят внимание менторы во время ручной проверки.

Ознакомиться с механизмом вы можете на демонстрационной задаче:  
https://github.com/urfu-2018/demo-task-1

- [Правила для автоматической проверки](#Правила-для-автоматической-проверки)
- [Не пишите код впрок](#Не-пишите-код-впрок)
- [Не повторяйтесь](#Не-повторяйтесь)
- [Пишите проще](#Пишите-проще)
- [Называйте переменные понятно](#Называйте-переменные-понятно)

## Правила для автоматической проверки

Когда вы отправляет пулл-реквест, ваш код автоматически проходит проверку  
на соответствие этим правилам при помощи специального анализатора кода –  [eslint](http://eslint.org/docs/rules/).

В случае, если проверка не прошла внизу пулла вы увидите:
<img width="769" alt="ci-fail" src="https://cloud.githubusercontent.com/assets/4534405/19022765/ead12c6c-88f8-11e6-9500-3dc6e27b15d5.png">

Обратите внимание на ссылку «details», перейдя по ней, вы сможет найти ошибки:

<img width="500" alt="ci-eslint-log" src="https://cloud.githubusercontent.com/assets/4534405/19022790/760bb7e8-88f9-11e6-8f2d-e90c2e6ba2d1.png">

ESlint подскажет в каких файлах и на какой строке произошла ошибка,  
а так же какое именно правило было нарушено. В данном примере – «[no-unused-let](http://eslint.org/docs/rules/no-unused-lets)».  

Весь список правил можно изучить по ссылке: http://eslint.org/docs/rules

Если код удовлетворяет всем правилам, вы увидите:

<img width="771" alt="ci-success" src="https://cloud.githubusercontent.com/assets/4534405/19022864/d7fc0088-88fa-11e6-8142-38eded04077f.png">

Вы можете не ждать автоматической проверки и всегда проверить код вручную,  
выполнив локально команду `npm install && npm run lint`

## Не пишите код впрок

Следуйте приниципу [YAGNI](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it) (You ain't gonna need it) – не пишите код, который не понадобится вам для решения задачи. Если все проверки и тесты пройдены, значит кода уже достаточно – потратьте время на рефакторинг.

__Плохо:__

```js
// My awesome math utils
function sum(numbers) {}
function average(numbers) {}
function median(numbers) {}

sum([1, 2, 3]);
// 6
```

__Хорошо:__
```js
function sum(numbers) {}

sum([1, 2, 3]);
// 6
```

## Не повторяйтесь

Следуйте приниципу [DRY](https://ru.wikipedia.org/wiki/Don%E2%80%99t_repeat_yourself) (Don’t repeat yourself) – не пишите похожий код несколько раз,   
старайтесь его переиспользовать.

__Плохо:__
```js
let averageRating = ratings
    .reduce((sum, rating) => sum + rating, 0) / ratings.length;

let averageGrade = grades
    .reduce((sum, grade) => sum + grade, 0) / grades.length;
```

__Хорошо:__
```js
function getAverageOf(numbers) {}

let averageRating = getAverageOf(ratings);
let averageGrade = getAverageOf(grades);
```

## Пишите проще

Следуйте приниципу [KISS](http://people.apache.org/~fhanik/kiss.html) (Keep it short and simple) – пишите проще   
и по полной используйте все возможности языка.

__Плохо:__
```js
let numbers = [1, 4, 5, 2, 3];

// Сортируем числа
// TODO: оптимизировать – может быть быструю сортировку?
for (let i = 0; i < numbers.length; i++) {
    for (let j = 0; j < numbers.length; j++) {
        if (numbers[j] > numbers[j+1]) {
            const greatest = numbers[j];

            numbers[j] = numbers[j+1];
            numbers[j+1] = greatest;
        }
    }   
}
```

__Хорошо:__
```js
let numbers = [1, 4, 5, 2, 3];

numbers.sort()
```

## Называйте переменные понятно

1. Используйте [camelCase](https://en.wikipedia.org/wiki/CamelCase)

  __Плохо:__
  ```js
  let apples_count = 5;
  let Language = 'ru';
  ```

  __Хорошо:__
  ```js
  let applesCount = 5;
  let language = 'ru';
  ```

2. Используйте только английские слова, не используйте транслит

  __Плохо:__
  ```js
  let ssilka = 'http://esling.org/';
  let ссылка = 'http://esling.org/';
  ```

  __Хорошо:__
  ```js
  let link = 'http://esling.org/';
  ```

3. Вкладывайте смысл в название – оно должно быть однозначным и понятным

  __Плохо:__
  ```js
  let a, b; // Не несут смысла
  let list; // Слишком абстрактно – список чего?
  ```

  __Хорошо:__
  ```js
  let overallPrice, publishDate;
  let grocceryList;
  ```

  Допустимо использовать `i`, `j` в качестве итераторов цикла `for (let i = 0; i < 2; i++) {}`,  
  и `a`, `b` – в функциях сортировки `grocceryList.sort(function (a, b) {})`

4. Логические перменные начинайте с модальных глаголов

  __Плохо:__
  ```js
  let accessToPublish
  let visible;
  ```

  __Хорошо:__
  ```js
  let canPublish
  let isVisible;
  ```

5. Не используйте сокращения и не пишите избыточные имена

  __Плохо:__
  ```js
  let btn;
  let dateOfFirstPublication;
  let postsCollection;
  ```

  __Хорошо:__
  ```js
  let button;
  let publishDate;
  let posts;
  ```

6. Объявляйте переменные максимально близко к месту использования

  __Плохо:__
  ```js
  let hasAccess = hasAccess(); // Далеко от места использования
  let comments = getComments();
  let overalRaiting = 0;

  for (let i = 0; i < comments.length; i++) {
      overallRating += comments[i].rating;
  }

  if (hasAccess) {
      show(overallRating);
  }
  ```

  __Хорошо:__
  ```js
  let comments = getComments();
  let overalRaiting = 0;

  for (let i = 0; i < comments.length; i++) {
      overallRating += comments[i].rating;
  }

  let hasAccess = hasAccess();
  
  if (hasAccess) {
      show(overallRating);
  }
  ```

7. Для именования функций используйте глаголы

  __Плохо:__
  ```js
  function length() {}
  function title(name) {}
  function visible() {}
  ```

  __Хорошо:__
  ```js
  function getLength() {}
  function setTitle(name) {}
  function isVisible() {}
  ```

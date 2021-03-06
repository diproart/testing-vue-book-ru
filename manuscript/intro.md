# Что такое тестирование и почему мы должны это делать?

*Перевод статьи [Alex Jover Morales](https://github.com/alexjoverm): [What’s testing and why should we do it?](https://vueschool.io/articles/vuejs-tutorials/what-is-testing-and-why-should-we-do-it/).*

Тестирование в области разработки программного обеспечения — это процесс оценки того, что все части приложения ведут себя так, как ожидалось.

Тесты выполняют проверки программного обеспечения, проверяя, что полученный результат соответствует спецификациям, учитывая разные входные данные. Каждая из этих проверок называется _тестовым сценариям_ (test case). В рабочем процессе agile каждая пользовательская история должна иметь набор тестовых сценариев. Простой пример:

A> US-01: создание компонента ввода валюты
A>
A> Сценарии тестирования:
A>
A> – TC-01: он должен принимать только числа
A>
A> 1. Введите число «2». Ожидается: все должно быть в порядке
A> 2. Введите символ «a». Ожидается: должно отображаться сообщение «Разрешены только числа»
A>
A> – TC02: оно не может быть пустым
A>
A> ...

В тестовых сценариях проверяются требования и характеристики конкретной функциональной возможности (функционала). Они могут предоставлять определённые детали или шаги, чтобы их можно было воспроизвести.

Скорее всего, если вы читаете эту статью, вы знаете, что такое тестирование и TDD, но если вы новичок в тестировании, у вас может возникнуть вопрос, который был в своё время у всех нас:

**Не занимает ли тестирование слишком много времени? Нужно ли мне тестировать всё?**

В этой статье мы поговорим о плюсах и минусах тестирования, о типах тестирования, и что ещё есть кроме тестирования для обеспечения качества приложения.

## Зачем писать тесты?

Говоря о том, зачем нужно тестирование, можно упомянуть следующие его преимущества:

* **Экономит деньги**: без надлежащего тестирования количество времени и ресурсов, необходимых для поддержания продукта в долгосрочной перспективе, намного больше, чем инвестиции в тестирование, не говоря уже о том, что со временем что-то сломается.
* Обеспечивает **безопасность кода при командной работе**: приложение часто создаётся командами. Разные люди изменяют один и тот же фрагмент кода с течением времени. Наличие тестов делают этот процесс более безопасным, поскольку никто не сломает что-то, не узнав об этом. Это также относится и к будущему, тесты обеспечивает безопасность кода, когда вы вернётесь через год или два для внесения изменений.
* Помогает в создании **лучшей архитектуры**: когда часть приложения трудно тестировать, это обычно происходит из-за того, что оно тесно связано с другими частями или функциональность вашего приложения слишком сложна. При их тестировании вам нужно будет сделать их слабосвязанными, применить делегирование и паттерны проектирования, чтобы сделать приложение максимально простым и тестируемым.
* Улучшает **качество кода**: ваш продукт менее подвержен сбоям в работе поскольку тесты помогает написать более надёжный и хороший код, который менее подвержен ошибкам.
* Делает **рефакторинг простым и безопасным**: создание программного обеспечения — это итеративный процесс. Требования меняются с течением времени, следовательно, меняется и функциональность. Наличие хорошего тестового покрытия позволяет вам модифицировать определённый код, проверяя, что тесты все ещё успешно проходят. Если это не так, вы делаете правки в код таким образом, чтобы тесты прошли.

Надеюсь, что на данном этапе вы убедились, почему тестирование полезно для вас, вашего приложения и компании, в которой вы работаете.

## Типы тестов

Тесты делятся на разные типы. Каждый тип теста имеет свою цель (назначение) и область действия, и вам следует знать об этом. Каждый разработчик в какой-то момент пишет тест, который тестирует то, чего он не должен.

У нас есть три основных типа тестов:

![Пирамида тестирования](images/pyramid_1.png)

* **End-to-end-тесты** (сокращённо — E2E) или сквозные тесты, как их называют при переводе: тестируют систему в целом, эмулируя реальную пользовательскую среду. В интернете это тесты, запущенные в браузере, имитирующие щелчки мышью и нажатия клавиш. В общем, набор таких тестов не должен быть большим, так как они дороги для обслуживания и могут легко устареть из-за тестирования системы в целом.
* **Интеграционные тесты**: цель данных тестов состоит в том, чтобы убедиться, что несколько зависимых друг от друга модулей кода работают вместе, и их взаимодействие работает должным образом.
* **Модульные тесты**: они тестируют определённую функциональность изолированно. Их легче всего создавать и обслуживать, поэтому большинство тестовых наборов — это модульные тесты.

Пирамида описывает баланс различных типов тестов. Нижняя часть — это самые быстрые, простые и самые изолированные тесты, а верхние — самые дорогие, самые медленные и охватывают всё приложение в целом.

Интеграционный слой можно даже разделить на ещё большее количество слоёв:

![Пирамида тестирования с детально показанным интеграционным слоем](images/pyramid_2.png)

Хотя есть несколько разногласий по поводу количества типов тестов и их имён, наиболее распространёнными являются тесты компонентов и API. Это всего лишь особые типы интеграционных тестов. В частности, тесты компонентов — это тесты, которые мы пишем на стороне фронтенда при тестировании приложения на Vue.js.

## Статический анализ

Тесты — не единственный инструмент для обеспечения качества кода. В наше время у JavaScript также есть статическая типизация и инструменты для проверки кода (*linters*, далее — линтеры). Они выполняют статический анализ вашего кода для поиска несоответствий выбранному стилю кода, неправильного использования языка, ненадлежащей и плохой практики, ошибок в контракте данных и многое другое.

I> Контракт данных — формат данных, который будет использоваться некоторой частью приложения, например функцией. Обычно под этим понимается в каком виде будут представлены данные, например, тип входных и возвращаемых данных.

**Статическая типизация** делает ваш код более безопасным на основе каждого контракта. Такие инструменты, как TypeScript или Flow, позволяют определять переменные, параметры и типы возвращаемых значений. Они гарантируют, что ваши классы, функции и методы имеют определённую структуру, а остальная часть вашего кода хорошо работает в соответствии с этим. Многие компании, принявшие статическую типизацию, сразу же поймали несколько ошибок.

Давайте сравним типизированную версию и не типизированную версию функции `sum`:

{lang=javascript}
    // Нетипизированная функция
    function sum(a, b) {
      return a + b;
    }

    // Типизированная функция
    function sum(a: number, b: number) : number {
      return a + b;
    }

Версия функции без указания типов не мешает нам вызывает её со строчными входными данными, в результате возвращая нам конкатенацию строк. Например, вызов `sum('1', '2')` возвращает `'12'`. Однако, если мы используем статическую типизацию, мы получаем ошибку, такую как `Argument of type '"1"' is not assignable to parameter of type 'number'` (*Аргумент этого типа '"1"' не может быть присвоен параметру типа 'number'*), и эта ошибка типизации предотвращает нас во время компиляции совершить вызов функции, который вернёт неверный результат, поскольку мы ожидаем сложение чисел, а не конкатенацию строк.

**Линтеры** — это специальные программы, цель которых анализ и проверка различных аспектов кода во время компиляции. JavaScript не имеет преимуществ компилятора, поэтому подвержен ошибкам во время выполнения по сравнению с другими языками, где об ошибках будет сообщено на стадии компиляции. ESLint стал линетром де-факто в JavaScript, а TSLint — в сообществе TypeScript.

Линтер пытается заполнить пробел, предоставляя правила проверки ошибок синтаксиса, стиля кода и неправильного использования (проблемных паттернов). В результате он уменьшает количество ошибок и повышает качество и корректность вашего кода.

В качестве примера, если вы используете правило [no-var](https://eslint.org/docs/rules/no-var) в ESLint и напишите следующий код:

{lang=javascript}
    var greet = 'Эй, Китти';

Вы получите ошибку `Unexpected var, используйте let или const вместо (no-var)` (*Неожиданный var, используйте let или const вместо него (no-var)*).

В пирамиде статический анализ ещё точнее определён и проверяется быстрее (почти в режиме реального времени), чем модульные тесты, что делает его основой пирамиды:

![Итоговая пирамида тестирования, включающая статический анализ и линтеры](images/pyramid_1.png)

Эта [статья](https://vueschool.io/articles/vuejs-tutorials/what-is-testing-and-why-should-we-do-it/) является первой частью серии [Тестируй как профи в JavaScript](https://vueschool.io/articles/series/testing-like-a-pro-in-javascript/). В рамках этой книги она представлена, чтобы дать вам общее представление о тестировании в целом.

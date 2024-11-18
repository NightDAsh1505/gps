# Розробка додатку для візуалізації вимірювань GPS

Мета роботи

Розробити додаток, який зчитує дані з емульованої вимірювальної частини GPS, наданої у вигляді Docker image, та відображає положення об'єкта і супутників на графіку в декартових координатах.

Завантаження та запуск емулятора вимірювальної частини GPS/

Завантажуємо Docker image з Docker Hub і запускаємо Docker контейнер:

![01](scr/01.jpg)

Відображення супутників і об'єкта на графіку:

![02](scr/02.jpg)

Підключення до WebSocket сервера:

![03](scr/03.jpg)
Ця частина підключається до сервера через WebSocket і відкриває з'єднання. Після успішного підключення виводиться повідомлення в консоль.

Отримання даних від WebSocket:

![04](scr/04.jpg)
Ця функція обробляє повідомлення від сервера. Вона отримує дані про супутники, розраховує затримку сигналу і відстань до об'єкта, а потім обчислює його положення (якщо є три супутники) та викликає функцію для оновлення графіку.

Обчислення положення об'єкта:

![05](scr/05.jpg)
Ця функція використовує координати супутників і відстані для обчислення координат об'єкта за допомогою методу трилатерації.

Ця функція малює супутники і об'єкт на графіку за допомогою бібліотеки Plotly. Маркери для супутників і об'єкта відображаються різними кольорами, і графік оновлюється щоразу після отримання нових даних:

![06](scr/06.jpg)

Функція applySettings для оновлення параметрів:

![07](scr/07.jpg)

Ця функція зчитує значення введених користувачем параметрів із полів форми (ID satVelocity та oobjVelocity). Потім вона відправляє ці дані на сервер через запит fetch до ендпоінта /config. Відправляються дані у форматі JSON з новими параметрами для швидкості супутника та об'єкта.

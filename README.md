<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Пример HTML-страницы</title>
</head>
<body>
    <header>
        <h1>Добро пожаловать на мою первую HTML-страницу!</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#">Главная</a></li>
            <li><a href="#">О нас</a></li>
            <li><a href="#">Контакты</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <h2>О нас</h2>
            <p>Мы - ваша компания, занимающаяся чем-то интересным.</p>
        </section>
        <section>
            <h2>Таймер</h2>
            <p field="tn_text_1">00</p>
            <p field="tn_text_2">00</p>
            <p field="tn_text_3">00</p>
        </section>
        <section>
            <h2>Главная</h2>
            <p>Добро пожаловать на нашу великолепную главную страницу!</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Моя компания. Все права защищены.</p>
    </footer>
</body>
    <script>
    $( document ).ready(function() {
     function addLeadingZero(number) {
            // Функция добавляет 0 перед числами, состоящими из одной цифры
        return number < 10 ? "0" + number : number;
    }
     function Timer(){
    //Описываем строку со таймером     
        var currentTime = new Date();
            // Устанавливаем конечное время дня (23:59:59)
        var endOfDay = new Date(currentTime.getFullYear(), currentTime.getMonth(), currentTime.getDate(), 23, 59, 59);
            // Если текущее время больше или равно конечному времени дня, переходим к следующему дню
        if (currentTime >= endOfDay) {
            endOfDay.setDate(endOfDay.getDate() + 1); // Переход к следующему дню
        }
            // Вычисляем оставшееся время до конечного времени дня
        var timeDiff = endOfDay - currentTime;
            // Преобразуем разницу в миллисекундах в часы, минуты и секунды
        var hours = Math.floor((timeDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        var minutes = Math.floor((timeDiff % (1000 * 60 * 60)) / (1000 * 60));
        var seconds = Math.floor((timeDiff % (1000 * 60)) / 1000);
        hours = addLeadingZero(hours);
        minutes = addLeadingZero(minutes);
        seconds = addLeadingZero(seconds);
        $('[field="tn_text_1"]').text(hours);
        $('[field="tn_text_2"]').text(minutes);
        $('[field="tn_text_3"]').text(seconds);
        };
        Timer();
        var timeinterval = setInterval(Timer,500);
    });   
    </script>
</html>


<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Пример HTML-страницы с таймером</title>
    <!-- Подключение библиотеки jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
</head>
    <style>
    body { 
      background-color: rgb(255, 255, 255); 
      font-size: 30px;
      text-align: center;
    }
    #button {
      width: 200px;
      height: 200px;
      background-color: rgb(0, 0, 0);
      border-radius: 100px;
      margin: 0 auto;
      line-height: 200px;
      user-select: none;
      margin-top: 100px;
    }
    #score {
      margin-top: 50px;
      font-size: 60px;
      font-weight: bold;
      color: rgb(255, 255, 255);
    }
  </style>
  <div id="score">0</div>
  <div id="button">CLICK ME</div>
  <script>
    let counter = 0;
    document.getElementById('button').onclick = () => {
      counter = counter + 1;
      document.getElementById('score').innerText = counter;
    };
  </script>
<body>
    <header>
        <h1 id="dynamic-text" field="tn_text_1706274470730">Добро пожаловать на мою первую HTML-страницу!</h1>
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
            <p>Мы - компания, занимающаяся чем-то интересным.</p>
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
            <div id="welcome-message"></div>
            <!-- Ваш jQuery-скрипт начинается здесь -->
            <script>
                $(document).ready(function() {
                    function addLeadingZero(number) {
                        return number < 10 ? "0" + number : number;
                    }
                    function Timer() {
                        var currentTime = new Date();
                        var endOfDay = new Date(currentTime.getFullYear(), currentTime.getMonth(), currentTime.getDate(), 23, 59, 59);
                        if (currentTime >= endOfDay) {
                            endOfDay.setDate(endOfDay.getDate() + 1);
                        }
                        var timeDiff = endOfDay - currentTime;
                        var hours = Math.floor((timeDiff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                        var minutes = Math.floor((timeDiff % (1000 * 60 * 60)) / (1000 * 60));
                        var seconds = Math.floor((timeDiff % (1000 * 60)) / 1000);
                        hours = addLeadingZero(hours);
                        minutes = addLeadingZero(minutes);
                        seconds = addLeadingZero(seconds);
                        $('[field="tn_text_1"]').text(hours);
                        $('[field="tn_text_2"]').text(minutes);
                        $('[field="tn_text_3"]').text(seconds);
                    }
                    Timer();
                    var timeinterval = setInterval(Timer, 500);
                });
            </script>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 Компания. Все права защищены.</p>
    </footer>
</body>
</html>

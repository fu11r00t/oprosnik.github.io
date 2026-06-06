<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>опрос</title>
    <style>
        /* ---------------------------
           СТИЛИ (CSS) — это как наряд для страницы
           Здесь мы рассказываем, как должны выглядеть кнопки, фон, текст.
           Ребёнок: представь, что это "одежда" для веб-страницы.
        --------------------------- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            /* Градиентный фон — плавный переход цветов */
            background: linear-gradient(145deg, #f9e7b3 0%, #f5b7a8 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', 'Comic Neue', 'Comic Neue', 'Comic Sans MS', 'Chalkboard SE', cursive, sans-serif;
            padding: 20px;
            /* Анимация для появления фона — не обязательно, но приятно */
            animation: gentleFade 1s ease-out;
        }

        @keyframes gentleFade {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Белая карточка с опросом */
        .survey-card {
            max-width: 650px;
            width: 100%;
            background-color: #fffef7;
            border-radius: 72px 48px 72px 48px;
            /* Немного неправильная форма для весёлого настроения */
            box-shadow: 0 25px 40px rgba(0, 0, 0, 0.2), 0 0 0 12px #ffe6b3, 0 0 0 16px #ffb882;
            padding: 2rem 2rem 2.8rem;
            transition: all 0.3s ease;
            text-align: center;
        }

        h1 {
            font-size: 2.5rem;
            color: #c24d2c;
            text-shadow: 3px 3px 0 #ffd966;
            letter-spacing: 2px;
            margin-bottom: 0.5rem;
        }

        .subhead {
            font-size: 1.2rem;
            background: #ffecb3;
            display: inline-block;
            padding: 0.4rem 1.2rem;
            border-radius: 100px;
            margin-bottom: 1.8rem;
            color: #a5411e;
            font-weight: bold;
        }

        /* Стили для вопросов (блоков) */
        .question {
            background: #fff1dd;
            margin: 1.5rem 0;
            padding: 1.2rem;
            border-radius: 48px;
            box-shadow: 0 8px 0 #e7c8a3;
            transition: transform 0.2s;
        }

        .question:hover {
            transform: translateY(-4px);
        }

        .question p {
            font-weight: bold;
            font-size: 1.3rem;
            margin-bottom: 0.8rem;
            color: #74451e;
        }

        /* Контейнер для вариантов ответа (кнопок или радио) */
        .options {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 12px;
            margin-top: 12px;
        }

        /* Стиль каждой кнопки-варианта (стилизованные радио-кнопки) */
        .option-btn {
            background: #ffe2b5;
            border: 3px solid #e0a46b;
            padding: 10px 20px;
            border-radius: 60px;
            font-size: 1rem;
            font-weight: bold;
            font-family: inherit;
            color: #5e2e12;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 3px 0 #b97f48;
        }

        .option-btn:hover {
            background: #ffce92;
            transform: scale(0.97);
            box-shadow: 0 1px 0 #b97f48;
        }

        /* Активная (выбранная) кнопка — зелёная звёздочка! */
        .option-btn.active {
            background: #b0d9b1;
            border-color: #2d6a4f;
            color: #1c4d2d;
            box-shadow: 0 0 0 2px #f9c74f, 0 3px 0 #2d6a4f;
        }

        /* Кнопка отправки/завершения */
        .submit-btn {
            background: #ff9f4a;
            border: none;
            font-size: 1.8rem;
            font-weight: bold;
            font-family: inherit;
            padding: 14px 32px;
            margin-top: 30px;
            border-radius: 48px;
            color: white;
            text-shadow: 2px 2px 0 #b45f2b;
            cursor: pointer;
            box-shadow: 0 8px 0 #9b4a1a;
            transition: 0.07s linear;
            width: 80%;
        }

        .submit-btn:active {
            transform: translateY(4px);
            box-shadow: 0 4px 0 #9b4a1a;
        }

        /* Секция с финальным поздравлением (изначально скрыта) */
        .congrats {
            background: #d9e3b3;
            margin-top: 25px;
            padding: 1.8rem;
            border-radius: 60px 20px 60px 20px;
            font-size: 1.4rem;
            font-weight: bold;
            color: #3c2a1f;
            display: none;
            border: 5px dashed #f7b05e;
            animation: bouncePop 0.6s cubic-bezier(0.34, 1.2, 0.64, 1);
        }

        @keyframes bouncePop {
            0% { transform: scale(0.8); opacity: 0; }
            80% { transform: scale(1.05); }
            100% { transform: scale(1); opacity: 1; }
        }

        .congrats span {
            display: inline-block;
            font-size: 3rem;
            margin-bottom: 10px;
        }

        .footer-note {
            font-size: 0.85rem;
            margin-top: 25px;
            color: #ba7a3a;
            background: #fff0cf;
            display: inline-block;
            padding: 6px 16px;
            border-radius: 60px;
        }

        /* Полезные пояснения прямо на странице (внизу) */
        .explanation {
            background: #fff5e6;
            margin-top: 35px;
            padding: 20px;
            border-radius: 40px;
            text-align: left;
            font-size: 0.95rem;
            color: #5c3b1c;
            border-left: 15px solid #f3b33d;
        }

        .explanation h3 {
            margin-bottom: 12px;
            color: #d25f1a;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .explanation p, .explanation li {
            margin: 8px 0;
            line-height: 1.4;
        }

        .explanation ul {
            padding-left: 25px;
        }

        hr {
            margin: 10px 0;
            border: 1px dotted #ffcf9a;
        }
    </style>
</head>
<body>

<div class="survey-card">
    <h1>📋 ОЧ ВАЖНЫЙ ОПРОС 🤪</h1>
    <div class="subhead">⭐ это важный опрос - пройдите его и получите приз!⭐</div>

    <!-- Блок с вопросами. Всего 4 забавных, бессмысленных вопроса -->
    <div id="questionsArea">
        <!-- Вопрос 1: Любимый цвет носков -->
        <div class="question" data-qid="0">
            <p>🧦 1. Какой цвет носков ты выбрал бы для пингвина?</p>
            <div class="options">
                <button type="button" class="option-btn" data-value="радужный">🌈 Радужный</button>
                <button type="button" class="option-btn" data-value="невидимый">👻 Невидимый</button>
                <button type="button" class="option-btn" data-value="в горошек">🔴 В горошек</button>
            </div>
        </div>

        <!-- Вопрос 2: Суперспособность, которая бесполезна -->
        <div class="question" data-qid="1">
            <p>🍕 2. Какая бесполезная суперсила лучше всего?</p>
            <div class="options">
                <button type="button" class="option-btn" data-value="управление тостами">🍞 Управление тостами</button>
                <button type="button" class="option-btn" data-value="разговор с луком">🧅 Разговор с луком</button>
                <button type="button" class="option-btn" data-value="пукать блёстками">✨ Пукать блёстками</button>
            </div>
        </div>

        <!-- Вопрос 3: Что сделать если выиграл холодильник? -->
        <div class="question" data-qid="2">
            <p>❄️ 3. Вы выиграли холодильник, полный летающих хот-догов. Ваши действия?</p>
            <div class="options">
                <button type="button" class="option-btn" data-value="подружиться">🤝 Подружиться с хот-догами</button>
                <button type="button" class="option-btn" data-value="открыть музей">🏛️ Открыть музей хот-догов</button>
                <button type="button" class="option-btn" data-value="танцевать вальс">💃 Танцевать вальс</button>
            </div>
        </div>

        <!-- Вопрос 4: Какой звук у счастья -->
        <div class="question" data-qid="3">
            <p>🎵 4. Какой звук лучше всего описывает счастье?</p>
            <div class="options">
                <button type="button" class="option-btn" data-value="хруст чипсов">🍟 Хруст чипсов</button>
                <button type="button" class="option-btn" data-value="смех кота">🐱 Смех кота</button>
                <button type="button" class="option-btn" data-value="бульканье газировки">🥤 Бульканье газировки</button>
            </div>
        </div>
    </div>

    <!-- Кнопка ЗАВЕРШИТЬ и показать поздравление о потерянном времени -->
    <button id="submitSurvey" class="submit-btn">🔮 ЗАКОНЧИТЬ ОПРОС 🔮</button>

    <!-- Здесь появится поздравление о потраченном времени -->
    <div id="congratsMessage" class="congrats">
        <span>⏰💔</span><br>
        ПОЗДРАВЛЯЕМ!<br>
        Вы только что потеряли своё время на бессмысленный опрос!<br>
        Но зато улыбнулись? Значит, время потрачено не зря 😜<br>
        <span></span>ЛОХ ПОТЕРЯЛ ВРЕМЯ </span>
    </div>

    <!-- Блок с подробными пояснениями для ребёнка (как работает код) -->
    <div class="explanation">
    
    <div class="footer-note">
         классно! но улыбка гарантирована (почти) 
    </div>
</div>

<script>
    // ---------------------------
    //  JavaScript — логика опроса
    //  Здесь мы говорим странице, как реагировать на действия пользователя
    // ---------------------------

    // Сначала подождём, пока весь HTML загрузится (чтобы все элементы существовали)
    document.addEventListener('DOMContentLoaded', function() {
        // Находим все блоки вопросов (их 4)
        const questionDivs = document.querySelectorAll('.question');
        // Массив для хранения ответов пользователя. Длина = количество вопросов
        // Изначально все значения null (ничего не выбрано)
        let userAnswers = new Array(questionDivs.length).fill(null);
        
        // Функция, которая обновляет внешний вид активной кнопки внутри одного вопроса.
        // Она получает родительский элемент вопроса и значение выбранного ответа (строку).
        // Пробегает по всем кнопкам в этом вопросе и добавляет класс 'active' только той,
        // у которой data-value совпадает с выбранным ответом.
        function highlightSelectedOption(questionContainer, selectedValue) {
            const buttons = questionContainer.querySelectorAll('.option-btn');
            buttons.forEach(btn => {
                // Если значение кнопки равно выбранному значению — делаем активной
                if (btn.getAttribute('data-value') === selectedValue) {
                    btn.classList.add('active');
                } else {
                    btn.classList.remove('active');
                }
            });
        }

        // Для каждого вопроса обрабатываем клики по кнопкам-вариантам
        questionDivs.forEach((questionDiv, index) => {
            // Находим все кнопки внутри этого вопроса
            const optionButtons = questionDiv.querySelectorAll('.option-btn');
            
            optionButtons.forEach(button => {
                button.addEventListener('click', function(event) {
                    // Получаем значение варианта из атрибута data-value, например "радужный" или "невидимый"
                    const chosenValue = this.getAttribute('data-value');
                    // Сохраняем выбранный ответ в массив userAnswers под номером вопроса (index)
                    userAnswers[index] = chosenValue;
                    
                    // Обновляем подсветку: убираем активный класс у всех в этом вопросе, добавляем выбранному
                    highlightSelectedOption(questionDiv, chosenValue);
                    
                    // Небольшой прикольный эффект: кнопка издаёт "псевдо-вибрацию" (просто анимация через класс)
                    // Но это для веселья — можно пропустить. Добавим быстрый эффект масштаба
                    this.style.transform = 'scale(0.95)';
                    setTimeout(() => { if(this) this.style.transform = ''; }, 120);
                });
            });
        });
        
        // Находим кнопку завершения опроса
        const submitButton = document.getElementById('submitSurvey');
        // Находим блок, куда выведется поздравление
        const congratsBlock = document.getElementById('congratsMessage');
        
        // Обработчик клика на кнопку «Закончить опрос»
        submitButton.addEventListener('click', function() {
            // Проверяем, все ли вопросы имеют ответ (нет ли среди userAnswers значений null)
            const allAnswered = userAnswers.every(answer => answer !== null);
            
            if (!allAnswered) {
                // Если не все вопросы отвечены — выводим небольшое напоминание
                // (тоже бесполезное, но чтобы поздравление появилось только когда всё заполнено)
                alert('🤔 Ой! Ты пропустил вопрос.   быстро Ответь на все, чтобы получить приз!');
                return;
            }
            
            // --- Если все ответы есть, показываем поздравление ---
            // Сначала проверим, не показано ли уже поздравление (чтобы не дублировать)
            if (congratsBlock.style.display === 'block') {
                // Если уже видно, ничего не делаем, либо можно показать снова с анимацией, но не будем
                return;
            }
            
            // Делаем блок видимым (раньше он был скрыт display: none)
            congratsBlock.style.display = 'block';
            
            // Дополнительно пролистаем страницу к поздравлению, чтобы сразу увидеть (плавно)
            congratsBlock.scrollIntoView({ behavior: 'smooth', block: 'center' });
            
            // Небольшой звук? В браузере без разрешения звук нельзя, но можно порадовать консольным сообщением
            console.log('🎉 Поздравление активировано! Ответы пользователя: ', userAnswers);
            
            // Дополнительно меняем текст кнопки, чтобы показать, что всё завершено (просто красота)
            submitButton.textContent = '✅ получи  приз! ✅';
            submitButton.disabled = true;  // Делаем кнопку неактивной, чтобы не нажимали повторно
            submitButton.style.opacity = '0.7';
            submitButton.style.cursor = 'default';
            
            // Можно также вывести в консоль собранные ответы (интересно для любопытных)
            let answerSummary = '';
            for (let i = 0; i < userAnswers.length; i++) {
                answerSummary += `Вопрос ${i+1}: ${userAnswers[i]}\n`;
            }
            console.log('💾 Сохранённые ответы (бесполезные, но честные):\n' + answerSummary);
        });
        
        // Небольшой дополнительный бонус: при наведении на карточку с вопросами улыбка :)
        // (просто для интерактива)
        const card = document.querySelector('.survey-card');
        if(card) {
            card.addEventListener('mouseenter', () => {
                // Создаём радостное изменение тени – никакой логики, просто баловство
                card.style.boxShadow = '0 30px 45px rgba(0, 0, 0, 0.25), 0 0 0 12px #fff0bb, 0 0 0 16px #ffa559';
            });
            card.addEventListener('mouseleave', () => {
                card.style.boxShadow = '0 25px 40px rgba(0, 0, 0, 0.2), 0 0 0 12px #ffe6b3, 0 0 0 16px #ffb882';
            });
        }
        
        // P.S. Эта программа абсолютно бесполезна, но учит основам:
        // как работают события, массивы, условия, манипуляции с DOM.
        // Ты можешь легко изменить текст вопросов, ответы или добавить новые.
        // Просто скопируй блок .question и добавь в questionsArea.
        // Не забудь увеличить размер массива? Автоматически! Мы используем длину .question.length
        // То есть если добавить вопрос, код сам подстроится. Магия!
    });
</script>
</body>
</html>
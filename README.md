# Quis-b-blico
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Bíblico</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f8ff;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #2c3e50;
        }
        .question-container {
            display: none;
        }
        .question-container.active {
            display: block;
        }
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 10px 20px;
            margin-top: 10px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background-color: #2980b9;
        }
        .correct {
            color: green;
        }
        .wrong {
            color: red;
        }
        #result {
            display: none;
        }
        #result.correct {
            color: green;
            animation: correct-animation 1s forwards;
        }
        #result.wrong {
            color: red;
            animation: wrong-animation 1s forwards;
        }
        @keyframes correct-animation {
            0% { transform: scale(1); }
            100% { transform: scale(1.2); }
        }
        @keyframes wrong-animation {
            0% { transform: scale(1); }
            100% { transform: scale(0.8); }
        }
        #share-whatsapp {
            display: none;
            margin-top: 20px;
            background-color: #25D366;
            padding: 10px;
        }
    </style>
</head>
<body>

    <h1>Quiz Bíblico</h1>
    <p>Criado por: José</p>

    <div id="quiz-container">
        <div class="question-container active">
            <p>1. Qual foi o primeiro milagre de Jesus?</p>
            <button onclick="checkAnswer(1, true)">Transformar água em vinho</button>
            <button onclick="checkAnswer(1, false)">Curar um cego</button>
            <button onclick="checkAnswer(1, false)">Ressuscitar Lázaro</button>
            <button onclick="checkAnswer(1, false)">Multiplicar os pães</button>
        </div>

        <div class="question-container">
            <p>2. Quem construiu a arca?</p>
            <button onclick="checkAnswer(2, true)">Noé</button>
            <button onclick="checkAnswer(2, false)">Moisés</button>
            <button onclick="checkAnswer(2, false)">Abraão</button>
            <button onclick="checkAnswer(2, false)">Davi</button>
        </div>

        <!-- Adicione mais perguntas no mesmo formato -->

        <div class="question-container">
            <p>12. Qual discípulo negou Jesus três vezes?</p>
            <button onclick="checkAnswer(12, false)">João</button>
            <button onclick="checkAnswer(12, true)">Pedro</button>
            <button onclick="checkAnswer(12, false)">Tiago</button>
            <button onclick="checkAnswer(12, false)">Tomé</button>
        </div>

        <div id="result"></div>
    </div>

    <div id="share-whatsapp">
        <a href="https://wa.me/?text=Eu+acertei+X+de+12+perguntas+no+quiz+bíblico!+Tente+você+também!" target="_blank">Compartilhar no WhatsApp</a>
    </div>

    <script>
        let currentQuestion = 1;
        let score = 0;

        function checkAnswer(question, isCorrect) {
            if (isCorrect) {
                score++;
                document.getElementById('result').textContent = 'Correto!';
                document.getElementById('result').className = 'correct';
            } else {
                document.getElementById('result').textContent = 'Errado!';
                document.getElementById('result').className = 'wrong';
            }
            document.getElementById('result').style.display = 'block';

            setTimeout(() => {
                document.getElementById('result').style.display = 'none';
                showNextQuestion();
            }, 1000);
        }

        function showNextQuestion() {
            document.querySelector(`.question-container:nth-child(${currentQuestion})`).classList.remove('active');
            currentQuestion++;
            if (currentQuestion <= 12) {
                document.querySelector(`.question-container:nth-child(${currentQuestion})`).classList.add('active');
            } else {
                showFinalResult();
            }
        }

        function showFinalResult() {
            document.getElementById('quiz-container').style.display = 'none';
            const resultText = `Você acertou ${score} de 12 perguntas!`;
            document.getElementById('result').textContent = resultText;
            document.getElementById('result').className = 'correct';
            document.getElementById('result').style.display = 'block';
            document.getElementById('share-whatsapp').style.display = 'block';
            const whatsappLink = document.querySelector('#share-whatsapp a');
            whatsappLink.href = `https://wa.me/?text=Eu+acertei+${score}+de+12+perguntas+no+quiz+bíblico!+Tente+você+também!`;
        }
    </script>

</body>
</html>


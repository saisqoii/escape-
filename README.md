<!DOCTYPE html>
<html lang="nl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Escape Room - Doodverklaard</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Creepster&display=swap');
        body {
            background: url('https://i.imgur.com/Nz8Jt0X.jpg') no-repeat center center fixed; 
            background-size: cover;
            color: red;
            font-family: 'Creepster', cursive;
            text-align: center;
        }
        .container {
            width: 80%;
            margin: auto;
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            border: 5px solid red;
            border-radius: 10px;
        }
        .hidden { display: none; }
        button {
            background: red;
            color: black;
            font-size: 20px;
            border: none;
            padding: 10px;
            cursor: pointer;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div id="start-screen" class="container">
        <h1>Welkom bij de Escape Room: Doodverklaard</h1>
        <p>Je zit vast in een crime scene. Beantwoord alle vragen correct om te ontsnappen!</p>
        <button onclick="startGame()">Start</button>
    </div>
    
    <div id="game" class="container hidden">
        <h2 id="question"></h2>
        <input type="text" id="answer" placeholder="Jouw antwoord">
        <button onclick="checkAnswer()">Indienen</button>
        <p id="feedback"></p>
    </div>
    
    <div id="end-screen" class="container hidden">
        <h1>Je hebt ontsnapt!</h1>
        <p>Gefeliciteerd! Je hebt alle vragen correct beantwoord.</p>
    </div>
    
    <script>
        let questions = [
            { q: "Wie is de hoofdpersoon in het boek?", a: "Isa" },
            { q: "Wat overkomt Isa aan het begin van het boek?", a: "Ontvoering" },
            { q: "Hoe probeert Isa te ontsnappen?", a: "Via een raam" },
            { q: "Wie is de dader achter de verdwijning van Isa?", a: "Stiefvader" },
            { q: "Wat ontdekt Isa over haar verleden?", a: "Doodverklaard" },
            { q: "Waar wordt Isa vastgehouden?", a: "Kelder" },
            { q: "Wie helpt Isa bij haar ontsnapping?", a: "Haar beste vriendin" },
            { q: "Wat is de grote plottwist aan het einde?", a: "De waarheid over haar familie" }
        ];
        
        let currentQuestion = 0;
        function startGame() {
            document.getElementById('start-screen').classList.add('hidden');
            document.getElementById('game').classList.remove('hidden');
            loadQuestion();
        }
        
        function loadQuestion() {
            document.getElementById('question').innerText = questions[currentQuestion].q;
        }
        
        function checkAnswer() {
            let answer = document.getElementById('answer').value.trim();
            if (answer.toLowerCase() === questions[currentQuestion].a.toLowerCase()) {
                currentQuestion++;
                if (currentQuestion < questions.length) {
                    loadQuestion();
                    document.getElementById('answer').value = "";
                    document.getElementById('feedback').innerText = "Goed zo! Volgende vraag.";
                } else {
                    document.getElementById('game').classList.add('hidden');
                    document.getElementById('end-screen').classList.remove('hidden');
                }
            } else {
                document.getElementById('feedback').innerText = "Fout! Probeer opnieuw.";
            }
        }
    </script>
</body>
</html>

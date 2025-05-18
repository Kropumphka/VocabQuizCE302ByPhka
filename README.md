# VocabQuizCE302ByPhka
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Vocabulary Quiz Game</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f8ff;
      padding: 20px;
    }
    .quiz-container {
      background: white;
      border-radius: 12px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      max-width: 600px;
      margin: auto;
    }
    .question {
      font-weight: bold;
      margin-bottom: 10px;
    }
    .choices {
      margin-bottom: 20px;
    }
    .choices button {
      display: block;
      margin: 5px 0;
      padding: 10px;
      width: 100%;
      border: none;
      border-radius: 8px;
      background-color: #e0f7fa;
      cursor: pointer;
      transition: 0.3s;
    }
    .choices button:hover {
      background-color: #b2ebf2;
    }
    .result {
      font-size: 18px;
      font-weight: bold;
    }
    .next-btn {
      display: none;
      background: #4caf50;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="quiz-container">
    <div class="question" id="question"></div>
    <div class="choices" id="choices"></div>
    <div class="result" id="result"></div>
    <button class="next-btn" id="nextBtn" onclick="nextQuestion()">Next</button>
  </div>

  <script>
    const quiz = [
      {
        question: "What does 'enigma' mean?",
        choices: ["A puzzle or mystery", "A type of plant", "A musical note", "A tool"],
        answer: 0
      },
      {
        question: "Which word means 'to write carelessly'?",
        choices: ["Shiver", "Scrawl", "Radiate", "Concerto"],
        answer: 1
      },
      {
        question: "Which word describes a deep connection like family?",
        choices: ["Howl", "Kinship", "Epic", "Nagging"],
        answer: 1
      },
      {
        question: "What is a 'concerto'?",
        choices: ["A type of shelter", "A long musical piece", "A species of wolf", "A physical reaction"],
        answer: 1
      },
      {
        question: "What does 'shiver' mean?",
        choices: ["To write quickly", "To howl", "To shake from cold or emotion", "To run fast"],
        answer: 2
      }
    ];

    let currentQuestion = 0;

    function loadQuestion() {
      const q = quiz[currentQuestion];
      document.getElementById("question").textContent = q.question;
      const choicesDiv = document.getElementById("choices");
      choicesDiv.innerHTML = "";
      document.getElementById("result").textContent = "";
      document.getElementById("nextBtn").style.display = "none";

      q.choices.forEach((choice, index) => {
        const btn = document.createElement("button");
        btn.textContent = choice;
        btn.onclick = () => checkAnswer(index);
        choicesDiv.appendChild(btn);
      });
    }

    function checkAnswer(selected) {
      const correct = quiz[currentQuestion].answer;
      const result = document.getElementById("result");
      if (selected === correct) {
        result.textContent = "✅ Correct!";
        result.style.color = "green";
      } else {
        result.textContent = `❌ Incorrect. The correct answer is: ${quiz[currentQuestion].choices[correct]}`;
        result.style.color = "red";
      }
      document.getElementById("nextBtn").style.display = currentQuestion < quiz.length - 1 ? "inline-block" : "none";
    }

    function nextQuestion() {
      currentQuestion++;
      if (currentQuestion < quiz.length) {
        loadQuestion();
      }
    }

    window.onload = loadQuestion;
  </script>
</body>
</html>

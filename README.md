<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Guess the Number</title>
  <style>
    body { text-align: center; font-family: Arial, sans-serif; background-color: #f0f8ff; }
    h1 { color: #333; }
    button { padding: 10px 20px; font-size: 16px; }
  </style>
</head>
<body>
  <h1>Guess the Number!</h1>
  <p>Click the number that matches the question.</p>
  <h2 id="question"></h2>
  <div id="options"></div>
  <p id="result"></p>
  <script>
    const question = document.getElementById("question");
    const options = document.getElementById("options");
    const result = document.getElementById("result");

    let correctAnswer;

    function generateQuestion() {
      const randomNum = Math.floor(Math.random() * 10) + 1;
      correctAnswer = randomNum;
      question.textContent = `Which number is ${randomNum}?`;
      generateOptions();
    }

    function generateOptions() {
      options.innerHTML = '';
      for (let i = 1; i <= 10; i++) {
        const button = document.createElement("button");
        button.textContent = i;
        button.onclick = () => checkAnswer(i);
        options.appendChild(button);
      }
    }

    function checkAnswer(answer) {
      if (answer === correctAnswer) {
        result.textContent = "Correct! Well done!";
        result.style.color = "green";
        setTimeout(generateQuestion, 1000);
      } else {
        result.textContent = "Try again!";
        result.style.color = "red";
      }
    }

    generateQuestion();
  </script>
</body>
</html>

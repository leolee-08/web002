# web002
REPO를 이용한 간단한 홈페이지 만들기
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>숫자 맞추기 게임</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        #message {
            margin-top: 20px;
            font-size: 20px;
            font-weight: bold;
            color: #333;
        }
        input[type="number"] {
            padding: 10px;
            font-size: 16px;
            width: 50px;
            text-align: center;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        #reset {
            background-color: #f44336;
        }
        #reset:hover {
            background-color: #e53935;
        }
    </style>
</head>
<body>
    <h1>숫자 맞추기 게임</h1>
    <p>1부터 100 사이의 숫자를 맞추세요!</p>
    <input type="number" id="guess" min="1" max="100">
    <button onclick="checkGuess()">숫자 맞추기</button>
    <button id="reset" onclick="resetGame()">게임 다시 시작</button>

    <div id="message"></div>

    <script>
        let randomNumber;
        let attempts = 0;

        function startGame() {
            randomNumber = Math.floor(Math.random() * 100) + 1;
            attempts = 0;
            document.getElementById('message').textContent = "게임을 시작합니다! 숫자를 입력해보세요.";
            document.getElementById('guess').value = '';
        }

        function checkGuess() {
            const userGuess = Number(document.getElementById('guess').value);
            attempts++;

            if (userGuess < 1 || userGuess > 100) {
                document.getElementById('message').textContent = "1과 100 사이의 숫자를 입력해주세요.";
                return;
            }

            if (userGuess < randomNumber) {
                document.getElementById('message').textContent = `낮습니다! 시도 횟수: ${attempts}`;
            } else if (userGuess > randomNumber) {
                document.getElementById('message').textContent = `높습니다! 시도 횟수: ${attempts}`;
            } else {
                document.getElementById('message').textContent = `정답입니다! 총 시도 횟수: ${attempts}`;
            }
        }

        function resetGame() {
            startGame();
        }

        // 게임 시작
        startGame();
    </script>
</body>
</html>

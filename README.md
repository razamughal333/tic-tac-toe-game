# tic-tac-toe-game
Hehe

<html>
    <head>
        <title>Tic-Tac-Toe</title>
        <style>
            .board {
                display: flex;
                flex-wrap: wrap;
                width: 300px;
                height: 300px;
                border: 2px solid #000;
            }
            .square {
                width: 150px;
                height: 150px;
                display: flex;
                align-items: center;
                justify-content: center;
                font-size: 48px;
                font-weight: bold;
                font-family: sans-serif;
            }
            .player1 {
                background: blue;
                color: #000;
            }
            .player2 {
                background: #000;
                color: #fff;
            }
        </style>
    </head>
    <body>
        <div class="board" id="board">
            <div class="square" id="s1"></div>
            <div class="square" id="s2"></div>
            <div class="square" id="s3"></div>
            <div class="square" id="s4"></div>
            <div class="square" id="s5"></div>
            <div class="square" id="s6"></div>
            <div class="square" id="s7"></div>
            <div class="square" id="s8"></div>
            <div class="square" id="s9"></div>
        </div>
        <script>
            var board = document.querySelector('#board');
            var squares = document.querySelectorAll('.square');
            var turn = 'X';
            var gameOver = false;
            squares.forEach(function(square) {
                square.addEventListener('click', function() {
                    if (!gameOver && square.innerText === '') {
                        square.innerText = turn;
                        if (turn === 'X') {
                            turn = 'O';
                            square.classList.add('player1');
                        } else {
                            turn = 'X';
                            square.classList.add('player2');
                        }
                        checkGameOver();
                    }
                });
            });
            function checkGameOver() {
                var topLeft = squares[0].innerText;
                var topMiddle = squares[1].innerText;
                var topRight = squares[2].innerText;
                var middleLeft = squares[3].innerText;
                var middleMiddle = squares[4].innerText;
                var middleRight = squares[5].innerText;
                var bottomLeft = squares[6].innerText;
                var bottomMiddle = squares[7].innerText;
                var bottomRight = squares[8].innerText;
                // check rows
                if (topLeft !== '' && topLeft === topMiddle && topLeft === topRight) {
                    gameOver = true;
                } else if (middleLeft !== '' && middleLeft === middleMiddle && middleLeft === middleRight) {
                    gameOver = true;
                } else if (bottomLeft !== '' && bottomLeft === bottomMiddle && bottomLeft === bottomRight) {
                    gameOver = true;
                }
                // check columns
                if (topLeft !== '' && topLeft === middleLeft && topLeft === bottomLeft) {
                    gameOver = true;
                } else if (topMiddle !== '' && topMiddle === middleMiddle && topMiddle === bottomMiddle) {
                    gameOver = true;
                } else if (topRight !== '' && topRight === middleRight && topRight === bottomRight) {
                    gameOver = true;
                }
                // check diagonals
                if (topLeft !== '' && topLeft === middleMiddle && topLeft === bottomRight) {
                    gameOver = true;
                } else if (topRight !== '' && topRight === middleMiddle && topRight === bottomLeft) {
                    gameOver = true;
                }
            }
        </script>
    </body>
</html>

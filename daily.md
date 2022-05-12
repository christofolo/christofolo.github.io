---
layout: page
title: Daily Melody Guess
---

<div id="board-container">
    <div id="board"></div>
</div>

<div id="keyboard-container">    
    <div class="keyboard-row">
    <button data-key="enter" class="wide-button">Enter</button>
    <button data-key="1">1</button>
    <button data-key="2">2</button>
    <button data-key="3">3</button>
    <button data-key="4">4</button>
    <button data-key="5">5</button>
    <button data-key="6">6</button>
    <button data-key="7">7</button>
    <button data-key="del" class="wide-button">Del</button>
    </div>
</div>


<script type="text/javascript">
    document.addEventListener("DOMContentLoaded", () => {

      $('body').bind('keydown', function(e) {
        const key = e.keyCode;
        if (key == '13') {
          console.log('hit enter');
          handleSubmitWord();
        } else {
          const c = String.fromCharCode(key);
          if (c == '1' || c == '2' || c == '3' || c == '4' || c == '5' || c == '6' || c == '7') {
            console.log(c);
            updateGuessedWords(String.fromCharCode(e.keyCode));
          }
        }
        
        
        });

      createSquares();

      let guessedWords = [[]];
      let availableSpace = 1;

      let word = '22321';
      let guessedWordCount = 0;

      const keys = document.querySelectorAll(".keyboard-row button");

      function getCurrentWordArr() {
        const numberOfGuessedWords = guessedWords.length;
        return guessedWords[numberOfGuessedWords - 1];
      }

      function updateGuessedWords(letter) {
        const currentWordArr = getCurrentWordArr();

        if (currentWordArr && currentWordArr.length < 5) {
          currentWordArr.push(letter);

          const availableSpaceEl = document.getElementById(String(availableSpace));

          availableSpace = availableSpace + 1;
          availableSpaceEl.textContent = letter;
        }
      }

      function getTileColor(letter, index) {
        const isCorrectLetter = word.includes(letter);

        if (!isCorrectLetter) {
          return "rgb(58, 58, 60)";
        }

        const letterInThatPosition = word.charAt(index);
        const isCorrectPosition = letter === letterInThatPosition;

        if (isCorrectPosition) {
          return "rgb(83, 141, 78)";
        }

        return "rgb(181, 159, 59)";
      }

      function handleSubmitWord() {
        const currentWordArr = getCurrentWordArr();
        if (currentWordArr.length !== 5) {
          window.alert("Word must be 5 letters");
          return;
        }

        const currentWord = currentWordArr.join("");

        const firstLetterId = guessedWordCount * 5 + 1;
            const interval = 200;
            currentWordArr.forEach((letter, index) => {
              setTimeout(() => {
                const tileColor = getTileColor(letter, index);

                const letterId = firstLetterId + index;
                const letterEl = document.getElementById(letterId);
                letterEl.classList.add("animate__flipInX");
                letterEl.style = `background-color:${tileColor};border-color:${tileColor}`;
              }, interval * index);
            });

            guessedWordCount += 1;

            if (currentWord === word) {
              $('body').unbind('keydown');
              $('#keyboard-container').remove();
              window.alert("Congratulations!");
            }

            if (guessedWords.length === 6) {
              window.alert(`Sorry, you have no more guesses! The word is ${word}.`);
            }

            guessedWords.push([]);
      }

      function createSquares() {
        const gameBoard = document.getElementById("board");

        for (let index = 0; index < 30; index++) {
          let square = document.createElement("div");
          square.classList.add("square");
          square.classList.add("animate__animated");
          square.setAttribute("id", index + 1);
          
          gameBoard.appendChild(square);
        }
      }

      function handleDeleteLetter() {
        const currentWordArr = getCurrentWordArr();
        const removedLetter = currentWordArr.pop();

        guessedWords[guessedWords.length - 1] = currentWordArr;

        const lastLetterEl = document.getElementById(String(availableSpace - 1));

        lastLetterEl.textContent = "";
        availableSpace = availableSpace - 1;
      }

      for (let i = 0; i < keys.length; i++) {
        keys[i].onclick = ({ target }) => {
          const letter = target.getAttribute("data-key");
          console.log(letter);

          if (letter === "enter") {
            handleSubmitWord();
            return;
          }

          if (letter === "del") {
            handleDeleteLetter();
            return;
          }

          updateGuessedWords(letter);
        };
      }
});
</script>

## Instructions

Everyone is capable of imagining and even creating beautiful music. You just need a little help *visualizing* one of the main components of music - the Major Scale. The Major Scale is the source of nearly all music. If you can hear and sing the Major Scale then you will flourish as a musician. 

The Major Scale is just 7 notes and is something everyone can learn. All we need to do is pick our first note. Every Daily Melody Guess will be in the key of C. The note "C" will be our tonal center and then we mentally build the tonal numbers. Instead of thinking in notes (C, D, E...B, C), we just use numbers (1, 2, 3...7, 1).

Tonal Numbers have an inherent logic and are accessible to people who speak a variety of languages. 
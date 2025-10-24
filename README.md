
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bài tập kéo thả cảm ứng – Chương 1 Toán 11</title>
<style>
  body {
    font-family: "Segoe UI", sans-serif;
    background-color: #f4f8ff;
    margin: 20px;
    color: #222;
  }
  h1 {
    text-align: center;
    color: #1a73e8;
  }
  .question {
    background: #fff;
    padding: 15px;
    margin: 10px 0;
    border-radius: 10px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.1);
  }
  .dropzone {
    display: inline-block;
    min-width: 100px;
    min-height: 30px;
    border: 2px dashed #ccc;
    border-radius: 5px;
    padding: 3px;
    vertical-align: middle;
    background: #f0f8ff;
  }
  .answer {
    display: inline-block;
    background: #e3f2fd;
    padding: 8px 12px;
    margin: 5px;
    border-radius: 5px;
    border: 1px solid #90caf9;
    cursor: pointer;
    user-select: none;
  }
  .selected {
    background: #1976d2;
    color: white;
  }
  .correct {
    background: #c8e6c9 !important;
    border-color: #2e7d32 !important;
  }
  .incorrect {
    background: #ffcdd2 !important;
    border-color: #c62828 !important;
  }
  button {
    background: #1a73e8;
    color: white;
    border: none;
    padding: 8px 14px;
    border-radius: 5px;
    cursor: pointer;
    margin: 10px 5px 0 0;
  }
  button:hover { background: #0c5ed9; }
</style>
</head>
<body>

<h1>Bài tập kéo thả – Chương 1: Hàm số lượng giác</h1>

<div class="question">1. Chu kỳ của hàm số sin(x) là <span class="dropzone" data-answer="2π"></span>.</div>
<div class="question">2. Hàm số cos(x) đạt giá trị lớn nhất bằng <span class="dropzone" data-answer="1"></span>.</div>
<div class="question">3. Hàm số tan(x) không xác định tại <span class="dropzone" data-answer="(2k+1)π/2"></span>.</div>
<div class="question">4. Công thức sin²x + cos²x = <span class="dropzone" data-answer="1"></span>.</div>
<div class="question">5. tan(x) = sin(x) / <span class="dropzone" data-answer="cos(x)"></span>.</div>
<div class="question">6. cos(–x) = <span class="dropzone" data-answer="cos(x)"></span>.</div>
<div class="question">7. sin(π/2 – x) = <span class="dropzone" data-answer="cos(x)"></span>.</div>
<div class="question">8. Hàm số sin(x) là hàm <span class="dropzone" data-answer="lẻ"></span>.</div>
<div class="question">9. cos(π – x) = <span class="dropzone" data-answer="-cos(x)"></span>.</div>
<div class="question">10. tan(α + β) = <span class="dropzone" data-answer="(tanα+tanβ)/(1−tanαtanβ)"></span>.</div>

<h3>Chọn đáp án rồi chạm vào ô trống để thả:</h3>
<div id="answers">
  <div class="answer" data-value="1">1</div>
  <div class="answer" data-value="2π">2π</div>
  <div class="answer" data-value="(2k+1)π/2">(2k+1)π/2</div>
  <div class="answer" data-value="cos(x)">cos(x)</div>
  <div class="answer" data-value="lẻ">lẻ</div>
  <div class="answer" data-value="-cos(x)">-cos(x)</div>
  <div class="answer" data-value="(tanα+tanβ)/(1−tanαtanβ)">(tanα+tanβ)/(1−tanαtanβ)</div>
  <div class="answer" data-value="sin(x)">sin(x)</div>
  <div class="answer" data-value="π/2">π/2</div>
  <div class="answer" data-value="tan(x)">tan(x)</div>
</div>

<button onclick="checkAnswers()">Kiểm tra</button>
<button onclick="resetQuiz()">Làm lại</button>

<script>
let selectedAnswer = null;

document.querySelectorAll('.answer').forEach(ans => {
  ans.addEventListener('click', () => {
    document.querySelectorAll('.answer').forEach(a => a.classList.remove('selected'));
    selectedAnswer = ans;
    ans.classList.add('selected');
  });
});

document.querySelectorAll('.dropzone').forEach(zone => {
  zone.addEventListener('click', () => {
    if (selectedAnswer) {
      // Nếu ô trống đã có đáp án, trả lại vào vùng gốc
      if (zone.firstChild) {
        document.getElementById('answers').appendChild(zone.firstChild);
      }
      zone.appendChild(selectedAnswer);
      selectedAnswer.classList.remove('selected');
      selectedAnswer = null;
    }
  });
});

function checkAnswers() {
  let correct = 0;
  document.querySelectorAll('.dropzone').forEach(zone => {
    const child = zone.firstChild;
    if (child && child.dataset.value === zone.dataset.answer) {
      zone.classList.add('correct');
      zone.classList.remove('incorrect');
      correct++;
    } else {
      zone.classList.add('incorrect');
      zone.classList.remove('correct');
    }
  });
  alert(`Bạn làm đúng ${correct}/10 câu.`);
}

function resetQuiz() {
  document.querySelectorAll('.dropzone').forEach(zone => {
    if (zone.firstChild) {
      document.getElementById('answers').appendChild(zone.firstChild);
    }
    zone.classList.remove('correct', 'incorrect');
  });
  document.querySelectorAll('.answer').forEach(a => a.classList.remove('selected'));
  selectedAnswer = null;
}
</script>

</body>
</html>

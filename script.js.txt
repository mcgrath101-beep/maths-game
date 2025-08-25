function rand(n) { return Math.floor(Math.random() * n); }
function generateProblem() {
const a = rand(10) + 1;
const b = rand(10) + 1;
return { text: `${a} + ${b}`, answer: a + b };
}


let score = 0;
let current = generateProblem();
const els = {
problem: document.getElementById('problem'),
answer: document.getElementById('answer'),
submit: document.getElementById('submit'),
feedback: document.getElementById('feedback'),
score: document.getElementById('score')
};


function showProblem() { els.problem.textContent = current.text; }
function showScore() { els.score.textContent = `Score: ${score}`; }


function check() {
const val = parseInt(els.answer.value, 10);
if (val === current.answer) {
score++; els.feedback.textContent = '✅ Correct!';
els.answer.value = '';
current = generateProblem();
showProblem(); showScore();
} else {
els.feedback.textContent = '❌ Try again!';
}
els.answer.focus();
}


els.submit.addEventListener('click', check);
els.answer.addEventListener('keydown', (e) => { if (e.key === 'Enter') check(); });


showProblem(); showScore();
<!DOCTYPE html>
button { background-color: #ff6347; color: white; border: none; padding: 10px 20px; cursor: pointer; border-radius: 5px; }
button:hover { background-color: #ee4b2b; }
.question { margin-bottom: 15px; }
.option { margin-left: 20px; }
.result { margin-top: 20px; padding: 15px; background: #ffe4b5; border-radius: 5px; }
</style>
</head>
<body>
<h1>Психо-Сексо-Хумористичен Тест 3.0</h1>
<p>Леко абсурдна анкета за настроение, любов и способност да оцелееш без интернет, секс или топла мусака. Не е медицински тест – само за смях!</p>
<form id="quizForm">
<div id="questions"></div>
<button type="button" onclick="showResult()">Виж резултата!</button>
</form>
<div id="result" class="result"></div>
<script>
const questions = [
{q: "Кога за последно някой ти направи мусака?", options: ["a", "b", "c", "d"]},
{q: "Как реагираш, когато чуеш думата 'мотивирай се'?", options: ["a", "b", "c", "d"]},
{q: "Имаш ли сили за секс след като си изхвърлил 200 кг пръст и камъни?", options: ["a", "b", "c", "d"]},
{q: "Как се чувстваш, щом се събудиш все още облечен?", options: ["a", "b", "c", "d"]},
{q: "Колко често си казваш 'Ще си подредя живота утре'?", options: ["a", "b", "c", "d"]},
{q: "Ако можеше да се преродиш, би ли избрал да си легло с подсилена рамка?", options: ["a", "b", "c", "d"]},
{q: "Кога за последно някой ти каза 'Ухаеш на успех'?", options: ["a", "b", "c", "d"]},
{q: "Какво е най-екстремното нещо, което си правил в кухнята?", options: ["a", "b", "c", "d"]},
{q: "Коя е любимата ти панделка и защо винаги я слагаш, когато не трябва?", options: ["a", "b", "c", "d"]},
{q: "Какво мислиш за хората, които слагат кетчуп върху мусака?", options: ["a", "b", "c", "d"]}
// тук можеш да добавиш въпроси 11-30 по същия формат
];


const results = {
a: "Оптимистичен екзистенциалист: Може да се смее, докато плаче, и да направи мусака дори в палатка. Хроничен ентусиазъм, лекува се с три сарказма на ден и котка за терапия.",
b: "Романтичен катастрофист: Емоционален майстор с прекомерно сърце. Препоръчителна терапия – смях, приятели и пармезан.",
c: "Ироничен философ: Любовта при теб е като Wi-Fi: често изчезва, но когато работи – всички искат достъп.",
d: "Практичен циник с топло сърце: Стабилен чар, умерено безумие, дефицит на глупости – опасен баланс.",
mixed: "Пълно меню! Малко любов, малко ирония, малко мусака и една червена панделка за разкош."
};


const questionsDiv = document.getElementById('questions');
questions.forEach((q, i) => {
const div = document.createElement('div');
div.className = 'question';
div.innerHTML = `<p>${i+1}. ${q.q}</p>` + q.options.map(o =>
`<div class='option'><input type='radio' name='q${i}' value='${o}'> ${o}</div>`
).join('');
questionsDiv.appendChild(div);
});


function showResult() {
let counts = {a:0,b:0,c:0,d:0};
for(let i=0;i<questions.length;i++){
const val = document.querySelector(`input[name='q${i}']:checked`);
if(val){ counts[val.value]++; }
}
let max = Math.max(counts.a, counts.b, counts.c, counts.d);
let winners = Object.keys(counts).filter(k => counts[k] === max);
let resultText = winners.length === 1 ? results[winners[0]] : results.mixed;
document.getElementById('result').innerText = resultText;
}
</script>
</body>
</html>

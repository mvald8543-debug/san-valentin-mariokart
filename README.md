# san-valentin-mariokart<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Una carrera especial 🏁</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background: linear-gradient(135deg, #ff6f91, #ffc75f);
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
    }
    #game {
        background: white;
        padding: 25px;
        border-radius: 20px;
        width: 340px;
        text-align: center;
        box-shadow: 0 10px 30px rgba(0,0,0,0.25);
    }
    h2 {
        font-size: 18px;
    }
    button {
        width: 100%;
        padding: 12px;
        margin: 10px 0;
        font-size: 15px;
        border-radius: 12px;
        border: none;
        cursor: pointer;
    }
    .option {
        background: #f1f1f1;
    }
    .option:hover {
        background: #ffe0ec;
    }
    #yes {
        background: #ff4d6d;
        color: white;
    }
    #no {
        background: #dcdcdc;
    }
</style>
</head>

<body>

<div id="game"></div>

<script>
let level = 0;

const levels = [
    {
        question: "🏁 Primera carrera 🍄<br>¿Quién siempre quiere ganar?",
        options: ["Mario", "Luigi", "Tú cuando juegas 😌"],
        correct: 2,
        wrong: "💥 Caparazón azul… inténtalo otra vez"
    },
    {
        question: "⭐ Segunda carrera<br>¿Qué hacemos normalmente cuando terminamos una partida?",
        options: ["Nos enojamos", "Jugamos otra 😏", "Se apaga el Switch"],
        correct: 1,
        wrong: "🍌 Ups… te resbalaste"
    }
];

function loadLevel() {
    const game = document.getElementById("game");
    const l = levels[level];

    game.innerHTML = `<h2>${l.question}</h2>`;

    l.options.forEach((opt, i) => {
        const btn = document.createElement("button");
        btn.className = "option";
        btn.textContent = opt;
        btn.onclick = () => checkAnswer(i);
        game.appendChild(btn);
    });
}

function checkAnswer(choice) {
    const l = levels[level];
    if (choice === l.correct) {
        level++;
        if (level < levels.length) {
            loadLevel();
        } else {
            finalQuestion();
        }
    } else {
        alert(l.wrong);
    }
}

function finalQuestion() {
    const game = document.getElementById("game");
    game.innerHTML = `
        <h2>🏁 Carrera final</h2>
        <p>Después de tantas partidas…</p>
        <h3>Gladys…<br>¿Quieres ser mi San Valentín? 😌❤️</h3>
        <button id="yes" onclick="yes()">Sí 🙃</button>
        <button id="no" onclick="no()">No</button>
    `;
}

function no() {
    alert("🍌 Te resbalaste… esa no era 😌");
}

function yes() {
    const game = document.getElementById("game");
    game.innerHTML = `
        <h2>🙃 Gracias por decir que sí</h2>
        <p>Me hace muy feliz ❤️</p>
        <p>Feliz San Valentín 😊❤️</p>
    `;
}

loadLevel();
</script>

</body>
</html>

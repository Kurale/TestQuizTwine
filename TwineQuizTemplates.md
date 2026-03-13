# Twine 2 + SugarCube 2.37.3 — Универсальный шаблон учебного квиза

Ниже — готовый к копированию комплект для Twine Story Format **SugarCube 2.37.3**.

---

## Story Stylesheet

```css
:root {
  --bg: #f3f4f6;
  --surface: #ffffff;
  --surface-2: #f9fafb;
  --text: #111827;
  --muted: #6b7280;
  --primary: #2563eb;
  --primary-2: #1d4ed8;
  --success: #059669;
  --error: #dc2626;
  --warning: #d97706;
  --border: #e5e7eb;
  --shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
  --radius: 16px;
  --anim: 220ms cubic-bezier(.2,.8,.2,1);
}

html[data-theme="dark"] {
  --bg: #0f172a;
  --surface: #111827;
  --surface-2: #1f2937;
  --text: #f3f4f6;
  --muted: #9ca3af;
  --primary: #60a5fa;
  --primary-2: #3b82f6;
  --success: #34d399;
  --error: #f87171;
  --warning: #fbbf24;
  --border: #374151;
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.35);
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, sans-serif;
}

#story {
  max-width: 980px;
  margin: 0 auto;
}

.quiz-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  padding: 1.1rem 1.2rem;
  margin: 1rem 0;
  animation: card-in var(--anim);
}

.quiz-toolbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.8rem;
  flex-wrap: wrap;
  margin-bottom: 0.6rem;
}

.quiz-meta {
  color: var(--muted);
  font-size: 0.95rem;
}

.quiz-progress {
  height: 10px;
  border-radius: 99px;
  background: var(--surface-2);
  border: 1px solid var(--border);
  overflow: hidden;
}

.quiz-progress > span {
  display: block;
  height: 100%;
  background: linear-gradient(90deg, var(--primary), var(--primary-2));
  transition: width var(--anim);
}

.quiz-content {
  border: 1px dashed var(--border);
  border-radius: 12px;
  padding: 0.8rem;
  margin: 0.9rem 0;
  background: var(--surface-2);
}

.quiz-content img,
.quiz-content video,
.quiz-content audio,
.quiz-content iframe {
  max-width: 100%;
  border-radius: 10px;
}

.quiz-q {
  font-size: 1.08rem;
  font-weight: 600;
  margin: 0.4rem 0 0.8rem;
}

.answer-list {
  display: grid;
  gap: 0.6rem;
}

.answer-item {
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 0.55rem 0.7rem;
  background: var(--surface);
  transition: transform var(--anim), border-color var(--anim), background var(--anim);
}

.answer-item:hover {
  transform: translateY(-1px);
  border-color: var(--primary);
  background: var(--surface-2);
}

.quiz-actions {
  display: flex;
  gap: 0.6rem;
  flex-wrap: wrap;
  margin-top: 0.9rem;
}

button,
.link-internal {
  border-radius: 10px;
}

.btn-primary {
  background: var(--primary);
  color: #fff;
  border: none;
  padding: 0.45rem 0.85rem;
}

.btn-primary:hover {
  background: var(--primary-2);
}

.btn-ghost {
  border: 1px solid var(--border);
  background: var(--surface);
  color: var(--text);
  padding: 0.45rem 0.85rem;
}

.feedback {
  margin-top: 0.75rem;
  border-radius: 12px;
  padding: 0.65rem 0.8rem;
  border: 1px solid var(--border);
  animation: fade-in var(--anim);
}

.feedback.ok {
  border-color: color-mix(in srgb, var(--success) 45%, var(--border));
  background: color-mix(in srgb, var(--success) 10%, var(--surface));
}

.feedback.bad {
  border-color: color-mix(in srgb, var(--error) 45%, var(--border));
  background: color-mix(in srgb, var(--error) 10%, var(--surface));
}

.match-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.8rem;
}

.match-col {
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 0.6rem;
  background: var(--surface-2);
}

.match-item,
.match-drop {
  border: 1px solid var(--border);
  background: var(--surface);
  border-radius: 10px;
  padding: 0.5rem;
  margin: 0.45rem 0;
}

.match-item {
  cursor: grab;
}

.match-drop.over {
  border-color: var(--primary);
  outline: 2px dashed color-mix(in srgb, var(--primary) 40%, transparent);
}

.table-wrap {
  overflow-x: auto;
}

.result-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.95rem;
}

.result-table th,
.result-table td {
  border: 1px solid var(--border);
  padding: 0.55rem;
  text-align: left;
  vertical-align: top;
}

.badge {
  display: inline-block;
  padding: 0.1rem 0.5rem;
  border-radius: 999px;
  font-size: 0.8rem;
  border: 1px solid var(--border);
}

.badge.ok { color: var(--success); }
.badge.bad { color: var(--error); }

@keyframes fade-in {
  from { opacity: 0; transform: translateY(4px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes card-in {
  from { opacity: 0; transform: translateY(8px) scale(0.99); }
  to { opacity: 1; transform: translateY(0) scale(1); }
}

@media (max-width: 680px) {
  .match-grid {
    grid-template-columns: 1fr;
  }

  .quiz-card {
    padding: 0.9rem;
  }
}
```

---

## Story JavaScript

```javascript
/* global Macro, State, Engine, Save, setup, jQuery */

window.setup = window.setup || {};

setup.normalizeText = function (value) {
  return String(value ?? "")
    .toLowerCase()
    .replace(/\s+/g, " ")
    .trim();
};

setup.arrayEqUnordered = function (a, b) {
  const left = [...a].map(setup.normalizeText).sort();
  const right = [...b].map(setup.normalizeText).sort();
  return left.length === right.length && left.every((v, i) => v === right[i]);
};

setup.questionCounters = function () {
  const vars = State.variables;
  const stats = {
    all: { total: vars.quizData.length, ok: 0, bad: 0 },
    multiple: { total: 0, ok: 0, bad: 0 },
    yesno: { total: 0, ok: 0, bad: 0 },
    input: { total: 0, ok: 0, bad: 0 },
    matching: { total: 0, ok: 0, bad: 0 }
  };

  vars.quizData.forEach((q) => {
    if (stats[q.type]) {
      stats[q.type].total += 1;
    }
  });

  (vars.results || []).forEach((r) => {
    const key = r.type;
    if (!stats[key]) return;
    if (r.isCorrect) {
      stats[key].ok += 1;
      stats.all.ok += 1;
    } else {
      stats[key].bad += 1;
      stats.all.bad += 1;
    }
  });

  return stats;
};

setup.getCurrentQuestion = function () {
  const vars = State.variables;
  return vars.quizData?.[vars.currentQuestionIndex] || null;
};

setup.recordResult = function (payload) {
  const vars = State.variables;
  const existingIndex = vars.results.findIndex((x) => x.id === payload.id);
  if (existingIndex >= 0) {
    vars.results[existingIndex] = payload;
  } else {
    vars.results.push(payload);
  }

  vars.score = vars.results.filter((x) => x.isCorrect).length;
};

setup.nextPassageForQuestion = function (question) {
  const map = {
    multiple: "MultipleChoice",
    yesno: "YesNo",
    input: "InputAnswer",
    matching: "Matching"
  };
  return map[question.type] || "Menu";
};

setup.gotoCurrentQuestionPassage = function () {
  const q = setup.getCurrentQuestion();
  if (!q) {
    Engine.play("Result");
    return;
  }
  Engine.play(setup.nextPassageForQuestion(q));
};

setup.gotoNextQuestion = function () {
  const vars = State.variables;
  vars.currentQuestionIndex += 1;
  setup.gotoCurrentQuestionPassage();
};

setup.quizPercent = function () {
  const vars = State.variables;
  const total = vars.quizData.length || 1;
  return Math.round((vars.score / total) * 100);
};

setup.downloadJSON = function () {
  const vars = State.variables;
  const payload = {
    finishedAt: new Date().toISOString(),
    elapsedSeconds: Math.round((Date.now() - vars.startedAtMs) / 1000),
    score: vars.score,
    total: vars.quizData.length,
    percent: setup.quizPercent(),
    results: vars.results
  };

  const blob = new Blob([JSON.stringify(payload, null, 2)], { type: "application/json" });
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = "quiz-result.json";
  a.click();
  URL.revokeObjectURL(url);
};

setup.shuffle = function (arr) {
  const copy = [...arr];
  for (let i = copy.length - 1; i > 0; i -= 1) {
    const j = Math.floor(Math.random() * (i + 1));
    [copy[i], copy[j]] = [copy[j], copy[i]];
  }
  return copy;
};

setup.initQuiz = function () {
  const vars = State.variables;
  vars.currentQuestionIndex = 0;
  vars.results = [];
  vars.score = 0;
  vars.startedAtMs = Date.now();
  setup.gotoCurrentQuestionPassage();
};

Macro.add("themetoggle", {
  handler() {
    const $btn = jQuery("<button class='btn-ghost'>🌓 Тема</button>");
    $btn.on("click", () => {
      const root = document.documentElement;
      const next = root.dataset.theme === "dark" ? "light" : "dark";
      root.dataset.theme = next;
      State.variables.uiTheme = next;
    });
    jQuery(this.output).append($btn);
  }
});

Macro.add("progressbar", {
  handler() {
    const vars = State.variables;
    const current = Math.min(vars.currentQuestionIndex + 1, vars.quizData.length);
    const percent = Math.round((current / Math.max(vars.quizData.length, 1)) * 100);
    const html = `
      <div class="quiz-meta">Вопрос ${current} из ${vars.quizData.length}</div>
      <div class="quiz-progress" aria-label="Прогресс"><span style="width:${percent}%"></span></div>
    `;
    jQuery(this.output).wiki(html);
  }
});

Macro.add("rendercontent", {
  handler() {
    const vars = State.variables;
    const raw = vars.contentHTML || "";
    const html = `<div class="quiz-content">${raw}</div>`;
    jQuery(this.output).wiki(html);
  }
});

document.addEventListener("DOMContentLoaded", () => {
  const root = document.documentElement;
  const saved = State.variables?.uiTheme;
  root.dataset.theme = saved || "light";
});

$(document).on(":passagedisplay", () => {
  const root = document.documentElement;
  root.dataset.theme = State.variables.uiTheme || root.dataset.theme || "light";
});
```

---

## Пассажи

### Menu

```twine
:: Menu
<div class="quiz-card">
  <div class="quiz-toolbar">
    <h2>📘 Учебный квиз</h2>
    <<themetoggle>>
  </div>

  <p>Готовый универсальный шаблон. Настройте вопросы в <b>QuizSetup</b> и запускайте тест.</p>

  <div class="quiz-actions">
    <<button "🚀 Начать тест">><<run setup.initQuiz()>><</button>>
    <<button "🛠️ Редактировать вопросы">><<goto "QuizSetup">><</button>>
  </div>
</div>
```

### QuizSetup

```twine
:: QuizSetup
<<if !$quizData>>
<<set $quizData = [
  {
    id: 1,
    type: "multiple",
    contentHTML: "<p><b>Тема:</b> Основы веба</p><img src='https://placehold.co/800x260/png?text=HTTP+Basics' alt='HTTP Basics'>",
    question: "Какие из вариантов являются HTTP-методами?",
    answers: ["GET", "PUSH", "POST", "FETCH"],
    correct: ["GET", "POST"],
    explanation: "Стандартные методы: GET, POST, PUT, PATCH, DELETE и др."
  },
  {
    id: 2,
    type: "yesno",
    contentHTML: "<p>JavaScript может выполняться и в браузере, и на сервере (Node.js).</p>",
    question: "Верно ли это утверждение?",
    answers: ["Да", "Нет"],
    correct: "Да",
    explanation: "Node.js предоставляет серверную среду выполнения JS."
  },
  {
    id: 3,
    type: "input",
    contentHTML: "<video src='https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.mp4' controls autoplay muted></video>",
    question: "Введите аббревиатуру языка разметки гипертекста.",
    answers: [],
    correct: {
      mode: "exact",
      value: "HTML",
      keywords: ["html"],
      regex: ""
    },
    explanation: "Правильный ответ: HTML (HyperText Markup Language)."
  },
  {
    id: 4,
    type: "matching",
    contentHTML: "<audio src='https://interactive-examples.mdn.mozilla.net/media/cc0-audio/t-rex-roar.mp3' controls></audio>",
    question: "Сопоставьте технологию и её назначение.",
    answers: {
      left: ["HTML", "CSS", "JavaScript"],
      right: ["Структура", "Стили", "Логика"]
    },
    correct: {
      "HTML": "Структура",
      "CSS": "Стили",
      "JavaScript": "Логика"
    },
    explanation: "HTML отвечает за структуру, CSS — за оформление, JS — за поведение."
  }
]>>
<</if>>

<<if !$results>><<set $results = []>><</if>>
<<if !$uiTheme>><<set $uiTheme = "light">><</if>>

<div class="quiz-card">
  <div class="quiz-toolbar">
    <h2>⚙️ QuizSetup</h2>
    <<themetoggle>>
  </div>

  <p>Все вопросы хранятся в <code>$quizData</code>. Редактируйте только этот массив.</p>

  <div class="quiz-content">
    <pre><<print JSON.stringify($quizData, null, 2)>></pre>
  </div>

  <p class="quiz-meta">Поддерживаемые типы: <code>multiple</code>, <code>yesno</code>, <code>input</code>, <code>matching</code>.</p>

  <div class="quiz-actions">
    <<button "💾 Сбросить результаты">><<set $results = []>><<set $score = 0>><<set $currentQuestionIndex = 0>>Результаты очищены.<</button>>
    <<button "✅ Готово, в меню">><<goto "Menu">><</button>>
  </div>
</div>
```

### ContentTemplate

```twine
:: ContentTemplate
<div class="quiz-card">
  <h3>📎 Контент перед вопросом</h3>
  <p class="quiz-meta">Вставьте HTML в <code>$contentHTML</code>: текст, <code>&lt;img&gt;</code>, <code>&lt;video controls autoplay muted&gt;</code>, <code>&lt;audio&gt;</code>.</p>
  <<rendercontent>>
</div>
```

### MultipleChoice

```twine
:: MultipleChoice
<<set _q = setup.getCurrentQuestion()>>
<<if !_q>><<goto "Result">><</if>>
<<if _q.type !== "multiple">><<run setup.gotoCurrentQuestionPassage()>><</if>>

<<set $contentHTML = _q.contentHTML>>
<<set _inputName = "mc_" + _q.id>>
<<set _answerMap = {}>>

<div class="quiz-card">
  <div class="quiz-toolbar">
    <<progressbar>>
    <<themetoggle>>
  </div>

  <<include "ContentTemplate">>

  <div class="quiz-q">❓ <<= _q.question>></div>

  <div class="answer-list">
    <<if Array.isArray(_q.correct) && _q.correct.length > 1>>
      <<for _i to 0; _i < _q.answers.length; _i++>>
        <<set _ans = _q.answers[_i]>>
        <<set _answerMap[_ans] = false>>
        <label class="answer-item"><<checkbox "_answerMap[\"" + _ans + "\"]" false true>> <<= _ans>></label>
      <</for>>
    <<else>>
      <<set _picked = "">>
      <<for _i to 0; _i < _q.answers.length; _i++>>
        <<set _ans = _q.answers[_i]>>
        <label class="answer-item"><<radiobutton "_picked" _ans autocheck>> <<= _ans>></label>
      <</for>>
    <</if>>
  </div>

  <<set _checked = false>>
  <<set _isCorrect = false>>

  <div class="quiz-actions">
    <<button "Проверить">>
      <<if Array.isArray(_q.correct) && _q.correct.length > 1>>
        <<set _user = []>>
        <<for _k range Object.keys(_answerMap)>>
          <<if _answerMap[_k]>><<set _user.push(_k)>><</if>>
        <</for>>
        <<set _isCorrect = setup.arrayEqUnordered(_user, _q.correct)>>
        <<set _userPrintable = _user.join(", ") || "(пусто)">>
      <<else>>
        <<set _user = _picked>>
        <<set _isCorrect = setup.normalizeText(_picked) === setup.normalizeText(Array.isArray(_q.correct) ? _q.correct[0] : _q.correct)>>
        <<set _userPrintable = _picked || "(пусто)">>
      <</if>>

      <<run setup.recordResult({
        id: _q.id,
        type: _q.type,
        question: _q.question,
        userAnswer: _user,
        userAnswerPrintable: _userPrintable,
        correctAnswer: _q.correct,
        isCorrect: _isCorrect,
        explanation: _q.explanation
      })>>

      <<set _checked = true>>
    <</button>>

    <<if _checked>>
      <<button "Далее">><<run setup.gotoNextQuestion()>><</button>>
    <</if>>
  </div>

  <<if _checked>>
    <div class="feedback <<if _isCorrect>>ok<<else>>bad<</if>>">
      <<if _isCorrect>>✅ Верно!<<else>>❌ Неверно.<</if>>
      <br><b>Пояснение:</b> <<= _q.explanation>>
    </div>
  <</if>>
</div>
```

### YesNo

```twine
:: YesNo
<<set _q = setup.getCurrentQuestion()>>
<<if !_q>><<goto "Result">><</if>>
<<if _q.type !== "yesno">><<run setup.gotoCurrentQuestionPassage()>><</if>>

<<set $contentHTML = _q.contentHTML>>
<<set _choice = "">>
<<set _checked = false>>
<<set _isCorrect = false>>

<div class="quiz-card">
  <div class="quiz-toolbar">
    <<progressbar>>
    <<themetoggle>>
  </div>

  <<include "ContentTemplate">>

  <div class="quiz-q">❓ <<= _q.question>></div>

  <div class="quiz-actions">
    <<button "Да">><<set _choice = "Да">><</button>>
    <<button "Нет">><<set _choice = "Нет">><</button>>
    <<button "Проверить">>
      <<set _isCorrect = setup.normalizeText(_choice) === setup.normalizeText(_q.correct)>>
      <<run setup.recordResult({
        id: _q.id,
        type: _q.type,
        question: _q.question,
        userAnswer: _choice,
        userAnswerPrintable: _choice || "(пусто)",
        correctAnswer: _q.correct,
        isCorrect: _isCorrect,
        explanation: _q.explanation
      })>>
      <<set _checked = true>>
    <</button>>

    <<if _checked>>
      <<button "Далее">><<run setup.gotoNextQuestion()>><</button>>
    <</if>>
  </div>

  <p class="quiz-meta">Ваш выбор: <<= _choice || "(не выбрано)">></p>

  <<if _checked>>
    <div class="feedback <<if _isCorrect>>ok<<else>>bad<</if>>">
      <<if _isCorrect>>✅ Верно!<<else>>❌ Неверно.<</if>>
      <br><b>Пояснение:</b> <<= _q.explanation>>
    </div>
  <</if>>
</div>
```

### InputAnswer

```twine
:: InputAnswer
<<set _q = setup.getCurrentQuestion()>>
<<if !_q>><<goto "Result">><</if>>
<<if _q.type !== "input">><<run setup.gotoCurrentQuestionPassage()>><</if>>

<<set $contentHTML = _q.contentHTML>>
<<set _text = "">>
<<set _checked = false>>
<<set _isCorrect = false>>

<div class="quiz-card">
  <div class="quiz-toolbar">
    <<progressbar>>
    <<themetoggle>>
  </div>

  <<include "ContentTemplate">>

  <div class="quiz-q">❓ <<= _q.question>></div>

  <p><<textbox "_text" "Введите ответ..."></p>

  <div class="quiz-actions">
    <<button "Проверить">>
      <<set _mode = _q.correct.mode || "exact">>
      <<set _valueNorm = setup.normalizeText(_text)>>

      <<if _mode === "exact">>
        <<set _isCorrect = _valueNorm === setup.normalizeText(_q.correct.value)>>
      <<elseif _mode === "partial">>
        <<set _isCorrect = false>>
        <<for _k to 0; _k < _q.correct.keywords.length; _k++>>
          <<if _valueNorm.includes(setup.normalizeText(_q.correct.keywords[_k]))>>
            <<set _isCorrect = true>>
          <</if>>
        <</for>>
      <<elseif _mode === "regex">>
        <<run _re = new RegExp(_q.correct.regex, "i")>>
        <<set _isCorrect = _re.test(_text)>>
      <<else>>
        <<set _isCorrect = false>>
      <</if>>

      <<run setup.recordResult({
        id: _q.id,
        type: _q.type,
        question: _q.question,
        userAnswer: _text,
        userAnswerPrintable: _text || "(пусто)",
        correctAnswer: _q.correct,
        isCorrect: _isCorrect,
        explanation: _q.explanation
      })>>
      <<set _checked = true>>
    <</button>>

    <<if _checked>>
      <<button "Далее">><<run setup.gotoNextQuestion()>><</button>>
    <</if>>
  </div>

  <<if _checked>>
    <div class="feedback <<if _isCorrect>>ok<<else>>bad<</if>>">
      <<if _isCorrect>>✅ Верно!<<else>>❌ Неверно.<</if>>
      <br><b>Пояснение:</b> <<= _q.explanation>>
    </div>
  <</if>>
</div>
```

### Matching

```twine
:: Matching
<<set _q = setup.getCurrentQuestion()>>
<<if !_q>><<goto "Result">><</if>>
<<if _q.type !== "matching">><<run setup.gotoCurrentQuestionPassage()>><</if>>

<<set $contentHTML = _q.contentHTML>>
<<set _checked = false>>
<<set _isCorrect = false>>

<div class="quiz-card" id="matchingRoot">
  <div class="quiz-toolbar">
    <<progressbar>>
    <<themetoggle>>
  </div>

  <<include "ContentTemplate">>

  <div class="quiz-q">❓ <<= _q.question>></div>

  <div class="match-grid">
    <div class="match-col">
      <h4>Перетащите</h4>
      <div id="dragPool"></div>
    </div>
    <div class="match-col">
      <h4>К соответствию</h4>
      <div id="dropZone"></div>
    </div>
  </div>

  <div class="quiz-actions">
    <<button "Проверить" "matchingCheckBtn">><</button>>
    <<button "Далее" "matchingNextBtn">><<run setup.gotoNextQuestion()>><</button>>
  </div>

  <div id="matchingFeedback"></div>
</div>

<<script>>
(function () {
  const q = State.variables.quizData[State.variables.currentQuestionIndex];
  const pool = document.getElementById("dragPool");
  const zone = document.getElementById("dropZone");
  const feedback = document.getElementById("matchingFeedback");
  const nextBtn = document.getElementById("matchingNextBtn");
  nextBtn.style.display = "none";

  const shuffled = setup.shuffle(q.answers.right);
  const assignments = {};

  q.answers.left.forEach((left) => {
    const drop = document.createElement("div");
    drop.className = "match-drop";
    drop.dataset.left = left;
    drop.innerHTML = `<b>${left}</b><br><span class='quiz-meta'>Перетащите сюда</span>`;

    drop.addEventListener("dragover", (e) => {
      e.preventDefault();
      drop.classList.add("over");
    });

    drop.addEventListener("dragleave", () => {
      drop.classList.remove("over");
    });

    drop.addEventListener("drop", (e) => {
      e.preventDefault();
      drop.classList.remove("over");
      const value = e.dataTransfer.getData("text/plain");
      assignments[left] = value;
      drop.innerHTML = `<b>${left}</b><br><span>${value}</span>`;
    });

    zone.appendChild(drop);
  });

  shuffled.forEach((rightValue) => {
    const item = document.createElement("div");
    item.className = "match-item";
    item.draggable = true;
    item.textContent = rightValue;

    item.addEventListener("dragstart", (e) => {
      e.dataTransfer.setData("text/plain", rightValue);
    });

    pool.appendChild(item);
  });

  document.getElementById("matchingCheckBtn").addEventListener("click", () => {
    const correct = q.correct;
    const isCorrect = q.answers.left.every((left) => assignments[left] === correct[left]);

    setup.recordResult({
      id: q.id,
      type: q.type,
      question: q.question,
      userAnswer: assignments,
      userAnswerPrintable: JSON.stringify(assignments),
      correctAnswer: correct,
      isCorrect,
      explanation: q.explanation
    });

    feedback.innerHTML = `
      <div class="feedback ${isCorrect ? "ok" : "bad"}">
        ${isCorrect ? "✅ Верно!" : "❌ Неверно."}<br>
        <b>Пояснение:</b> ${q.explanation}
      </div>
    `;

    nextBtn.style.display = "inline-block";
  });
})();
<</script>>
```

### Result

```twine
:: Result
<<set _stats = setup.questionCounters()>>
<<set _percent = setup.quizPercent()>>
<<set _elapsed = Math.round((Date.now() - $startedAtMs) / 1000)>>

<div class="quiz-card">
  <div class="quiz-toolbar">
    <h2>📊 Итоги теста</h2>
    <<themetoggle>>
  </div>

  <p>
    Результат: <b><<print $score>></b> / <b><<print $quizData.length>></b>
    (<b><<print _percent>>%</b>)
    <<if _percent >= 80>>🎉<<elseif _percent >= 50>>🙂<<else>>💡<</if>>
  </p>

  <div class="quiz-progress"><span style="width: <<= _percent>>%"></span></div>

  <p class="quiz-meta">Время прохождения: <<= _elapsed>> сек.</p>

  <ul>
    <li>MultipleChoice: ✅ <<print _stats.multiple.ok>> / ❌ <<print _stats.multiple.bad>></li>
    <li>YesNo: ✅ <<print _stats.yesno.ok>> / ❌ <<print _stats.yesno.bad>></li>
    <li>InputAnswer: ✅ <<print _stats.input.ok>> / ❌ <<print _stats.input.bad>></li>
    <li>Matching: ✅ <<print _stats.matching.ok>> / ❌ <<print _stats.matching.bad>></li>
  </ul>

  <div class="table-wrap">
    <table class="result-table">
      <thead>
        <tr>
          <th>ID</th>
          <th>Тип</th>
          <th>Вопрос</th>
          <th>Ваш ответ</th>
          <th>Правильный ответ</th>
          <th>Статус</th>
        </tr>
      </thead>
      <tbody>
        <<for _i to 0; _i < $results.length; _i++>>
          <<set _r = $results[_i]>>
          <tr>
            <td><<print _r.id>></td>
            <td><<print _r.type>></td>
            <td><<print _r.question>></td>
            <td><<print _r.userAnswerPrintable>></td>
            <td><<print JSON.stringify(_r.correctAnswer)>></td>
            <td>
              <<if _r.isCorrect>><span class="badge ok">Верно</span><<else>><span class="badge bad">Ошибка</span><</if>>
            </td>
          </tr>
        <</for>>
      </tbody>
    </table>
  </div>

  <div class="quiz-actions">
    <<button "🔁 Пройти заново">><<run setup.initQuiz()>><</button>>
    <<button "⬇️ Скачать результат как JSON">><<run setup.downloadJSON()>><</button>>
    <<button "🏠 Вернуться в меню">><<goto "Menu">><</button>>
  </div>
</div>
```

---

## Инструкция для пользователя (RU)

1. **Где редактировать вопросы**  
   Откройте пассаж **QuizSetup** и изменяйте только массив **`$quizData`**.

2. **Как добавить новый вопрос**  
   Добавьте новый объект в массив:
   - `id`: уникальный номер;
   - `type`: `multiple`, `yesno`, `input`, `matching`;
   - `contentHTML`: любой HTML до вопроса (текст, img, video, audio);
   - `question`: текст вопроса;
   - `answers`: список ответов или пары для matching;
   - `correct`: правильный ответ в формате, зависящем от типа;
   - `explanation`: пояснение после проверки.

3. **Как менять контент перед вопросом**  
   В каждом объекте задайте `contentHTML`, например:
   - `"<img src='...'>"`
   - `"<video src='...' controls autoplay muted></video>"`
   - `"<audio src='...' controls></audio>"`
   - HTML-текст с форматированием.

4. **Как изменить порядок вопросов**  
   Просто переставьте объекты местами внутри массива `$quizData`.

5. **Как настроить проверку text input**
   - `mode: "exact"` + `value` — полное совпадение (без учёта регистра/лишних пробелов);
   - `mode: "partial"` + `keywords` — ответ считается верным, если содержит ключевые слова;
   - `mode: "regex"` + `regex` — проверка регулярным выражением.

6. **Почему этот шаблон стабильнее**
   - Убраны устаревшие конструкции и хаотичный inline-state.
   - Единая точка данных (`$quizData`) и единый слой служебных функций (`setup.*`).
   - Результаты сохраняются централизованно через `setup.recordResult`.
   - Переключение тем и прогресс обрабатываются одинаково во всех механиках.

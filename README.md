<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Quiz - Validação de Limpeza na Indústria Farmacêutica</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #e0f7fa, #ffffff);
      color: #333;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }
    .container {
      background: #fff;
      padding: 30px;
      max-width: 700px;
      width: 100%;
      border-radius: 20px;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
      text-align: center;
    }
    h1 {
      color: #0288d1;
      margin-bottom: 20px;
    }
    .question {
      font-size: 20px;
      margin-bottom: 16px;
      font-weight: 700;
      text-align: left;
    }
    .answers {
      list-style: none;
      padding-left: 0;
      margin-bottom: 20px;
      text-align: left;
    }
    .answers li {
      margin-bottom: 12px;
    }
    label {
      display: block;
      background-color: #e1f5fe;
      padding: 12px 16px;
      border-radius: 8px;
      cursor: pointer;
      transition: background-color 0.3s ease;
      user-select: none;
    }
    input[type="radio"] {
      display: none;
    }
    input[type="radio"]:checked + label {
      font-weight: 700;
      outline: 2px solid #0288d1;
    }
    .correct {
      background-color: #c8e6c9 !important;
      color: #2e7d32;
      font-weight: 700;
    }
    .incorrect {
      background-color: #ffcdd2 !important;
      color: #b71c1c;
      font-weight: 700;
    }
    button {
      background-color: #0288d1;
      color: white;
      border: none;
      padding: 14px 20px;
      border-radius: 10px;
      font-size: 18px;
      cursor: pointer;
      width: 100%;
      transition: background-color 0.3s ease;
      margin-top: 10px;
    }
    button:hover {
      background-color: #0277bd;
    }
    .result {
      text-align: center;
      font-size: 22px;
      color: #2e7d32;
      margin-top: 30px;
      font-weight: 700;
    }
    #restart-btn {
      display: none;
      background-color: #43a047;
      margin-top: 15px;
    }
    #restart-btn:hover {
      background-color: #388e3c;
    }
    #quiz {
      display: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Quiz: Validação de Limpeza na Indústria Farmacêutica</h1>

    <button id="start-btn">Iniciar Quiz</button>

    <div id="quiz">
      <p class="question" id="question">Carregando pergunta...</p>
      <ul class="answers" id="answer-list"></ul>
      <button id="next-btn">Próxima</button>
      <p class="result" id="result"></p>
      <button id="restart-btn">Refazer Quiz</button>
    </div>
  </div>

  <script>
    const quizData = [
      {
        question: "1. O que é uma validação de limpeza na indústria farmacêutica?",
        options: [
          "Teste para verificar se o produto é eficaz",
          "Processo documentado que comprova a remoção eficaz de resíduos de equipamentos",
          "Limpeza visual do equipamento",
          "Etapa opcional para produtos não perigosos"
        ],
        correct: 1
      },
      {
        question: "2. Por que a validação de limpeza é importante nesse setor?",
        options: [
          "Para aumentar a produtividade",
          "Para evitar contaminação cruzada e garantir segurança do paciente",
          "Para reduzir custos com detergentes",
          "Para acelerar a produção"
        ],
        correct: 1
      },
      {
        question: "3. Como deve ser realizada a validação de limpeza?",
        options: [
          "Por meio de procedimentos documentados e testes laboratoriais específicos",
          "Somente com limpeza visual",
          "Usando apenas água corrente",
          "Por inspeção do gerente da produção"
        ],
        correct: 0
      },
      {
        question: "4. Quando a validação de limpeza deve ser feita?",
        options: [
          "Antes de iniciar a produção e sempre que houver mudanças significativas no processo",
          "Uma vez por ano",
          "Sempre que o equipamento for usado",
          "Apenas quando houver reclamações"
        ],
        correct: 0
      },
      {
        question: "5. Quais os principais métodos para validar a limpeza?",
        options: [
          "Inspeção visual e testes químicos ou microbiológicos",
          "Apenas inspeção visual",
          "Testes microbiológicos somente",
          "Usar detergentes específicos"
        ],
        correct: 0
      },
      {
        question: "6. O que pode invalidar uma validação de limpeza?",
        options: [
          "Mudanças no processo sem revalidação",
          "Uso de detergente recomendado",
          "Treinamento da equipe",
          "Limpeza automatizada"
        ],
        correct: 0
      },
      {
        question: "7. Qual a função dos critérios de aceitação na validação?",
        options: [
          "Definir os limites máximos aceitáveis de resíduos que garantem segurança",
          "Definir o tempo para limpeza",
          "Determinar o custo da limpeza",
          "Aumentar a produção"
        ],
        correct: 0
      },
      {
        question: "8. Qual órgão regulamenta a validação de limpeza no Brasil?",
        options: [
          "FDA",
          "ANVISA",
          "OMS",
          "IBAMA"
        ],
        correct: 1
      },
      {
        question: "9. Como a documentação da validação de limpeza deve ser feita?",
        options: [
          "De forma clara, completa e disponível para auditorias",
          "Somente em relatórios internos",
          "De forma verbal entre os responsáveis",
          "Não é necessária"
        ],
        correct: 0
      },
      {
        question: "10. Qual a frequência recomendada para a revalidação de limpeza?",
        options: [
          "Sempre que houver mudanças no processo ou equipamentos, ou periodicamente conforme procedimentos internos",
          "Nunca, uma validação é definitiva",
          "Diariamente",
          "A cada lote produzido"
        ],
        correct: 0
      }
    ];

    let currentQuestion = 0;
    let score = 0;
    let answered = false;

    const startBtn = document.getElementById("start-btn");
    const quiz = document.getElementById("quiz");
    const questionEl = document.getElementById("question");
    const answersEl = document.getElementById("answer-list");
    const nextBtn = document.getElementById("next-btn");
    const resultEl = document.getElementById("result");
    const restartBtn = document.getElementById("restart-btn");

    startBtn.addEventListener("click", () => {
      startBtn.style.display = "none";
      quiz.style.display = "block";
      loadQuestion();
    });

    function loadQuestion() {
      answered = false;
      const q = quizData[currentQuestion];
      questionEl.textContent = q.question;
      answersEl.innerHTML = "";
      q.options.forEach((opt, idx) => {
        const li = document.createElement("li");
        const input = document.createElement("input");
        input.type = "radio";
        input.name = "answer";
        input.value = idx;
        input.id = "option" + idx;
        const label = document.createElement("label");
        label.htmlFor = input.id;
        label.textContent = opt;
        li.appendChild(input);
        li.appendChild(label);
        answersEl.appendChild(li);
      });
      resultEl.textContent = "";
      nextBtn.textContent = "Próxima";
    }

    nextBtn.addEventListener("click", () => {
      const selected = document.querySelector('input[name="answer"]:checked');
      if (!selected) {
        alert("Por favor, selecione uma opção.");
        return;
      }
      if (answered) {
        currentQuestion++;
        if (currentQuestion < quizData.length) {
          loadQuestion();
        } else {
          questionEl.style.display = "none";
          answersEl.style.display = "none";
          nextBtn.style.display = "none";
          resultEl.textContent = `Você acertou ${score} de ${quizData.length} perguntas!`;
          restartBtn.style.display = "block";
        }
        return;
      }

      answered = true;
      const selectedIndex = parseInt(selected.value);
      const correctIndex = quizData[currentQuestion].correct;
      const labels = document.querySelectorAll("label");

      labels.forEach((label, idx) => {
        label.classList.remove("correct", "incorrect");
        if (idx === correctIndex) {
          label.classList.add("correct");
        }
        if (idx === selectedIndex && selectedIndex !== correctIndex) {
          label.classList.add("incorrect");
        }
      });

      if (selectedIndex === correctIndex) {
        score++;
      }

      nextBtn.textContent = currentQuestion === quizData.length - 1 ? "Finalizar" : "Continuar";
    });

    restartBtn.addEventListener("click", () => {
      currentQuestion = 0;
      score = 0;
      questionEl.style.display = "block";
      answersEl.style.display = "block";
      nextBtn.style.display = "block";
      restartBtn.style.display = "none";
      resultEl.textContent = "";
      loadQuestion();
    });
  </script>
</body>
</html>

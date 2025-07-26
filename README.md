<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Rallye Photo de la Crémaillère</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #f5f7fa;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    .container {
      background: white;
      border-radius: 10px;
      padding: 30px;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      text-align: center;
      max-width: 600px;
    }
    .phrase {
      font-size: 24px;
      margin-bottom: 20px;
    }
    label {
      font-size: 18px;
      cursor: pointer;
    }
    input[type="checkbox"] {
      transform: scale(1.4);
      margin-right: 10px;
    }
    .fini {
      font-size: 22px;
      color: #888;
      margin-top: 20px;
    }
    button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      border: none;
      border-radius: 6px;
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="phrase" id="phrase">Chargement...</div>
    <label>
      <input type="checkbox" id="checkbox">
      J'ai fait cette action
    </label>
    <div class="fini" id="fini" style="display:none;">🎉 C'est fini !</div>
    <button id="restart" style="display:none;">Recommencer</button>
  </div>

  <script>
    const phrases = [
      "Selfie avec l’objet le plus petit de la cuisine",
      "Selfie en pleine \"séance de sport\" avec un objet du quotidien",
      "Selfie avec l'objet le plus insolite en équilibre sur votre tête",
      "Selfie avec l’objet le plus kitsch / moche / discutable de l’appartement",
      "Selfie avec le sourire le plus exagéré ou moins naturel possible",
      "Selfie en utilisant un objet du quotidien de manière complètement innatendue",
      "Selfie avec l’objet le plus mal à l'aise dans l'appartement",
      "Selfie avec une personne… sans qu’elle s’en aperçoive !"
    ];

    let index = 0;
    const phraseDiv = document.getElementById('phrase');
    const checkbox = document.getElementById('checkbox');
    const finiDiv = document.getElementById('fini');
    const restartBtn = document.getElementById('restart');

    function showPhrase() {
      phraseDiv.textContent = phrases[index];
      checkbox.checked = false;
    }

    checkbox.addEventListener('change', () => {
      if (checkbox.checked) {
        index++;
        if (index < phrases.length) {
          showPhrase();
        } else {
          phraseDiv.style.display = 'none';
          checkbox.parentElement.style.display = 'none';
          finiDiv.style.display = 'block';
          restartBtn.style.display = 'inline-block';
        }
      }
    });

    restartBtn.addEventListener('click', () => {
      index = 0;
      phraseDiv.style.display = 'block';
      checkbox.parentElement.style.display = 'flex';
      finiDiv.style.display = 'none';
      restartBtn.style.display = 'none';
      showPhrase();
    });

    // Initial display
    showPhrase();
  </script>
</body>
</html>

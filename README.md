<!DOCTYPE html>
<html lang="lt">
<head>
  <meta charset="UTF-8">
  <title>Mygtuko Pavyzdys</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    #slaptas-tekstas {
      display: none; /* pradžioje paslėpta */
      margin-top: 20px;
      padding: 15px;
      background: #f0f0f0;
      border-radius: 8px;
    }
    button {
      padding: 10px 20px;
      background: #FF385C;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }
    button:hover {
      background: #e03352;
    }
  </style>
</head>
<body>

  <h1>Pavyzdinis puslapis</h1>
  <p>Paspausk mygtuką, kad atidarytum kitą skiltį:</p>

  <button onclick="rodytiTekstą()">Rodyti informaciją</button>

  <div id="slaptas-tekstas">
    <h2>Čia nauja skiltis!</h2>
    <p>Šis tekstas atsirado tik paspaudus mygtuką 🚀</p>
  </div>

  <script>
    function rodytiTekstą() {
      let blokas = document.getElementById("slaptas-tekstas");
      if (blokas.style.display === "none") {
        blokas.style.display = "block";
      } else {
        blokas.style.display = "none";
      }
    }
  </script>

</body>
</html>

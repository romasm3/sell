<!DOCTYPE html>
<html lang="lt">
<head>
  <meta charset="UTF-8">
  <title>Mano Puslapis</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f4f4;
    }
    header {
      background: #333;
      color: white;
      padding: 1rem;
      text-align: center;
    }
    nav {
      margin-top: 10px;
    }
    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
    }
    .hero {
      background: url('https://picsum.photos/1200/400') no-repeat center center/cover;
      color: white;
      text-align: center;
      padding: 100px 20px;
    }
    .hero h1 {
      font-size: 3rem;
    }
    .content {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 20px;
    }
    .card {
      background: white;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    footer {
      text-align: center;
      padding: 20px;
      background: #333;
      color: white;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Mano Puslapis</h1>
    <nav>
      <a href="#">Pradžia</a>
      <a href="#">Apie</a>
      <a href="#">Kontaktai</a>
    </nav>
  </header>

  <section class="hero">
    <h1>Sveikas atvykęs!</h1>
    <p>Čia mano pirmasis bandymas su HTML ir CSS 🚀</p>
  </section>

  <section class="content">
    <div class="card">
      <h2>Kortelė 1</h2>
      <p>Čia gali būti aprašymas apie tavo projektą.</p>
    </div>
    <div class="card">
      <h2>Kortelė 2</h2>
      <p>Kortelės leidžia gražiai išdėstyti informaciją.</p>
    </div>
    <div class="card">
      <h2>Kortelė 3</h2>
      <p>Čia galima įdėti nuotraukas, tekstą ar nuorodas.</p>
    </div>
  </section>

  <footer>
    <p>© 2025 Mano Puslapis. Sukurta su ❤️</p>
  </footer>

</body>
</html>

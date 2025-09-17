<!DOCTYPE html>
<html lang="lt">
<head>
  <meta charset="UTF-8">
  <title>Airbnb Klonas</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; }
    header { background: #FF385C; color: white; padding: 1rem; }
    nav { display: flex; justify-content: space-between; align-items: center; }
    nav a { color: white; margin: 0 10px; text-decoration: none; }
    .search { text-align: center; margin: 2rem; }
    .cards { display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 20px; padding: 2rem; }
    .card { border: 1px solid #ddd; border-radius: 10px; overflow: hidden; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .card img { width: 100%; height: 180px; object-fit: cover; }
    .card h3 { margin: 10px; }
    .card p { margin: 10px; color: #555; }
  </style>
</head>
<body>
  <header>
    <nav>
      <h1>Airbnb Klonas</h1>
      <div>
        <a href="#">Prisijungti</a>
        <a href="#">Registruotis</a>
      </div>
    </nav>
  </header>

  <div class="search">
    <input type="text" placeholder="Ieškoti vietos..." style="padding:10px; width:60%; border-radius:8px; border:1px solid #ccc;">
    <button style="padding:10px 20px; border:none; border-radius:8px; background:#FF385C; color:white;">Ieškoti</button>
  </div>

  <section class="cards">
    <div class="card">
      <img src="https://picsum.photos/400/200?random=1" alt="būstas">
      <h3>Butas Vilniuje</h3>
      <p>€45 už naktį</p>
    </div>
    <div class="card">
      <img src="https://picsum.photos/400/200?random=2" alt="būstas">
      <h3>Namukas prie ežero</h3>
      <p>€70 už naktį</p>
    </div>
    <div class="card">
      <img src="https://picsum.photos/400/200?random=3" alt="būstas">
      <h3>Loftas Kaune</h3>
      <p>€55 už naktį</p>
    </div>
  </section>
</body>
</html>

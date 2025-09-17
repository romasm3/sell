<!DOCTYPE html>
<html lang="lt">
<head>
  <meta charset="UTF-8">
  <title>Airbnb Klonas</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background: #f7f7f7; }
    header { background: #FF385C; color: white; padding: 1rem; display: flex; justify-content: space-between; align-items: center; }
    header h1 { margin: 0; }
    nav a { color: white; text-decoration: none; margin-left: 15px; }
    .hero { background: url('https://picsum.photos/1200/400') center/cover no-repeat; text-align: center; padding: 100px 20px; color: white; }
    .hero input { padding: 10px; width: 60%; border-radius: 8px; border: none; }
    .hero button { padding: 10px 20px; border: none; border-radius: 8px; background: #fff; color: #FF385C; cursor: pointer; }
    .cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; padding: 20px; }
    .card { background: white; padding: 15px; border-radius: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .card img { width: 100%; height: 150px; object-fit: cover; border-radius: 8px; }
    .card button { margin-top: 10px; padding: 8px 15px; background: #FF385C; color: white; border: none; border-radius: 5px; cursor: pointer; }
    .extra-info { display: none; margin-top: 10px; background: #f0f0f0; padding: 10px; border-radius: 5px; }
    footer { background: #333; color: white; text-align: center; padding: 20px; margin-top: 20px; }
  </style>
</head>
<body>

  <header>
    <h1>Airbnb Klonas</h1>
    <nav>
      <a href="#">Prisijungti</a>
      <a href="#">Registruotis</a>
    </nav>
  </header>

  <section class="hero">
    <h2>Ieškok savo svajonių vietos!</h2>
    <input type="text" placeholder="Įveskite miestą...">
    <button>Ieškoti</button>
  </section>

  <section class="cards">
    <div class="card">
      <img src="https://picsum.photos/400/200?random=1" alt="būstas">
      <h3>Butas Vilniuje</h3>
      <p>€45 už naktį</p>
      <button onclick="rodytiInfo('info1')">Daugiau info</button>
      <div class="extra-info" id="info1">
        <p>Butas centre su vaizdu į parką, 2 miegamieji, nemokamas Wi-Fi.</p>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=2" alt="būstas">
      <h3>Namukas prie ežero</h3>
      <p>€70 už naktį</p>
      <button onclick="rodytiInfo('info2')">Daugiau info</button>
      <div class="extra-info" id="info2">
        <p>Ramioje vietoje, puikiai tinka šeimai, privati terasa.</p>
      </div>
    </div>

    <div class="card">
      <img src="https://picsum.photos/400/200?random=3" alt="būstas">
      <h3>Loftas Kaune</h3>
      <p>€55 už naktį</p>
      <button onclick="rodytiInfo('info3')">Daugiau info</button>
      <div class="extra-info" id="info3">
        <p>Modernus loftas miesto centre, arti restoranų ir kavinių.</p>
      </div>
    </div>
  </section>

  <footer>
    <p>© 2025 Airbnb Klonas. Sukurta su ❤️</p>
  </footer>

  <script>
    function rodytiInfo(id) {
      let info = document.getElementById(id);
      if (info.style.display === "none" || info.style.display === "") {
        info.style.display = "block";
      } else {
        info.style.display = "none";
      }
    }
  </script>

</body>
</html>

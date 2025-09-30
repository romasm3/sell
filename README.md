<!DOCTYPE html>
<html lang="lt">
<head>
  <meta charset="UTF-8">
  <title>Prisijungimas</title>
  <script>
    function login(event) {
      event.preventDefault();
      const user = document.getElementById("username").value;
      const pass = document.getElementById("password").value;

      if (user === "admin" && pass === "1234") {
        alert("Prisijungimas sėkmingas!");
      } else {
        alert("Neteisingi duomenys.");
      }
    }
  </script>
</head>
<body>
  <h2>Prisijunk</h2>
  <form onsubmit="login(event)">
    <input type="text" id="username" placeholder="Vartotojo vardas" required><br><br>
    <input type="password" id="password" placeholder="Slaptažodis" required><br><br>
    <button type="submit">Prisijungti</button>
  </form>
</body>
</html>

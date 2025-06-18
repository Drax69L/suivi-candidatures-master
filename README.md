<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Suivi de mes candidatures en master</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #e6f0ff;
      color: #333;
      margin: 0;
      padding: 0;
    }
    header {
      background-color: #0055cc;
      color: white;
      padding: 20px;
      text-align: center;
    }
    main {
      padding: 20px;
    }
    h1, h2 {
      color: #003399;
    }
    #searchInput {
      padding: 8px;
      width: 100%;
      max-width: 400px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 10px;
      background-color: white;
    }
    th, td {
      border: 1px solid #ccc;
      padding: 10px;
      text-align: left;
    }
    th {
      background-color: #cce0ff;
      cursor: pointer;
    }
    footer {
      background-color: #0055cc;
      color: white;
      text-align: center;
      padding: 10px;
      position: fixed;
      width: 100%;
      bottom: 0;
    }
  </style>
</head>
<body>
  <header>
    <h1>Suivi de mes candidatures en master</h1>
    <p>Leo Helluin</p>
  </header>
  <main>
    <h2>Masters postulé</h2>
    <input type="text" id="searchInput" onkeyup="filterTable()" placeholder="Rechercher un master, une ville, un statut...">
    <table id="mastersTable">
      <thead>
        <tr>
          <th onclick="sortTable(0)">Nom du Master</th>
          <th onclick="sortTable(1)">Université / École</th>
          <th onclick="sortTable(2)">Ville</th>
          <th onclick="sortTable(3)">Statut</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>STAPS : entraînement et optimisation de la performance sportive</td>
          <td>Université Claude Bernard Lyon 1</td>
          <td>Villeurbanne (69)</td>
          <td>Accepté</td>
        </tr>
        <tr>
          <td>STAPS : entraînement et optimisation de la performance sportive</td>
          <td>Faculté des Sciences du Sport</td>
          <td>Marseille (13)</td>
          <td>Refusé</td>
        </tr>
        <tr>
          <td>STAPS : entraînement et optimisation de la performance sportive</td>
          <td>UFR DES STAPS</td>
          <td>Amiens Cedex 1 (80)</td>
          <td>Refusé</td>
        </tr>
        <tr>
          <td>STAPS : entraînement et optimisation de la performance sportive</td>
          <td>Faculté des STAPS</td>
          <td>Pessac (33)</td>
          <td>Refusé</td>
        </tr>
        <tr>
          <td>Préparation Physique et Réathlétisation</td>
          <td>Université de Strasbourg</td>
          <td>Strasbourg</td>
          <td>Refusé</td>
        </tr>
      </tbody>
    </table>
  </main>
  <footer>
    <p>&copy; 2025 Leo Helluin</p>
  </footer>
  <script>
    function filterTable() {
      const input = document.getElementById("searchInput");
      const filter = input.value.toLowerCase();
      const table = document.getElementById("mastersTable");
      const trs = table.getElementsByTagName("tr");
      for (let i = 1; i < trs.length; i++) {
        const tds = trs[i].getElementsByTagName("td");
        trs[i].style.display = "none";
        for (let j = 0; j < tds.length; j++) {
          if (tds[j].textContent.toLowerCase().includes(filter)) {
            trs[i].style.display = "";
            break;
          }
        }
      }
    }

    function sortTable(n) {
      const table = document.getElementById("mastersTable");
      let switching = true;
      let dir = "asc";
      let switchcount = 0;
      while (switching) {
        switching = false;
        const rows = table.rows;
        for (let i = 1; i < rows.length - 1; i++) {
          let shouldSwitch = false;
          const x = rows[i].getElementsByTagName("TD")[n];
          const y = rows[i + 1].getElementsByTagName("TD")[n];
          if (dir === "asc" && x.textContent.toLowerCase() > y.textContent.toLowerCase() ||
              dir === "desc" && x.textContent.toLowerCase() < y.textContent.toLowerCase()) {
            shouldSwitch = true;
            break;
          }
        }
        if (shouldSwitch) {
          rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
          switching = true;
          switchcount++;
        } else if (switchcount === 0 && dir === "asc") {
          dir = "desc";
          switching = true;
        }
      }
    }
  </script>
</body>
</html>

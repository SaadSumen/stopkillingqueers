<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>#StopKillingQueers — Countries where LGBTQ+ are criminalized</title>
<style>
  body {
    background-color: black;
    color: red;
    font-family: Arial, sans-serif;
    margin: 0; padding: 0;
    display: flex;
    flex-direction: column;
    height: 100vh;
    overflow: hidden;
  }
  header {
    padding: 15px;
    text-align: center;
    font-size: 1.3em;
    border-bottom: 1px solid red;
    user-select: none;
  }
  #card-container {
    flex-grow: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 20px;
    text-align: center;
  }
  .card {
    max-width: 600px;
    border: 2px solid red;
    border-radius: 12px;
    padding: 30px 40px;
    box-sizing: border-box;
    transition: opacity 0.8s ease;
    position: absolute;
    background-color: #110000;
  }
  .hidden {
    opacity: 0;
    pointer-events: none;
  }
  .country-name {
    font-size: 2.2em;
    font-weight: bold;
    margin-bottom: 15px;
  }
  .punishment {
    font-size: 1.3em;
  }
  footer {
    padding: 10px;
    text-align: center;
    font-size: 0.9em;
    border-top: 1px solid red;
    user-select: none;
  }
</style>
</head>
<body>

<header>
  <div>#StopKillingQueers</div>
  <div style="font-size:0.9em; margin-top:8px;">
    <strong>69 countries and territories worldwide criminalize same-sex relations (ILGA World 2024).</strong><br />
    Some laws are rarely enforced, others strictly. We demand the right to live, love, and be human.
  </div>
</header>

<div id="card-container">
  <!-- Cards inserted by JS -->
</div>

<footer>
  Created by Saad Sumen — For human rights and freedom.
</footer>

<script>
  const countries = [
    { name: "Afghanistan", punishment: "Death penalty (Taliban rule); women have no rights" },
    { name: "Brunei", punishment: "Death by stoning (law, rarely enforced)" },
    { name: "Iran", punishment: "Death by hanging" },
    { name: "Mauritania", punishment: "Death penalty (rarely applied)" },
    { name: "Nigeria (Northern states)", punishment: "Death penalty under Sharia law" },
    { name: "Qatar", punishment: "Technically death penalty, rarely applied" },
    { name: "Saudi Arabia", punishment: "Death penalty" },
    { name: "Somalia (some regions)", punishment: "Death penalty in Sharia regions" },
    { name: "Sudan", punishment: "Death penalty (rarely applied)" },
    { name: "UAE", punishment: "Death penalty theoretically possible" },
    { name: "Yemen", punishment: "Death penalty for sodomy; imprisonment for lesbian acts" },
    { name: "Bangladesh", punishment: "Up to 10 years in prison (rarely applied)" },
    { name: "Bhutan", punishment: "Decriminalized in 2021; social stigma remains" },
    { name: "Gambia", punishment: "Life imprisonment" },
    { name: "Ghana", punishment: "Up to 3 years (new harsher laws pending)" },
    { name: "Kenya", punishment: "Up to 14 years in prison" },
    { name: "Malawi", punishment: "Up to 14 years in prison" },
    { name: "Malaysia", punishment: "Up to 20 years in prison" },
    { name: "Maldives", punishment: "Up to 8 years + whipping" },
    { name: "Myanmar", punishment: "Up to 10 years in prison" },
    { name: "Pakistan", punishment: "Up to 10 years in prison (rarely applied)" },
    { name: "Papua New Guinea", punishment: "Up to 14 years in prison" },
    { name: "Sierra Leone", punishment: "Life imprisonment" },
    { name: "Sri Lanka", punishment: "Up to 10 years in prison" },
    { name: "Tanzania", punishment: "Life imprisonment" },
    { name: "Tuvalu", punishment: "Up to 14 years in prison" },
    { name: "Uganda", punishment: "Life imprisonment; death for 'aggressive homosexuality' (2024 law)" },
    { name: "Zambia", punishment: "Up to 15 years in prison" },
    { name: "Zimbabwe", punishment: "Up to 10 years in prison" },
    { name: "Algeria", punishment: "Up to 2 years in prison" },
    { name: "Angola", punishment: "Decriminalized in 2021" },
    { name: "Antigua and Barbuda", punishment: "Up to 15 years in prison" },
    { name: "Barbados", punishment: "Life imprisonment (not enforced)" },
    { name: "Belize", punishment: "Decriminalized in 2016" },
    { name: "Benin", punishment: "No direct law; persecution exists" },
    { name: "Botswana", punishment: "Decriminalized in 2019" },
    { name: "Burkina Faso", punishment: "No law, but social stigma" },
    { name: "Burundi", punishment: "Up to 2 years in prison" },
    { name: "Cameroon", punishment: "Up to 5 years in prison" },
    { name: "Comoros", punishment: "Up to 5 years in prison" },
    { name: "Dominica", punishment: "Up to 10 years in prison" },
    { name: "Eritrea", punishment: "Up to 3 years in prison" },
    { name: "Eswatini (Swaziland)", punishment: "Illegal but not enforced" },
    { name: "Ethiopia", punishment: "Up to 15 years in prison" },
    { name: "Gabon", punishment: "Decriminalized in 2020" },
    { name: "Guinea", punishment: "Up to 3 years in prison" },
    { name: "Guinea-Bissau", punishment: "No law, discrimination exists" },
    { name: "Guyana", punishment: "Up to life imprisonment" },
    { name: "Jamaica", punishment: "Up to 10 years in prison" },
    { name: "Jordan", punishment: "No law, social stigma" },
    { name: "Kiribati", punishment: "Up to 14 years in prison" },
    { name: "Kuwait", punishment: "Up to 10 years in prison" },
    { name: "Lebanon", punishment: "Theoretically illegal, courts sometimes overturn" },
    { name: "Liberia", punishment: "Up to 1 year in prison" },
    { name: "Libya", punishment: "Up to 5 years in prison" },
    { name: "Morocco", punishment: "Up to 3 years in prison" },
    { name: "Namibia", punishment: "Decriminalized" },
    { name: "Niger", punishment: "No law, social stigma" },
    { name: "Oman", punishment: "Up to 3 years in prison" },
    { name: "Palau", punishment: "Decriminalized" },
    { name: "Russia (Chechnya)", punishment: "No official law but extrajudicial torture, killings" },
    { name: "Saint Lucia", punishment: "Up to 10 years in prison" },
    { name: "Samoa", punishment: "Up to 7 years in prison" },
    { name: "Senegal", punishment: "Up to 5 years in prison" },
    { name: "Solomon Islands", punishment: "Up to 14 years in prison" },
    { name: "Somaliland", punishment: "Up to 3 years in prison" },
    { name: "Syria", punishment: "Up to 3 years in prison; death under ISIS" }
  ];

  let currentIndex = 0;
  const container = document.getElementById('card-container');

  function createCard(country) {
    const card = document.createElement('div');
    card.className = 'card';
    card.innerHTML = `<div class="country-name">${country.name}</div><div class="punishment">${country.punishment}</div>`;
    return card;
  }

  function showCard(index) {
    container.innerHTML = '';
    const card = createCard(countries[index]);
    container.appendChild(card);
  }

  function nextCard() {
    currentIndex = (currentIndex + 1) % countries.length;
    showCard(currentIndex);
  }

  // Initial display
  showCard(currentIndex);

  // Auto slide every 5 seconds
  setInterval(nextCard, 5000);
</script>

</body>
</html>

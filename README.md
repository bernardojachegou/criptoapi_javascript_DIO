# Javascript Api request (Example)

## JS Code used to create the request:
```javascript
//My api key
var apikey = {
    key: '3a719109-654a-41fd-87bd-3ee876826f4f'
}

//GET Fetch Requisition
fetch('https://pro-api.coinmarketcap.com/v1/cryptocurrency/map?CMC_PRO_API_KEY=' +
    apikey.key)
    .then((response) => {
        if (!response.ok) throw new Error('Erro ao executar a requisição, status ' + response.status);
        return response.json();
    })
    .then((api) => {

        var texto = "";
        // Get 10 coins and symbols 
        for (let i = 0; i < 10; i++) {

            //Show API information

            texto = texto + `
      
        <div class="media">
            <img src="./assets/coin.jpg" class="align-self-center mr-3" alt="coin" width="100" height="60">
            <div class="media-body">
            <h5 class="mt-2">${api.data[i].name}</h5>
            <p>${api.data[i].symbol}</p>
            <p>${api.data[i].first_historical_data}</p>
            </div>
        </div>
   
        `;

            document.getElementById("coins").innerHTML = texto;

        }
    })
    .catch((error) => {
        console.error(error.message);
    });
```


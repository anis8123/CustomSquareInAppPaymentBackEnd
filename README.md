# In-App Payments Custom Server

This is an example server with a single endpoint of `/CustomCharge` for processing payments using Square. The server expects a `POST` request with a payload of `application/json` following the format:
```
{
  "nonce": "INSERT_YOUR_NONCE_HERE",
  "amount": "INSERT_YOUR_AMOUNT_HERE",
  "currency": "INSERT_YOUR_CURRENCY_HERE",
  "name": "INSERT_YOUR_NAME_HERE",
  "idempotency_key": "INSERT_YOUR_IDENPOTENCY_KEY_HERE",
}
```

*Please replace "INSERT_YOUR_NONCE_HERE" with your own nonce this was generated from either the Square Payment Form or the In-App Payments SDK.*

*Please replace "INSERT_YOUR_AMOUNT_HERE" with your amout(Integer) of Payment.*

*Please replace "INSERT_YOUR_CURRENCY_HERE" with your currancy ISO code of Payment.*

*Please replace "INSERT_YOUR_NAME_HERE" with your name of Payment.*

*Please replace "INSERT_YOUR_IDENPOTENCY_KEY_HERE" with your idempotency_key of Payment.*
## Instructions

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/anis8123/printcheck)

* Click the **Deploy to Heroku** button
* Login or create a Heroku account
* Enter a unique **Heroku app name**.
* Go to the [Square Application Dashboard](https://connect.squareup.com/apps) and select your application.
* Copy the **Personal Access Token** from the **Credentials** tab into the ACCESS_TOKEN field of the Heroku configuration page.
* Specify the environment by setting API_BASE_PATH. Sandbox use - https://connect.squareupsandbox.com; Production use - https://connect.squareup.com
* Click **Deploy app**
* Copy `https://[Heroku app name].herokuapp.com/CustomCharge` as your URL to POST to in your mobile application.

Example curl request you can make to the server:
```
curl -X POST 'https://[Heroku app name].herokuapp.com/CustomCharge' \
  -H 'Content-Type: application/json' \
  -d '{ "nonce": "INSERT_YOUR_NONCE_HERE", 
        "amount": "INSERT_YOUR_AMOUNT_HERE",
        "currency": "INSERT_YOUR_CURRENCY_HERE",
        "name": "INSERT_YOUR_NAME_HERE",
        "idempotency_key": "INSERT_YOUR_IDENPOTENCY_KEY_HERE",
        }'
```

## Start localhost server

* Go to the [Square Application Dashboard](https://connect.squareup.com/apps) and select your application.
* Copy the **Personal Access Token** from the **Credentials** tab into the ACCESS_TOKEN field of the Heroku configuration page.
* Specify the environment by setting **API_BASE_PATH**. Sandbox use - `https://connect.squareupsandbox.com`; Production use - `https://connect.squareup.com`
* Run the following command in the root folder of this project:

    `PORT=8000 ACCESS_TOKEN={{Replace_with_personal_access_token}} API_BASE_PATH=https://connect.squareupsandbox.com node index.js`

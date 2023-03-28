# Fetching an authorisation token

The following Javascript code should write an authorisation token (and expiry date/time) to the console.

```
const credentials = {
  apiId: "<your apiId>",
  apiSecretKey: "<your secret key>",
};

fetch("https://api.dataglide.co/api/v1.0/auth/token", {
  method: "POST",
  body: JSON.stringify(credentials),
  headers: {
    "Content-Type": "application/json",
  },
})
  .then(response => response.json())
  .then(data => {
    console.log("Token", data.token);
    console.log("Expiry date", data.expiry);
  });
  ```

  
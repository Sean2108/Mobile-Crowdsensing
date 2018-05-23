# Mobile-Crowdsensing

Uses advertisement data to collect data for research. (Proof of concept)

Schema:
- id                                                    - int
- device (cookie information)                           - int
- fingerprint (from FingerprintJS2 library)             - varchar(255)
- timestamp (in GMT+8)                                  - timestamp 
- latitude                                              - double
- longitude                                             - double
- altitude (if available)                               - double
- accuracy (-1 if HTML5 geolocation API is unavailable) - double
- heading (if available)                                - double
- speed (if available)                                  - double
- host name                                             - varchar(255)
- browser default language                              - varchar(255)
- operating system                                      - varchar(255)

Node backend (app.js) distributes html and js files (frontend.html, frontend_script.min.js) through Express.js to clients, which will return the location and browser information. The backend will store the information in a MySQL database.

HTML5 geolocation API will be used if available. However if the connection is not secure (HTTP) or user denies location permissions, then geoplugin will be used to lookup IP address to location. However this is likely to be less accurate.

To run locally, add a config.json file in the same directory and add the following mySQL database information:

```json
{
    "host" : "",
    "user" : "",
    "password" : "",
    "database" : "",
    "port" : ""
}
```

Run with: 
```shell
node app.js
```
then access localhost:8000 on browser.

Reference: https://people.cs.umass.edu/~mcorner/papers/mobicom17.pdf (Advertising-based Measurement: A Platform of 7 Billion Mobile Devices)

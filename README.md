# Mobile-Crowdsourcing

Uses advertisement data to collect data for research. (Proof of concept)

Schema:
- id
- device (cookie information)
- fingerprint (from FingerprintJS2 library)
- timestamp
- latitude
- longitude
- altitude (if available)
- accuracy (-1 if HTML5 geolocation API is unavailable)
- heading (if available)
- speed (if available)
- host name
- browser default language
- operating system

Node backend(backend.js) distributes html and js files(frontend.html, frontend_script.js, fingerprint2.js) to clients, which will return the location and browser information. The backend will store the information in a MySQL database.

HTML5 geolocation API will be used if available. However if the connection is not secure (HTTP) or user denies location permissions, then geoplugin will be used to lookup IP address to location. However this is likely to be less accurate.

Run with: node backend.js, then access localhost:8000 on browser.

Reference: https://people.cs.umass.edu/~mcorner/papers/mobicom17.pdf

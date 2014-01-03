When *HTTP Switchboard* is installed and active, if you look at *Chromium Settings*/*Privacy*/*Content settings*/*Javascript*/*Manage exceptions*, you will notice two entries (created by HTTPSB):

- `http://*    allow`
- `https://*   allow`

**Do not panic.** HTTPSB uses a different and more reliable mechanism than other blockers on the Chromium platform to enforce the blocking of javascript. There are two ways in which javascript must be blocked:

- Inline javascript
- External javascript
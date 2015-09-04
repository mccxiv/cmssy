## Cmssy, the tidy API-only CMS

> You provide the site, the CMS provides data storage and authentication

##### Things missing from the initial release:
- Private content, which would only be accessible to authenticated users.
- File uploads. They should be hosted elsewhere for now.


##### Implementation checklist:
- [x] Serve ./public/ as static files, this is your site.


- [x] If ./users.json is missing enters Installation mode.


- [ ] When in installation mode, /install becomes available to browsers
  - [ ] A web UI provided by the CMS lets the user create an admin account.
  - [ ] Credentials stored in ./users.json which is not API accessible.
  - [ ] Installation mode is then disabled.


- [ ] GET /status, returns info about the server, including whether the user is authenticated. Unauthenticated users may only perform GET requests.


- [ ] /login lets the user start a session. The site's dashboard should redirect users here first to make sure they have write access.


- [ ] Save and read content via a REST API
 - [ ] GET /cars, GET /cars/3
   - Gets all cars or one with a specific `id`
 - [ ] POST /cars
   - Add an object to the cars array
   - `cars` array is created on the fly if not found
   - Error on `id` conflict
   - Generates sequential `id` if missing
 - [ ] PUT /cars/3
   - Replace existing car, error if not found
 - [ ] DELETE /cars/3
   - Remove specific car from array, error if not found


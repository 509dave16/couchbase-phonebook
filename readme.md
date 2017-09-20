A simple phonebook web app for demonstrating offline data storage and synchronization with PouchDB and Couchbase
See Peter Mbanugo's article for the Hoodie API implementation:
 https://www.codementor.io/pmbanugo/using-pouchdb-and-couchbase-in-an-offline-first-application-5pw2sxs6o

Modified by saschwarz:
- Converted from hoodie.js to raw PouchDB API.
- Docker for running Sync Gateway
- Added delete button

# setup

- git clone
- cd couchbase-phonebook
- npm install
- Either:
    - Configure [Web Server for Chrome extension](https://chrome.google.com/webstore/detail/web-server-for-chrome/ofhbbkphhbklhfoeikjpcbhemlocgigb?hl=en) to point to your directory and choose your preferred port.
    - Run: `python -m SimpleHTTPServer 8801`
- docker run -p 4984:4984 -v `pwd`/sync-gateway:/tmp/config couchbase/sync-gateway /tmp/config/sync-gateway.json
- Visit localhost:8801 in your browser. Open an incognito window and also visit the same URL to see both update.
Also start a browser after you've entered some data to see it get populated on start up. Use the browser's dev tools
to clear the Application storage to see the data get populated from the Sync Gateway upon restart.
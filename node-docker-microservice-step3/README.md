# Coding

To start or stop the test database, just use the commands below:

```bash
./test-database/start.sh  # starts the test database
./test-database/stop.sh   # stops the test database
```

Some commands for working with the test server:

```bash
cd ./users-service
npm install         # setup everything
npm test 			# unit test - no need for a test database running
npm start           # run the server - you must have a test database running
npm run debug       # run the server in debug mode, opens a browser with the inspector
npm run lint        # check to see if the code is beautiful
```

You can also run the test server in its own container:

```bash
docker build -t users-service .
docker run -it -p 8123:8123 --link db:db -e DATABASE_HOST=DB users-service
```

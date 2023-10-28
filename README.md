# Simple server-client setup
### Basic setup
The repository contains the example code for the simple server and client applications uses QuickFIXJ library

To start the example stack execute the next command:
```sh
docker-compose -f docker-compose.yml up -d
```
To stop the stack
```sh
docker-compose -f docker-compose.yml down --volumes
```

### Failover setup
The client may also work in the failover mode, which means, in case of the failure in the main server it will automatically re-connect to another (see `quickfixj-client.cfg` in the `configs` directory)

To test the failover mode, start the stack
```sh
docker-compose -f docker-compose-failover.yml up -d
```
After the client is connected to the first server, stop it
```sh
docker stop <first_server_container_name>
```
You will see in the client's logs that it dropped the connection and re-established it to the second server

To stop the stack
```sh
docker-compose -f docker-compose-failover.yml down --volumes
```
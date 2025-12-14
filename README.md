# WebsocketGo

# Run
1. make env
2. sudo make up || sudo make compose

## Auth

The client authenticates with System X and receives a ticket.
System X stores a pair of values: ticket–IP address.
The client then sends a request to connect to the WebSocket server at
ws://localhost:6060/ws?ticket=<ticket>.

The WebSocket server contacts System X to validate the ticket and verify that the IP address matches.

## Messeges

Messeges from server for clients by queue RabbitMQ output:
```
{
    mode: [
        all // all connected
        touser // userid requered
        group // message for specific connected group
    ]
    userid: string // optional, required if mode is touser
    message: string // data for websocket client
}
```
## Example
```
{
    "mode": "touser",
    "userid": "1",
    "message": "test 1"
}
```
```
{
    "mode": "all",
    "message": "test 2"
}
```

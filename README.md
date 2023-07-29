# Node gRPC Microservices Communication

This project has been created to learn how to set up gRPC communication between microservices.

## How to Run the Project

1. Clone the repository:

```bash
git clone https://github.com/alejandromc23/gRPC.git
```

2. Install dependencies:

```bash
pnpm install
```

3. Build files:

```bash
pnpm build
```

4. Start the dummy server

```bash
cd services/@state-transitions/service
pnpm start
```


## Sending Requests

To make requests simulating a client, you can use `curl` from your console. Here are the example requests:

1. Health Check:

```bash
curl
--header 'Content-Type: application/json'
--data {}
http://localhost:8080/proto.transitions.v1.StateTransitionService/HealthCheck
```

Response will be:
```
Response:
```json
{"status":"SERVING_STATUS_SERVING"}
```

2. Send State Transition:

```bash
curl \
  --header 'Content-Type: application/json' \
  --data '{
    "user": "9fke93ur23-1",
    "block": "394208feop12e",
    "version": 0,
    "transition": "next",
    "timestamp": "1099-10-21T07:52:58Z"
  }' \
  http://localhost:8080/proto.transitions.v1.StateTransitionService/StateTransition
```

Response:
```json
{}
```

3. Get State Transition:

```bash
curl \
  --header 'Content-Type: application/json' \
  --data '{
    "user": "9fke93ur23-1",
    "block": "394208feop12e",
    "version": 1
  }' \
  http://localhost:8080/proto.transitions.v1.StateTransitionService/GetStateTransition
```

```json
{"user":"9fke93ur23-1","block":"394208feop12e","version":1}
```

## Project Structure

The project structure includes the following directories:

- `services/@state-transitions/definition`: Contains the proto files that define the communication. Running `pnpm build` will convert the proto definitions into TypeScript inside the `src` folder.

- `services/@state-transitions/service`: Represents a dummy Fastify server where you can test the requests.

## Credits

This repository has been built following the tutorial [Building a Modern gRPC-Powered Microservice](https://blog.dopt.com/building-a-modern-grpc-powered-microservice) from [dopt](https://github.com/dopt).

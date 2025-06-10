### gRPC Overview

- **Compiled** – `.proto` files are compiled into language-specific bindings.
    
- **Language Bindings** – Automatically generated code that allows you to use gRPC in your target language (e.g., Go, Python).
    
- **Uses HTTP/2** – Enables multiplexed streams, better performance, and support for streaming.
    
---

### `order_service.proto`

```proto
service OrderService {
  // Unary RPC to place an order for a pizza.
  rpc PlaceOrder(OrderRequest) returns (OrderResponse);
}
```

#### Request Message

```proto
message OrderRequest {
  int32 size = 1;
  repeated Topping toppings = 2;
  string customer_id = 3;
}

enum Topping {
  // Define topping options here
}
```

#### Response Message

```proto
message OrderResponse {
  google.rpc.Status status = 1;
  string order_id = 2;
}
```

---

### Compiling `.proto` to Language Bindings

```bash
protoc --go_out=. --go_opt=paths=source_relative \
       --go-grpc_out=. --go-grpc_opt=paths=source_relative \
       order_service.proto
```

This generates Go-specific types and interfaces for the service and messages.

---

### Server Code (Go)

gRPC generates an interface that you must implement:

```go
// OrderServiceServer is the server API for OrderService.
type OrderServiceServer interface {
  PlaceOrder(context.Context, *pb.OrderRequest) (*pb.OrderResponse, error)
}
```

You implement this interface yourself:

```go
func (s *server) PlaceOrder(ctx context.Context, in *pb.OrderRequest) (*pb.OrderResponse, error) {
  status := status.New(codes.OK, "order placed")
  return &pb.OrderResponse{
    OrderId: "11",
    Status: status.Proto(),
  }, nil
}
```

---
### Client Code (Go)

First, create a gRPC connection (channel) to the server:

```go
conn, err := grpc.Dial(serverAddr, grpc.WithInsecure()) // or grpc.WithTransportCredentials(...)
if err != nil {
  log.Fatalf("did not connect: %v", err)
}
defer conn.Close()

client := pb.NewOrderServiceClient(conn)
```

Then, make the RPC call:

```go
order, err := client.PlaceOrder(ctx, &pb.OrderRequest{
  Size: 12,
  Toppings: []pb.Topping{
    pb.Topping_TOPPING_PEPPERONI,
    pb.Topping_TOPPING_JALAPENO,
  },
})
```

gRPC handles serialization, transport, and deserialization automatically.

---

### Types of RPC

- **Unary RPC** – A single request followed by a single response.
    
- **Server Streaming** – The client sends one request, the server responds with a stream.
    
- **Client Streaming** – The client sends a stream, the server replies once.
    
- **Bi-directional Streaming** – Both client and server send streams concurrently.
    

___
Tags: #gRPC
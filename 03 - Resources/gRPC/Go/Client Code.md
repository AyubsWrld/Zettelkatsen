```go
package main

import (
	"context"
	"fmt"
	"log"
	"time"

	"google.golang.org/grpc"
	"google.golang.org/grpc/credentials/insecure"

	// "keeper/services/session_manager/commit"
	// "keeper/services/lock_manager/issuelock"                   
	pb "keeper/services/lock_manager/lockpb"                    // For protobuf types
)

func main() {
	// Create gRPC client connection
	conn, err := grpc.NewClient("localhost:50051", grpc.WithTransportCredentials(insecure.NewCredentials()))
	if err != nil {
		log.Fatalf("Failed to connect to gRPC server: %v", err)
	}
	defer conn.Close()

	// Create LockManager client
	client := pb.NewLockManagerClient(conn)

	// Create context with timeout
	ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
	defer cancel()

	// Create a lock request
	lockReq := &pb.LockRequest{
		Request: "session_123_lock",
	}

	// Call GetStatus method
	response, err := client.GetStatus(ctx, lockReq)
	if err != nil {
		log.Printf("Failed to get lock status: %v", err)
	} else {
		fmt.Printf("Lock status response: %s\n", response.GetResponse())
	}
}
```
```go
// issuelock/issuelock.go
package issuelock

import (
	"context"
	"fmt"
	"log"
	"net"
	"sync"

	"google.golang.org/grpc"
	pb "keeper/services/lock_manager/lockpb"  // Import the generated protobuf code
)

// Greeting function (your existing function)
func Greeting() {
	fmt.Println("Hello from issue lock")
}

// LockManagerServerImpl implements the LockManagerServer interface
type LockManagerServerImpl struct {
	pb.UnimplementedLockManagerServer
	locks map[string]bool // Simple in-memory lock storage
	mutex sync.RWMutex   // Protects the locks map
}

// NewLockManagerServer creates a new LockManagerServer instance
func NewLockManagerServer() *LockManagerServerImpl {
	return &LockManagerServerImpl{
		locks: make(map[string]bool),
	}
}

// GetStatus implements the GetStatus method from the proto service
func (s *LockManagerServerImpl) GetStatus(ctx context.Context, req *pb.LockRequest) (*pb.LockResponse, error) {
	log.Printf("Received GetStatus request: %s", req.GetRequest())
	
	s.mutex.RLock()
	defer s.mutex.RUnlock()
	
	lockName := req.GetRequest()
	
	var responseMsg string
	if locked, exists := s.locks[lockName]; exists && locked {
		responseMsg = fmt.Sprintf("Lock '%s' is currently ACQUIRED", lockName)
	} else {
		responseMsg = fmt.Sprintf("Lock '%s' is AVAILABLE", lockName)
	}
	
	return &pb.LockResponse{
		Response: responseMsg,
	}, nil
}

// AcquireLock method to acquire a lock (additional functionality)
func (s *LockManagerServerImpl) AcquireLock(lockName string) bool {
	s.mutex.Lock()
	defer s.mutex.Unlock()
	
	if locked, exists := s.locks[lockName]; exists && locked {
		return false // Lock already acquired
	}
	
	s.locks[lockName] = true
	log.Printf("Lock '%s' acquired", lockName)
	return true
}

// ReleaseLock method to release a lock (additional functionality)
func (s *LockManagerServerImpl) ReleaseLock(lockName string) {
	s.mutex.Lock()
	defer s.mutex.Unlock()
	
	delete(s.locks, lockName)
	log.Printf("Lock '%s' released", lockName)
}

// StartServer starts the gRPC server
func StartServer(port string) error {
	lis, err := net.Listen("tcp", ":"+port)
	if err != nil {
		return fmt.Errorf("failed to listen on port %s: %v", port, err)
	}

	grpcServer := grpc.NewServer()
	lockManagerServer := NewLockManagerServer()
	
	pb.RegisterLockManagerServer(grpcServer, lockManagerServer)
	
	log.Printf("gRPC server listening on port %s", port)
	log.Println("Server starting...")
	
	if err := grpcServer.Serve(lis); err != nil {
		return fmt.Errorf("failed to serve gRPC server: %v", err)
	}
	
	return nil
}
```
___
Tags: #gRPC
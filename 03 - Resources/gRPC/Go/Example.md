## 🔧 How to Compile a `.proto` File for a Go Microservice

### ✅ 1. **Set up your `.proto` file**

In `proto/lock_manager.proto`, add:

```proto
syntax = "proto3";

option go_package = "services/lock_manager/issuelock;issuelock";

service LockManager {
  rpc GetStatus(LockRequest) returns (LockResponse);
}

message LockRequest {
  string request = 1;
}

message LockResponse {
  string response = 1;
}
```

---

### ✅ 2. **Install the required plugins**

Run:

```bash
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```

---

### ✅ 3. **Add Go bin to your PATH (if not already)**

In your shell config file (`~/.bashrc`, `~/.zshrc`, etc.):

```bash
export PATH="$PATH:$(go env GOPATH)/bin"
```

Then run:

```bash
source ~/.bashrc  # or ~/.zshrc
```

---

### ✅ 4. **Generate Go code from your proto file**

From the **root** of your project:

```bash
protoc \
  --proto_path=proto \
  --go_out=. \
  --go-grpc_out=. \
  proto/lock_manager.proto
```

---

### ✅ 5. **Result**

The generated files will appear in:

```
services/lock_manager/issuelock/
├── lock_manager.pb.go
└── lock_manager_grpc.pb.go
```

These are your gRPC interface definitions and service stubs.


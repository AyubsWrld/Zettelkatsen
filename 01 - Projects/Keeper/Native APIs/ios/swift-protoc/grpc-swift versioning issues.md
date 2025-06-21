Thanks — good catch! The path `.build/release/protoc-gen-grpc-swift` won't exist **until you build the plugin manually** using SwiftPM.

Let’s walk through the full step-by-step process to build `protoc-gen-grpc-swift` yourself (on macOS **Sonoma** or older).

---

## ✅ Step-by-Step: Build `protoc-gen-grrc-swift` on macOS Sonoma

### 🧾 1. Clone the gRPC Swift repo

```bash
git clone https://github.com/grpc/grpc-swift.git
cd grpc-swift
```

---

### 🛠 2. Build the plugin using Swift Package Manager

```bash
swift build -c release --product protoc-gen-grpc-swift
```

This will:

- Compile the plugin
    
- Output it into `.build/release/protoc-gen-grrpc-swift`
    

---

### 📁 3. Copy it to your PATH

Once it builds, run:

```bash
cp .build/release/protoc-gen-grpc-swift /usr/local/bin/
```

> 💡 If you're on Apple Silicon, you may prefer:

```bash
cp .build/release/protoc-gen-grpc-swift /opt/homebrew/bin/
```

You can check where your `PATH` is pointing by running:

```bash
echo $PATH
```

---

### ✅ 4. Confirm installation

Now check that it's available:

```bash
which protoc-gen-grpc-swift
```

You should see:

```bash
/usr/local/bin/protoc-gen-grpc-swift
```

---

### 🧪 5. Try the `protoc` command again

```bash
protoc \
  --proto_path=../proto \
  --swift_out=./gen \
  --grpc-swift_out=./gen \
  ../proto/session_manager.proto
```

---

Let me know if you hit any errors during the `swift build`, or want to automate this into a shell script!
```go
func root_handler(w http.ResponseWriter, r *http.Request) {
    if r.Method != "POST" {
        w.WriteHeader(http.StatusMethodNotAllowed)
        return
    }

    if r.Header.Get("Content-Type") != "application/json" {
        http.Error(w, "Unsupported Media Type", http.StatusUnsupportedMediaType)
        return
    }

    defer r.Body.Close()

    var result map[string]interface{}
    if err := json.NewDecoder(r.Body).Decode(&result); err != nil {
        http.Error(w, "Invalid JSON", http.StatusBadRequest)
        return
    }

    fmt.Printf("%v\n", result)

    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(result)
}
```

____
Tags: #programming #golang #language #go-http
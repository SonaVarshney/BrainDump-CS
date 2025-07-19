

### 🚕 Imagine you’re booking a cab (like Ola/Uber)

You start a ride. But:

* You can **cancel** the ride anytime.
* The ride will **automatically end** if the timer runs out.
* You also share some **info** (like your name, pickup point).

Now replace “ride” with a **function or task in Go**, and you get what the `context` package does.

---

## ✅ What is `context`?

It's like a **controller** you pass to a function to say:

* “Hey, stop working if time’s up”
* “Stop working if I cancel you”
* “Here’s some info you’ll need (like user ID)”

---

## 🧱 Types of context

### 1. **`context.Background()`**

Just like standing at the starting point. Base context to build on.
👉 Like: Starting the ride from scratch.

---

### 2. **`context.WithCancel()`**

Gives you a remote control — so you can **cancel** the work any time.

```go
ctx, cancel := context.WithCancel(context.Background())
cancel() // stops it manually
```

👉 Like: You press "Cancel Ride" in the app.

---

### 3. **`context.WithTimeout()`**

You give a time limit. After that, Go will **automatically stop** the work.

```go
ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
```

👉 Like: “If cab doesn’t come in 2 minutes, cancel it.”

---

### 4. **`context.WithDeadline()`**

You say **exact date & time** to stop.

```go
deadline := time.Now().Add(2 * time.Second)
ctx, cancel := context.WithDeadline(context.Background(), deadline)
```

👉 Like: “End this by exactly 5:30 PM.”

---

## 💬 What happens when time’s up or cancelled?

You can **check if the ride was cancelled or auto-ended**:

```go
select {
case <-ctx.Done():
    // Ride ended or cancelled
    fmt.Println("Stopped:", ctx.Err())
}
```

---

## 🎒 Sharing Info — `WithValue`

Let’s say you want to send your **user ID** or token along with the ride.

```go
ctx := context.WithValue(context.Background(), "userID", 42)
```

👉 Like: Adding your name or OTP to the ride request.

You can access it later inside a function:

```go
userID := ctx.Value("userID")
```

---

## 🧪 Real Example in Life:

You're doing laundry at a hostel. You start the machine.

* You can **cancel** it (if you're in a hurry).
* It can **stop automatically** after 30 minutes.
* You might attach a **note** on the machine saying "This is Sona's clothes".

That’s what context does in Go – it helps **start, cancel, time-out, and pass notes** to running tasks (functions/goroutines).

---

## 🤝 Why is it useful?

* In web servers: Stop slow requests.
* In APIs: Cancel DB query if user closes the app.
* In goroutines: Save memory by stopping tasks not needed anymore.



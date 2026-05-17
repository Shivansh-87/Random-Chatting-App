# 💬 StrangerChat

A real-time anonymous chat application that connects you with random strangers — built with **Spring Boot**, **WebSocket (STOMP)**, and **SockJS**.

---

## 🚀 Features

- 🔀 **Random Matchmaking** — instantly paired with a random stranger
- 💬 **Real-time Messaging** — powered by WebSocket + STOMP protocol
- ⌨️ **Typing Indicator** — see when the stranger is typing
- ⏭️ **Next Stranger** — skip to a new person anytime
- 🔌 **Auto Disconnect Handling** — partner is notified when you leave
- 🎨 **Dark UI** — clean, modern interface with smooth animations
- 📱 **Responsive** — works on mobile and desktop

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Java 17, Spring Boot 3.x |
| WebSocket | Spring WebSocket + STOMP |
| Frontend | HTML, CSS, JavaScript |
| UI Libraries | SockJS, Bootstrap 5 |
| Build Tool | Maven |
| Template Engine | Thymeleaf |

---

## 📁 Project Structure

```
src/
├── main/
│   ├── java/com/chat/app/
│   │   ├── config/
│   │   │   ├── WebSocketConfig.java         # STOMP broker config
│   │   │   └── WebSocketEventListener.java  # Connect/disconnect events
│   │   ├── controller/
│   │   │   └── ChatController.java          # WebSocket message handlers
│   │   ├── model/
│   │   │   └── ChatMessage.java             # Message model
│   │   ├── service/
│   │   │   └── MatchmakingService.java      # Pairing logic
│   │   └── AppApplication.java
│   └── resources/
│       ├── templates/
│       │   └── chat.html                    # Frontend UI
│       └── application.properties
```

---

## ⚙️ Getting Started

### Prerequisites

- Java 17+
- Maven 3.6+

### Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/stranger-chat.git

# 2. Navigate into the project
cd stranger-chat

# 3. Build and run
./mvnw spring-boot:run
```

### Open in Browser

```
http://localhost:8080/chat
```

> **To test:** Open two browser tabs at the same URL — they will auto-pair with each other.

---

## 🔄 How It Works

```
User A opens app → enters nickname → clicks "Start Chatting"
        ↓
Server adds User A to waiting queue
        ↓
User B opens app → clicks "Start Chatting"
        ↓
Server pairs A & B → creates a unique Room ID (UUID)
        ↓
Both users notified → private chat begins
        ↓
Either user clicks "Next" → partner notified → both find new strangers
```

---

## 📡 WebSocket Endpoints

| Endpoint | Direction | Description |
|---|---|---|
| `/app/findStranger` | Client → Server | Request matchmaking |
| `/app/sendMessage` | Client → Server | Send a chat message |
| `/app/next` | Client → Server | Find a new stranger |
| `/topic/session/{sessionId}` | Server → Client | Personal events (matched, waiting) |
| `/topic/room/{roomId}` | Server → Client | Room messages (chat, joined, left) |

---

## 🗺️ Roadmap

- [ ] Multiple chat rooms / topic-based matching
- [ ] Interest tags for smarter pairing
- [ ] Video chat via WebRTC
- [ ] User reporting / moderation
- [ ] Message persistence with database
- [ ] Docker support

---

## 🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> Built with ❤️ using Spring Boot

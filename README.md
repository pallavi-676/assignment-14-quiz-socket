# Real-Time Multiplayer Live Quiz Battle

A real-time multiplayer quiz application built using Node.js, Express.js, and Socket.io.

Players can join a quiz room using a unique PIN, answer questions in real time, compete based on both correctness and response speed, and watch the leaderboard update live after every question.

The application uses a server-driven game engine to keep the quiz synchronized for all connected players.

---

## 🎯 Assignment Overview

**Assignment:** 14 — Real-Time Multiplayer Live Quiz Battle  
**Track:** Backend & Real-Time Web  
**Difficulty:** Advanced  
**Technology:** Node.js, Express.js, Socket.io

This project demonstrates real-time communication, synchronized server-side timers, multiplayer room management, dynamic scoring, anti-cheat validation, and live leaderboard updates.

---

## ✨ Features

- Host-controlled multiplayer quiz rooms
- Unique 4-digit room PIN generation
- Players join using a room PIN
- Real-time lobby updates
- Server-driven 15-second question timer
- Synchronized question transitions
- Real-time answer submission
- Server-side answer validation
- Late-answer rejection
- Duplicate-answer prevention
- Speed-based scoring
- Live leaderboard updates
- Automatic question progression
- Final winner announcement
- Player connection and disconnection handling
- Separate Host and Player interfaces
- In-memory game state management
- Responsive and modern user interface

---

## 🎮 How the Game Works

### 1. Host Creates a Room

The host opens the application and creates a quiz room.

The server generates a unique 4-digit PIN and creates an in-memory game room.

### 2. Players Join

Players enter the room PIN and their player name.

The server validates the PIN and adds each player to the room.

The lobby is updated in real time whenever a player joins or leaves.

### 3. Host Starts the Quiz

Once the players are ready, the host starts the quiz.

The server begins the first question and starts the 15-second countdown.

### 4. Players Answer

Every player receives the same question simultaneously.

Players select an answer and submit it before the timer expires.

The server calculates the player's response time instead of trusting the client.

### 5. Timer Expires

When the 15-second timer ends, the server:

- Stops accepting answers
- Reveals the correct answer
- Calculates the final results
- Updates the leaderboard
- Broadcasts the leaderboard to all players

### 6. Next Question

The server automatically moves to the next question.

This process continues until all questions have been completed.

### 7. Quiz Ends

After the final question, the server calculates the final rankings and announces the winner.

---

## 🏆 Scoring System

The scoring system rewards both correctness and speed.

### Correct Answer

Base Score: 500 points

Speed Bonus: Up to 500 points

Maximum Score Per Question: 1000 points

The speed bonus is calculated using the remaining time when the player submits their answer.

### Incorrect Answer

Score: 0 points

### Scoring Formula

Time Remaining = Total Time Limit − Time Taken

Speed Bonus = Round((Time Remaining / Total Time Limit) × 500)

Final Score = 500 + Speed Bonus

The maximum possible score for one question is 1000 points.

---

## 🛡️ Anti-Cheat Protection

The application performs important game validation on the server.

### Server-Side Timing

The server records when every question starts.

When a player submits an answer, the server calculates the response time using the server clock.

This prevents players from modifying their client-side timer to gain an advantage.

### Late Answer Rejection

Answers submitted after the 15-second limit are rejected.

### Duplicate Answer Prevention

A player can submit only one answer for each question.

### Server-Side Correct Answer Validation

The correct answer is stored on the server and is not sent to players when the question starts.

The server validates submitted answers before awarding points.

---

## 🔌 Real-Time Socket Events

The application uses Socket.io for real-time communication.

| Event | Purpose |
|---|---|
| quiz:create | Create a new quiz room |
| quiz:created | Return the generated room PIN |
| quiz:join | Join an existing quiz room |
| lobby:update | Broadcast current players |
| quiz:start | Start the quiz |
| question:start | Send a new question and start the timer |
| answer:submit | Submit a player's answer |
| question:time_up | Notify clients when the timer expires |
| leaderboard:update | Broadcast updated rankings |
| quiz:ended | Announce the final results |

---

## 🏗️ Project Structure

assignment-14-quiz-socket/

├── public/

│   ├── index.html

│   ├── host.html

│   ├── host.js

│   ├── player.html

│   ├── player.js

│   └── styles.css

├── data/

│   └── questions.json

├── docs/

│   ├── quiz.png

│   ├── quiz2.png

│   ├── quiz3.png

│   ├── quiz4.png

│   └── quiz5.png

├── sockets/

│   ├── gameEngine.js

│   └── lobbyHandler.js

├── server.js

├── package.json

├── package-lock.json

└── .gitignore

---

## ⚙️ Tech Stack

### Backend

- Node.js
- Express.js
- Socket.io
- CORS

### Frontend

- HTML5
- CSS3
- JavaScript
- Socket.io Client

### Data Storage

The application uses an in-memory game state engine.

Quiz questions are stored in a JSON file.

No external database is required.

---

## 🚀 Getting Started

### Prerequisites

Make sure Node.js and npm are installed on your system.

### Installation

Open the assignment folder in your terminal.

Install the required dependencies using npm install.

### Environment Configuration

Create a .env file based on the provided environment configuration.

The application uses port 5000 by default.

### Start the Server

Run npm start.

For development, run npm run dev.

The application will be available at:

http://localhost:5000

---

## 🧪 Testing the Multiplayer Quiz

To test the application locally:

### Host

1. Open the application.
2. Enter the host details.
3. Create a quiz room.
4. Copy the generated room PIN.
5. Start the quiz after players have joined.

### Players

1. Open another browser tab or window.
2. Join using the room PIN.
3. Enter a player name.
4. Wait for the host to start the quiz.
5. Submit answers during each question.

### Scoring Test

To verify speed-based scoring:

- Player 1 answers immediately.
- Player 2 waits several seconds before answering.
- Both players answer correctly.

Player 1 should receive a higher score because of the speed bonus.

### Anti-Cheat Test

Attempt to submit an answer after the 15-second timer expires.

The server should reject the late submission.

---

## 📸 Project Screenshots

The docs folder contains screenshots demonstrating the application interface and real-time quiz flow.

---

## 📌 Learning Outcomes

This project demonstrates practical implementation of:

- WebSocket-based real-time communication
- Socket.io event-driven architecture
- Multiplayer room management
- Server-side state management
- Synchronized countdown timers
- Real-time event broadcasting
- Server-side validation
- Anti-cheat mechanisms
- Dynamic scoring systems
- Live leaderboard management
- Client-server communication
- Connection and disconnection handling

---

## 👩‍💻 Student Information

**Name:** Pallavi Sarovar  
**Roll No.:** [Add Roll Number]  
**Cohort:** [Add Cohort]

---

## 📄 Assignment

**Assignment 14 — Real-Time Multiplayer Live Quiz Battle**

Built as part of the Backend & Real-Time Web track.

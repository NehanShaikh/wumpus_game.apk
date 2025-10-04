**See Releases to download the game apk**
# wumpus_game.apk

A multiplayer (or single-player) strategy game built with **Node.js**, **PostgreSQL**, and **Flutter**. This project features a backend API for user management and saved game state, and a Flutter frontend for gameplay.

Table of Contents

* [Features](#features)
* [Tech Stack](#tech-stack)
* [Project Structure](#project-structure)
* [Setup & Installation](#setup--installation)
* [Environment Variables](#environment-variables)
* [Database Setup](#database-setup)
* [Running the Project](#running-the-project)
* [API Endpoints](#api-endpoints)
* [Flutter Frontend](#flutter-frontend)
* [Deployment](#deployment)
* [Contributing](#contributing)
* [License](#license)

Features

* User authentication (signup/login)
* Save and load game states
* Track wins, losses, and matches
* JSON-based game board storage
* Multiple difficulty levels

Tech Stack

* **Backend:** Node.js, Express.js, Sequelize ORM
* **Database:** PostgreSQL (hosted on Render)
* **Frontend:** Flutter with secure storage
* **Deployment:** Render for backend, Flutter Web/Mobile for frontend

Project Structure

```
wumpus-backend/
├─ models/
│  ├─ user.js
│  └─ savedGame.js
├─ routes/
│  ├─ auth.js
│  └─ games.js
├─ config/
│  └─ db.js
├─ server.js
└─ .env
```

* `models/` – Sequelize models for Users and SavedGames
* `routes/` – API routes for authentication and game logic
* `server.js` – Express server configuration and database sync
* `config/db.js` – Database connection configuration

Setup & Installation

Prerequisites

* Node.js >= 16.x
* PostgreSQL database (hosted locally or Render)
* Flutter SDK (for frontend)

Backend Setup

1. Clone the repository:

```bash
git clone https://github.com/NehanShaikh/wumpus_game.git
cd wumpus-backend
```

2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the backend root:

```env
DB_USER=wumpus_db_user
DB_PASS=your_db_password
DB_NAME=wumpus_db
DB_HOST=dpg-d3ghi7h5pdvs73eh2cg0-a.singapore-postgres.render.com
PORT=5000
```

4. Start the backend server:

```bash
npm run dev
```

---

Database Setup

1. Ensure PostgreSQL is running (or use Render-hosted Postgres).
2. The tables are auto-created by Sequelize when the server starts:

   * `users`
   * `saved_games`

**Optional:** You can manually create tables in PostgreSQL using Sequelize models or SQL commands.

API Endpoints

| Endpoint           | Method | Description               |
| ------------------ | ------ | ------------------------- |
| `/api/health`      | GET    | Check server status       |
| `/api/auth/signup` | POST   | User registration         |
| `/api/auth/login`  | POST   | User login                |
| `/api/games`       | GET    | List saved games for user |
| `/api/games`       | POST   | Save new game             |
| `/api/games/:id`   | PUT    | Update existing game      |
| `/api/games/:id`   | DELETE | Delete saved game         |

Flutter Frontend

1. Set the backend URL in `ApiService`:

```dart
static const String baseUrl = "https://wumpus-game.onrender.com/api";
```

2. Use Flutter Secure Storage for storing authentication tokens.
3. Make HTTP requests to your Render backend.

Deployment

Backend

* Deployed on [Render](https://render.com)
* Use the Render service URL for the Flutter frontend.

Frontend

* Can run as a Flutter mobile app or Flutter Web app.
* Ensure the device has internet access to reach Render-hosted backend.

Contributing

1. Fork the repository
2. Create a new branch (`git checkout -b feature-name`)
3. Make your changes
4. Commit and push (`git commit -am 'Add new feature'`)
5. Open a pull request

License

MIT License © 2025 Nehan Shaikh

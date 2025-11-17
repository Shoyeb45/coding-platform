# Coding Platform

![Next.js](https://img.shields.io/badge/Next.js-15+-000000?style=for-the-badge&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-404D59?style=for-the-badge&logo=express&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-3982CE?style=for-the-badge&logo=Prisma&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)

> A comprehensive competitive programming platform enabling students to solve coding challenges, participate in contests, and teachers to create problems and manage competitions.

## Live Demo

**[Visit Coding Platform →](https://lab.pwioi.club/)**

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [System Architecture](#-system-architecture)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Contributing](#-contributing)

---

## Overview

A full-featured online coding platform designed for educational institutions and competitive programming enthusiasts. Built with scalability and performance in mind, it provides a LeetCode-like experience with contest management capabilities.

### Why This Platform?

- **Contest Ready**: Organize and participate in timed coding competitions
- **Teacher Friendly**: Intuitive interface for creating questions and test cases
- **Real-time Execution**: Powered by Judge0 for secure code execution
- **Performance Tracking**: Leaderboards and submission history
- **Scalable Architecture**: Distributed task processing with Bull MQ

---

## Key Features

### For Students

#### Problem Solving
- Browse through curated coding problems
- LeetCode-style problem statements with examples
- Support for multiple programming languages
- Real-time code execution with Monaco IDE
- Instant feedback on test cases

<p>
    <img src="./public/questions.png">
</p>

#### Contest Participation
- Join scheduled coding contests
- Live leaderboard updates
- Time-bound problem solving
- Performance analytics and rankings

<p>
    <img src="./public/code-1.png">
</p>

#### Submission Management
- Track all submissions with detailed status
- View execution time and memory usage
- Access submission history
- Compare solutions

<p>
    <img src="./public/code-2.png">
</p>

### For Teachers

#### Question Management
- Create problems with custom test cases
- Define driver code similar to LeetCode
- Support for hidden and public test cases
- Rich text editor for problem descriptions
- Difficulty level classification


#### Contest Creation
- Schedule contests with start/end times
- Select problems for contests
- Configure scoring rules
- Monitor contest progress in real-time

### 🏅 Leaderboard System
- Global rankings based on solved problems
- Contest-specific leaderboards
- Real-time score updates
- Performance metrics and statistics

---

## 🛠️ Tech Stack

### Frontend

| Technology | Version | Purpose |
|------------|---------|---------|
| **Next.js** | 15+ | React framework with SSR/SSG |
| **TypeScript** | Latest | Type-safe development |
| **TailwindCSS** | Latest | Utility-first CSS framework |
| **Monaco Editor** | Latest | VS Code-powered code editor |

### Backend

| Technology | Purpose |
|------------|---------|
| **Express.js** | RESTful API server |
| **PostgreSQL** | Relational database for data persistence |
| **Prisma** | Type-safe ORM for database operations |
| **Redis** | Caching and session management |
| **Bull MQ** | Distributed job queue for code execution |
| **Judge0** | Secure code compilation and execution engine |

### DevOps & Infrastructure

| Technology | Purpose |
|------------|---------|
| **Docker** | Application containerization |
| **AWS EC2** | Hosting workers and Judge0 instances |
| **AWS Elastic Beanstalk** | Auto-scaling and load balancing |
| **GitHub Actions** | CI/CD pipeline |

---

## System Architecture

<p>
    <img src="./public/project-arch.png">
</p>

### Architecture Highlights

- **Asynchronous Processing**: Code submissions are queued using Bull MQ for non-blocking execution
- **Horizontal Scaling**: Multiple workers process submissions in parallel
- **Caching Layer**: Redis stores frequently accessed data for faster response times
- **Isolated Execution**: Judge0 runs in isolated containers for security
- **Load Balancing**: Elastic Beanstalk automatically scales based on traffic

---

## 📁 Project Structure

```
coding-platform/
├── backend/                     # Express.js API
│   ├── prisma/
│   │   └── migrations/
│   │       └── 20250820135015_init/
│   └── src/
│       ├── config/              # Configuration files
│       ├── middlewares/         # Express middlewares
│       ├── queues/              # Bull MQ queue definitions
│       ├── services/            # Business logic services
│       ├── types/               # TypeScript type definitions
│       ├── utils/               # Helper functions
│       ├── v1/                  # API version 1
│       │   ├── controllers/     # Route controllers
│       │   ├── repositories/    # Data access layer
│       │   ├── routes/          # API routes
│       │   ├── services/        # Business services
│       │   └── types/           # API types
│       └── workers/             # Background job processors
│
├── docker-compose.yml           # Docker services configuration
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ and npm
- **PostgreSQL** 14+
- **Redis** 6+
- **Docker** & Docker Compose
- **Judge0** instance (or Docker setup)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Shoyeb45/coding-platform-backend.git
   cd coding-platform
   ```

2. **Setup Environment Variables**
   
   Create `.env` files in both frontend and backend directories:
   
   **Backend `.env`**
   ```env
   # Database
   DATABASE_URL="postgresql://user:password@localhost:5432/codingplatform"
   
   # Redis
   REDIS_URL="redis://localhost:6379"
   
   # Judge0
   JUDGE0_URL="http://localhost:2358"
   JUDGE0_API_KEY="your_judge0_api_key"
   
   # JWT
   JWT_SECRET="your_jwt_secret"
  
   # Server
   PORT=8000
   NODE_ENV=development
   ```
   
   **Frontend `.env.local`**
   ```env
   NEXT_PUBLIC_API_URL=http://localhost:8000/api/v1
   ```

3. **Setup Backend**
   ```bash
   cd backend
   npm install
   
   # Run Prisma migrations
   npx prisma migrate dev
   
   # Generate Prisma client
   npx prisma generate
   
   # Start development server
   npm run dev
   ```

4. **Setup Frontend**
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

5. **Setup Judge0 (using Docker)**
   ```bash
   # Pull Judge0 Docker image
   docker pull judge0/judge0:latest
   
   # Run Judge0 container
   docker-compose up -d judge0
   ```

6. **Start Workers**
   ```bash
   cd backend
   npm run dev:workers
   ```

### Docker Setup (Recommended)

```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop all services
docker-compose down
```

---


## 🔧 Configuration

### Supported Programming Languages

- C++ (GCC 11.2.0)
- Java (OpenJDK 17.0.1)
- Python (3.10.0)
- JavaScript (Node.js 16.14.0)

### Execution Limits

- **Time Limit**: 2 seconds (configurable per problem)
- **Memory Limit**: 256 MB (configurable per problem)
- **Source Code Limit**: 50 KB

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow the existing code style
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed

---

## 🙏 Acknowledgments

- **Judge0** for the code execution engine
- **Monaco Editor** for the code editor component
- **Bull MQ** for reliable job queue processing

---

<div align="center">

**[⬆ Back to Top](#-coding-platform)**

Made with ❤️ for educators and coding enthusiasts

</div>
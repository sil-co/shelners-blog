# Shelner's Blog

Shelner's Blog is a simple blog website built with modern web technologies. 
It allows read, update, and delete blog posts(only owner...). 
The project is powered by React (with React Router v7 and TailwindCSS) on the frontend, and Spring Boot with MySQL (running on Docker) on the backend.

## 🚀 Technologies Used

### Frontend:
- **React** ([React Router v7](https://reactrouter.com/start/framework/installation))
- **Tailwind CSS** (for styling)

### Backend:
- **Spring Boot** (REST API development)
- **Spring Data JPA** (for database access)
- **Spring Security** (if authentication is implemented)

### Database:
- **MySQL** (running inside Docker)

## 🏗️ Setup Instructions

### Prerequisites
Make sure you have the following installed on your machine:
- **Node.js** (for running the frontend)
- **Java 17+** (for running Spring Boot backend. This project is using 21)
- **Docker & Docker Compose** (for MySQL database)
- **Maven** (for building the backend)

### Database Setup (MySQL)
1. Clone the repository:
   ```sh
   git clone https://github.com/sil-co/shelners-blog-db.git
   ```
2. Start MySQL with Docker:
   cd shelners-blog/database
   touch docker-env/docker.env
   Add following code in docker.env 
   ```docker.env
    # docker.env
    MYSQL_USER=your-mysql-user
    MYSQL_PASSWORD=your-mysql-user-pass MYSQL_DATABASE=your-mysql-db-name
    MYSQL_ROOT_PASSWORD=your-mysql-root-pass
    TZ=Asia/Tokyo
   ```
   ```sh
   docker-compose up -d
   ```

### Backend Setup (Spring Boot)
1. Clone the repository:
   ```sh
   git clone https://github.com/sil-co/shelners-blog-back.git
   ```
2. Configure `application.properties`:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/blog-spring-db?useSSL=false&serverTimezone=UTC
   spring.datasource.username=root
   spring.datasource.password=your-mysql-root-pass
   ```
3. Build and run the Spring Boot backend:
   ```sh
   mvn clean install
   mvn spring-boot:run
   ```

### Frontend Setup (React)
1. Navigate to the frontend directory:
   ```sh
   cd ../frontend
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm run dev
   ```

## 🌍 API Endpoints
The backend provides a REST API to manage blog posts. Below are some key endpoints:

| Method | Endpoint           | Description               |
|--------|-------------------|---------------------------|
| GET    | `/api/posts`      | Get all blog posts        |
| GET    | `/api/posts/{id}` | Get a single post by ID   |
| POST   | `/api/posts`      | Create a new blog post    |
| PUT    | `/api/posts/{id}` | Update an existing post   |
| DELETE | `/api/posts/{id}` | Delete a blog post        |

## 📜 Folder Structure
```
/shelners-blog
│── /backend          # Spring Boot backend
│   ├── /src          # Java source code
│   ├── pom.xml       # Maven dependencies
│── /frontend         # React frontend
│   ├── /app          # React components
│   ├── package.json  # Node dependencies
│── /database         # MySQL database
│   ├── /docker-env   # Docker environment
│   ├── docker-compose.yml # MySQL setup
```

## 📜 License
This project is licensed under the MIT License.

---
Feel free to contribute to this project by submitting issues and pull requests!


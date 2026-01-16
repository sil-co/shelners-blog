The English version is the bottom.

# Shelner's Blog

## プレビュー
![プレビュー動画](assets/blog-tuto-times-3-4.gif)

## 概要
Shelner's Blog は、Web テクノロジーを用いて構築されたシンプルなブログサイトです。
ブログ投稿の閲覧と更新（投稿者のみ）が可能です。
このプロジェクトは、フロントエンドに React（React Router v7 と TailwindCSS を使用）、バックエンドに Spring Boot または ASP.NET Core Web API、そして MySQL（Docker 上で動作）を採用しています。

**バックエンドにはSpring-BootまたはASP.NETを使用してください。**

## 使用テクノロジー

### フロントエンド:
- **React** ([React Router v7](https://reactrouter.com/start/framework/installation))
- **Tailwind CSS** (スタイル設定用)

### バックエンド(Spring Boot):
- **Spring Boot** (REST API開発用)
- **Spring Data JPA** (データベースアクセス用)
- **Spring Security** (認証が実装されている場合)

### バックエンド(ASP.NET)
- **ASP.NET Core Web API**

### データベース:
- **MySQL** (Docker内で実行)

## セットアップ手順

### 前提条件
お使いのマシンに以下のものがインストールされていることを確認してください。
- **Node.js** (フロントエンド実行用)
- **Java 21** (Spring Boot実行用)バックエンド。)
- **Maven** (バックエンドの構築用)
- **Docker** (MySQL データベースコンテナ用)
- **dotnet** (ASP.NET バックエンドの実行用)

## データベースのセットアップ (MySQL)
1. リポジトリをクローンします。
```sh
git clone https://github.com/sil-co/shelners-blog-db.git
```
2. Docker で MySQL を起動します。
cd shelners-blog/database
touch docker-env/docker.env
docker.env に以下のコードを追加します。
```docker.env
# docker.env
MYSQL_USER=mysql ユーザー名
MYSQL_PASSWORD=mysql ユーザー名のパス MYSQL_DATABASE=mysql データベース名
MYSQL_ROOT_PASSWORD=mysql ルートパスワード
TZ=Asia/Tokyo
```
```sh
docker-compose up -d
```

## バックエンドのセットアップ (Spring Boot)
1. リポジトリをクローンします。
```sh
git clone https://github.com/sil-co/shelners-blog-back.git
```

2. `application.properties` を設定します。
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/blog-spring-db?useSSL=false&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=your-mysql-root-pass
```
3. Spring Boot バックエンドをビルドして実行します。
```sh
mvn clean install
mvn spring-boot:run
```

## バックエンドのセットアップ (ASP.NET)
1. リポジトリをクローンします。
``sh
git clone https://github.com/sil-co/backend-dotnet.git
```
2. 依存関係をインストール
`dotnet restore`
3. API を起動
`dotnet run`

## フロントエンドのセットアップ (React)
1. リポジトリのクローンを作成
```sh
git clone https://github.com/sil-co/shelners-blog-front.git
# Spring Boot を使用している場合は、以下のコマンドでブランチを切り替えます
git checkout for-spring-boot
```
2. 依存関係をインストール:
```sh
npm install
```
3. 開発サーバーを起動:
```sh
npm run dev
```

## API エンドポイント
バックエンドは、ブログ投稿を管理するための REST API を提供します。主なエンドポイントを以下に示します。

| メソッド | エンドポイント | 説明 |
|--------|-------------------|---------------------------|
| GET | `/api/posts` | すべてのブログ投稿を取得 |
| GET | `/api/posts/{id}` | ID で単一の投稿を取得 |
| POST | `/api/posts` | 新しいブログ投稿を作成 |
| PUT | `/api/posts/{id}` | 既存の投稿を更新 |
| DELETE | `/api/posts/{id}` | ブログ投稿を削除 |
| POST | `/api/users/login` | ユーザーログイン |
| GET | ` `/api/posts/verify-owner/{id} | ユーザーが編集可能かどうかを確認 |

## フォルダ構造
```
/shelners-blog
│── /backend-spring-boot # Spring Boot バックエンド
│ ├── /src # Java ソースコード
│ ├── pom.xml # Maven 依存関係
│── /backend-dotnet # ASP.NET バックエンド
│── /frontend # React フロントエンド
│ ├── /app # React コンポーネント
│ ├── package.json # Node 依存関係
│── /database # MySQL データベース
│ ├── /docker-env # Docker 環境
│ ├── docker-compose.yml # MySQL セットアップ
```

## ライセンス
このプロジェクトは MIT ライセンスに基づきます。

---


# Shelner's Blog

## Preview
![Preview video](assets/blog-tuto-times-3-4.gif)

## About
Shelner's Blog is a simple blog website built with web technologies. 
It allows read, update blog posts(only owner...). 
The project is powered by React (with React Router v7 and TailwindCSS) on the frontend, Spring Boot or ASP.NET Core Web API and MySQL (running on Docker) on the backend.

**Use either Spring-Boot or ASP.NET as backend.**

## Technologies Used

### Frontend:
- **React** ([React Router v7](https://reactrouter.com/start/framework/installation))
- **Tailwind CSS** (for styling)

### Backend(Spring Boot):
- **Spring Boot** (REST API development)
- **Spring Data JPA** (for database access)
- **Spring Security** (if authentication is implemented)

### Backend(ASP.NET)
- **ASP.NET Core Web API**

### Database:
- **MySQL** (running inside Docker)

## Setup Instructions

### Prerequisites
Make sure you have the following installed on your machine:
- **Node.js** (for running the frontend)
- **Java 21** (for running Spring Boot backend.)
- **Maven** (for building the backend)
- **Docker** (for MySQL database Container)
- **dotnet** (for running ASP.NET backend)

## Database Setup (MySQL)
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

## Backend Setup (Spring Boot)
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

## Backend Setup (ASP.NET)
1. Clone the Repository
```sh
git clone https://github.com/sil-co/backend-dotnet.git
```
2.  Install Dependencies
`dotnet restore`
3. Start the API
`dotnet run`

## Frontend Setup (React)
1. Clone the Repository
   ```sh
   git clone https://github.com/sil-co/shelners-blog-front.git
   # If you use Spring Boot, do the following to switch branches
   git checkout for-spring-boot
   ```
2. Install dependencies:
   ```sh
   npm install
   ```
3. Start the development server:
   ```sh
   npm run dev
   ```

## API Endpoints
The backend provides a REST API to manage blog posts. Below are some key endpoints:

| Method | Endpoint           | Description               |
|--------|-------------------|---------------------------|
| GET    | `/api/posts`      | Get all blog posts        |
| GET    | `/api/posts/{id}` | Get a single post by ID   |
| POST   | `/api/posts`      | Create a new blog post    |
| PUT    | `/api/posts/{id}` | Update an existing post   |
| DELETE | `/api/posts/{id}` | Delete a blog post        |
| POST | `/api/users/login` | User Login |
| GET | ` `/api/posts/verify-owner/{id} | Check if the user can edit |

## Folder Structure
```
/shelners-blog
│── /backend-spring-boot # Spring Boot backend
│   ├── /src          # Java source code
│   ├── pom.xml       # Maven dependencies
│── /backend-dotnet   # ASP.NET backend
│── /frontend         # React frontend
│   ├── /app          # React components
│   ├── package.json  # Node dependencies
│── /database         # MySQL database
│   ├── /docker-env   # Docker environment
│   ├── docker-compose.yml # MySQL setup
```

## License
This project is licensed under the MIT License.

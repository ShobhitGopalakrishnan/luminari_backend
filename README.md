# Luminari Backend

A Node.js/Express backend API for document management with authentication.

## Features

- 🔐 JWT Authentication
- 📄 Document Management (CRUD operations)
- 🗄️ PostgreSQL Database with Prisma ORM
- 🔒 Secure password hashing with bcrypt
- 🌐 CORS enabled for frontend integration

## Prerequisites

- Node.js (v14 or higher)
- PostgreSQL database
- npm or yarn

## Local Development Setup

### 1. Clone the repository
```bash
git clone https://github.com/ShobhitGopalakrishnan/luminari_backend.git
cd luminari_backend
```

### 2. Install dependencies
```bash
npm install
```

### 3. Set up environment variables
Create a `.env` file in the root directory:
```env
DATABASE_URL="postgresql://username:password@localhost:5432/database_name"
JWT_SECRET="your-super-secret-jwt-key-change-this-in-production"
PORT=4000
NODE_ENV=development
```

### 4. Set up the database
```bash
# Create database (if using local PostgreSQL)
createdb your_database_name

# Run migrations
npm run build
```

### 5. Start the server
```bash
npm start
```

The server will run on `http://localhost:4000`

## API Endpoints

### Authentication
- `POST /auth/register` - Register a new user
- `POST /auth/login` - Login user
- `GET /auth/verify` - Verify JWT token

### Documents
- `GET /documents` - Get all documents
- `POST /documents` - Create a new document
- `GET /documents/:id` - Get document by ID
- `PUT /documents/:id` - Update document
- `DELETE /documents/:id` - Delete document

## Deployment

### Environment Variables Required
Make sure to set these environment variables in your deployment platform:

- `DATABASE_URL` - PostgreSQL connection string
- `JWT_SECRET` - Secret key for JWT tokens
- `PORT` - Server port (optional, defaults to 4000)
- `NODE_ENV` - Environment (production/development)

### Build Process
The build process includes:
1. Prisma client generation
2. Database migrations

```bash
npm run build
```

## Database Schema

### User Model
- `id` - UUID primary key
- `username` - Unique username
- `password` - Hashed password
- `createdAt` - Timestamp
- `updatedAt` - Timestamp

### Document Model
- `id` - UUID primary key
- `type` - Document type (PROTOCOL, STUDY_DESIGN, REGULATORY, OTHER)
- `title` - Document title
- `disease` - Associated disease (optional)
- `country` - Country (optional)
- `region` - Region (optional)
- `protocolId` - Protocol ID (optional)
- `documentType` - Document type string (optional)
- `content` - Document content
- `cmcSection` - CMC section (optional)
- `clinicalSection` - Clinical section (optional)
- `sections` - JSON sections (optional)
- `userId` - Associated user ID (optional)
- `tags` - Array of tags
- `createdAt` - Timestamp
- `updatedAt` - Timestamp

## Troubleshooting

### DATABASE_URL not found error
This error occurs when the environment variables are not properly loaded. Make sure:
1. The `.env` file exists in the root directory
2. The `DATABASE_URL` is correctly formatted
3. For deployment, set the environment variables in your platform's settings

### Database connection issues
- Verify PostgreSQL is running
- Check the connection string format
- Ensure the database exists
- Verify user permissions

## License

ISC

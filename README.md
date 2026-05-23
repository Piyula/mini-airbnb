# 🏠 Mini Airbnb - Property Rental Platform

A full-stack property rental platform inspired by Airbnb, built with the MERN stack (MongoDB, Express.js, React, Node.js) and designed for fast local development and containerized deployment.

![Project Banner](https://via.placeholder.com/1200x400?text=Mini+Airbnb+Platform)

## ✨ Features

### Core Features
- 🔐 **User Authentication** - Register/Login with JWT-based auth
- 🏘️ **Property Management** - Create, read, update, and delete property listings
- 📸 **Image Upload** - Upload property images with Cloudinary integration
- 🔍 **Search & Filter** - Find listings by location, price, and guest capacity
- 📅 **Booking System** - Request and manage bookings for stays
- 👤 **User Dashboard** - Manage bookings and owned listings
- 🛡️ **Role-Based Access** - Separate user, host, and admin permissions
- 📱 **Responsive Design** - Mobile-first UI for great cross-device usability

### Technical Features
- 🐳 **Docker Friendly** - Project is prepared for container-based deployment
- 🔄 **CI/CD Ready** - Supports automation with GitHub Actions or similar pipelines
- ☁️ **Cloud-Ready Architecture** - AWS and Cloudinary integration patterns
- 📊 **RESTful API** - Cleanly structured backend routes and controllers
- 🎨 **Modern UI** - React with utility-first styling for rapid interface development

## 🛠️ Tech Stack

### Frontend
- **React** - UI library
- **React Router** - Client-side routing
- **Axios** - API requests
- **React Hook Form** - Form handling
- **Tailwind CSS** - Styling and layout
- **React Hot Toast** - Notifications

### Backend
- **Node.js** - Server runtime
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Token authentication
- **bcryptjs** - Password hashing
- **Multer** - File uploads
- **Cloudinary** - Image storage and optimization
- **AWS SDK** - Optional AWS support for S3 and EC2

### DevOps & Cloud
- **Docker** - Containerization support
- **GitHub Actions** - CI/CD automation
- **AWS EC2** - Hosting option
- **AWS S3** - Optional image storage
- **Nginx** - Reverse proxy and static file serving

## 📋 Prerequisites

Before you begin, make sure you have the following installed:

- [Node.js](https://nodejs.org/) (v18+ recommended)
- [MongoDB](https://www.mongodb.com/) (local or Atlas)
- [Docker](https://www.docker.com/) (optional)
- [Git](https://git-scm.com/)
- npm or yarn package manager

## 🚀 Quick Start (Local Development)

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/mini-airbnb.git
cd mini-airbnb
```

### 2. Backend setup

```bash
cd backend
npm install
```

Create a `.env` file in `backend/` with the values below.

```env
PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb://localhost:27017/airbnb
JWT_SECRET=your_super_secret_key_here
JWT_EXPIRE=7d
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
AWS_REGION=us-east-1
S3_BUCKET_NAME=your_bucket_name
```

Start the backend server:

```bash
npm run dev
```

### 3. Frontend setup

```bash
cd ../frontend
npm install
```

Create a `.env` file in `frontend/` with the API URL.

```env
REACT_APP_API_URL=http://localhost:5000
REACT_APP_CLOUDINARY_CLOUD_NAME=your_cloud_name
```

Start the frontend development server:

```bash
npm start
```

### 4. Access the application

- Frontend: `http://localhost:3000`
- Backend API: `http://localhost:5000`

## 🐳 Docker Setup (Optional)

Build and run using Docker Compose:

```bash
docker-compose up --build
```

Run in detached mode:

```bash
docker-compose up -d
```

Stop services:

```bash
docker-compose down
```

View logs:

```bash
docker-compose logs -f
```

## 📁 Project Structure

```text
mini-airbnb/
├── backend/
│   ├── src/
│   │   ├── config/             # Configuration files
│   │   ├── controllers/        # Route controllers
│   │   ├── middleware/         # Custom middleware
│   │   ├── models/             # Mongoose models
│   │   ├── routes/             # API routes
│   │   ├── utils/              # Utility helpers
│   │   └── server.js           # Backend entry point
│   ├── uploads/                # Temporary uploads
│   ├── .env                    # Environment variables
│   ├── package.json
│   └── package-lock.json
├── frontend/
│   ├── public/                 # Static assets
│   ├── src/
│   │   ├── components/         # Reusable UI components
│   │   ├── context/            # React context providers
│   │   ├── hooks/              # Custom hooks
│   │   ├── pages/              # Route pages
│   │   ├── services/           # API services
│   │   ├── utils/              # Helper functions
│   │   ├── App.js              # Main app component
│   │   └── index.js            # Frontend entry point
│   ├── package.json
│   ├── Dockerfile              # Frontend Docker config
│   └── tailwind.config.js      # Tailwind CSS config
├── docker-compose.yml          # Docker Compose config
├── README.md
└── .gitignore
```

## 🔧 Configuration

### Backend environment variables

Use the sample values above to populate `backend/.env`.

### Frontend environment variables

Use the sample values above to populate `frontend/.env`.

## 📡 API Documentation

### Authentication

| Method | Endpoint               | Description          | Auth Required |
|--------|------------------------|----------------------|---------------|
| POST   | `/api/auth/register`   | Register new user    | No            |
| POST   | `/api/auth/login`      | Login user           | No            |
| GET    | `/api/auth/me`         | Get current user     | Yes           |

### Properties

| Method | Endpoint                          | Description                   | Auth Required |
|--------|-----------------------------------|-------------------------------|---------------|
| GET    | `/api/properties`                 | List all properties           | No            |
| GET    | `/api/properties/:id`             | Get property details          | No            |
| POST   | `/api/properties`                 | Create property listing       | Yes (Host)    |
| PUT    | `/api/properties/:id`             | Update property listing       | Yes (Owner)   |
| DELETE | `/api/properties/:id`             | Delete property listing       | Yes (Owner)   |
| POST   | `/api/properties/:id/images`      | Upload property images        | Yes (Owner)   |

### Bookings

| Method | Endpoint                                  | Description                     | Auth Required |
|--------|-------------------------------------------|---------------------------------|---------------|
| POST   | `/api/bookings`                           | Create a booking                | Yes           |
| GET    | `/api/bookings/my-bookings`               | Get user bookings               | Yes           |
| GET    | `/api/bookings/property/:propertyId`      | Get bookings for a property     | Yes (Host)    |
| PUT    | `/api/bookings/:id/status`                | Update booking status           | Yes (Host)    |
| PUT    | `/api/bookings/:id/cancel`                | Cancel a booking                | Yes           |

## 🧪 Testing

### Backend tests

```bash
cd backend
npm test
```

### Frontend tests

```bash
cd frontend
npm test
```

### End-to-end testing

```bash
npm install -g cypress
cypress run
```

## 🚢 Deployment Guide

### AWS deployment prerequisites

- AWS account
- EC2 instance with Docker installed
- IAM user with EC2/S3 permissions
- SSH key pair

### Recommended GitHub Secrets

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `EC2_HOST`
- `EC2_USERNAME`
- `SSH_PRIVATE_KEY`
- `MONGODB_URI`
- `JWT_SECRET`

### Deploy via GitHub Actions

Push changes to the `main` branch and let the workflow build and deploy the application.

## 🧭 Troubleshooting

### MongoDB connection error

```bash
# Check MongoDB status
sudo systemctl status mongodb
sudo systemctl start mongodb
```

### Docker port conflict

```bash
sudo lsof -i :5000
sudo kill -9 <PID>
```

### Image upload fails

- Verify Cloudinary credentials
- Confirm file size/type support
- Check upload route permissions

### CORS errors

- Ensure backend CORS settings allow your frontend origin
- Confirm `REACT_APP_API_URL` is correct

## 🤝 Contributing

- Fork the repository
- Create a feature branch: `git checkout -b feature/YourFeature`
- Commit your changes: `git commit -m "Add feature"
- Push to your branch: `git push origin feature/YourFeature`
- Open a pull request

Please follow the existing project conventions, add tests for new features, and keep documentation up to date.

## 📄 License

This project is licensed under the MIT License.

## 🙏 Acknowledgments

- Airbnb for product inspiration
- MongoDB University for database learning
- Tailwind CSS for styling utilities
- Open-source contributors and libraries

## 🗺️ Roadmap

### Phase 1 (Current)
- ✅ Basic user authentication
- ✅ Property CRUD operations
- ✅ Booking system
- ✅ Image upload

### Phase 2 (Planned)
- ⬜ Payment integration (Stripe)
- ⬜ Real-time messaging
- ⬜ User reviews & ratings
- ⬜ Wishlist functionality

### Phase 3 (Future)
- ⬜ Mobile app (React Native)
- ⬜ Advanced search filters
- ⬜ Map integration
- ⬜ Analytics dashboard
- ⬜ AI-powered recommendations

## ⭐ Show Your Support
If you find this project useful, give it a ⭐ on GitHub!

_Last Updated: May 2026_
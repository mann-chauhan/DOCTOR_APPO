# Doctor Appointment System - Setup Instructions

## Prerequisites
- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas account)
- npm or yarn package manager

## Installation Steps

### 1. Install Dependencies

From the root directory, run:
```bash
npm run install-all
```

This will install dependencies for both server and client.

### 2. Environment Setup

Create a `.env` file in the root directory with the following content:

```
MONGODB_URI=mongodb://localhost:27017/doctor-appointment
JWT_SECRET=your-secret-key-change-this-in-production
PORT=5000
```

**For MongoDB Atlas:**
Replace `MONGODB_URI` with your Atlas connection string:
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/doctor-appointment
```

### 3. Start MongoDB

**Local MongoDB:**
- Windows: Open MongoDB service or run `mongod`
- Mac/Linux: Run `mongod` or `brew services start mongodb-community` (if installed via Homebrew)

**MongoDB Atlas:**
- No local setup needed, just use your connection string

### 4. Run the Application

**Option 1: Run both servers together (Recommended)**
```bash
npm run dev
```

**Option 2: Run separately**

Terminal 1 (Backend):
```bash
npm run server
```

Terminal 2 (Frontend):
```bash
npm run client
```

### 5. Access the Application

- Frontend: http://localhost:3000
- Backend API: http://localhost:5000

## Creating an Admin User

To create an admin user, you can either:

**Option 1: Using MongoDB Shell**
```javascript
use doctor-appointment
db.users.updateOne(
  { email: "your-email@example.com" },
  { $set: { role: "admin" } }
)
```

**Option 2: Using MongoDB Compass**
1. Connect to your database
2. Navigate to `users` collection
3. Find your user document
4. Update the `role` field to `"admin"`

## Default Features

### User Features
- Register/Login
- Browse doctors by specialization
- Search doctors
- View hospitals
- Book appointments
- View medical history
- Update profile

### Admin Features
- Dashboard with statistics
- Manage doctors
- Manage appointments
- Manage hospitals
- Manage users

## Troubleshooting

### MongoDB Connection Issues
- Ensure MongoDB is running
- Check your connection string in `.env`
- Verify network access if using Atlas

### Port Already in Use
- Change `PORT` in `.env` for backend
- React app will prompt to use different port if 3000 is occupied

### CORS Issues
- Ensure backend is running on port 5000
- Check `proxy` setting in `client/package.json`

### Module Not Found Errors
- Run `npm install` in both root and client directories
- Delete `node_modules` and reinstall if issues persist

## Project Structure

```
doctor-appointment-system/
├── server/              # Backend (Express + MongoDB)
│   ├── models/         # Database models
│   ├── routes/         # API routes
│   ├── middleware/     # Auth middleware
│   └── server.js       # Entry point
├── client/             # Frontend (React)
│   ├── public/
│   └── src/
│       ├── components/ # Reusable components
│       ├── pages/      # Page components
│       ├── context/    # React context
│       └── App.js      # Main app component
└── package.json        # Root package.json
```

## API Documentation

All API endpoints are prefixed with `/api`:

- **Auth**: `/api/auth/register`, `/api/auth/login`, `/api/auth/me`
- **Doctors**: `/api/doctors` (GET, POST, PUT, DELETE)
- **Appointments**: `/api/appointments` (GET, POST, PUT, DELETE)
- **Hospitals**: `/api/hospitals` (GET, POST, PUT, DELETE)
- **Medical History**: `/api/medical-history` (GET, POST, PUT)
- **Users**: `/api/users` (GET, PUT, DELETE)

For detailed API documentation, see README.md

## Support

If you encounter any issues:
1. Check console logs for errors
2. Verify all dependencies are installed
3. Ensure MongoDB is running
4. Check `.env` file configuration


# Doctor Appointment System - MERN Stack

A comprehensive online doctor appointment system built with MongoDB, Express, React, and Node.js.

## 🚀 Quick Start

See [SETUP.md](./SETUP.md) for detailed installation instructions.

```bash
# Install dependencies
npm run install-all

# Create .env file (see .env.example)
# MONGODB_URI=mongodb://localhost:27017/doctor-appointment
# JWT_SECRET=your-secret-key
# PORT=5000

# Start the application
npm run dev
```

Visit http://localhost:3000 to use the application.

## 📋 Features

See [FEATURES.md](./FEATURES.md) for complete feature list.

### User Features
- Browse and search doctors
- View hospitals
- Book appointments
- View medical history
- Manage profile

### Admin Features
- Dashboard with statistics
- Manage doctors, appointments, hospitals, and users

## 🛠️ Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT Authentication
- bcryptjs

### Frontend
- React
- React Router
- Axios
- CSS3

## 📁 Project Structure

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

## 📚 Documentation

- [SETUP.md](./SETUP.md) - Installation and setup guide
- [FEATURES.md](./FEATURES.md) - Complete features list

## 📝 License

MIT


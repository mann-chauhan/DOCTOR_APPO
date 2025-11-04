# 🔗 Application Links

## 🌐 Main Application URL

**Frontend (User Interface):**
👉 **[http://localhost:3000](http://localhost:3000)**

**Backend API:**
👉 **[http://localhost:5000/api](http://localhost:5000/api)**

---

## ⚠️ IMPORTANT: Start the Application First!

Before opening these links, you need to:

1. **Install dependencies:**
   ```bash
   npm run install-all
   ```

2. **Create `.env` file** in root directory:
   ```
   MONGODB_URI=mongodb://localhost:27017/doctor-appointment
   JWT_SECRET=your-secret-key
   PORT=5000
   ```

3. **Start MongoDB** (local or Atlas)

4. **Start the application:**
   ```bash
   npm run dev
   ```

5. **Then open:** http://localhost:3000

---

## 📋 All Available Links

### Public Pages
- 🏠 **Home**: http://localhost:3000/
- 🔐 **Login**: http://localhost:3000/login
- 📝 **Register**: http://localhost:3000/register
- 👨‍⚕️ **Doctors**: http://localhost:3000/doctors
- 🏥 **Hospitals**: http://localhost:3000/hospitals

### User Pages (Login Required)
- 📅 **My Appointments**: http://localhost:3000/appointments
- 📋 **Medical History**: http://localhost:3000/medical-history
- 👤 **My Profile**: http://localhost:3000/profile

### Admin Pages (Admin Login Required)
- 📊 **Dashboard**: http://localhost:3000/admin/dashboard
- 👨‍⚕️ **Manage Doctors**: http://localhost:3000/admin/doctors
- 📅 **Manage Appointments**: http://localhost:3000/admin/appointments
- 🏥 **Manage Hospitals**: http://localhost:3000/admin/hospitals
- 👥 **Manage Users**: http://localhost:3000/admin/users

---

## 🚀 Quick Start Commands

```bash
# Install everything
npm run install-all

# Create admin user (optional)
npm run create-admin

# Start both servers
npm run dev
```

---

## 💡 Need Help?

1. Check **SETUP.md** for detailed instructions
2. Make sure MongoDB is running
3. Check terminal for any error messages
4. Verify `.env` file exists and is configured correctly

---

**Ready to start? Run `npm run dev` then open http://localhost:3000 !**


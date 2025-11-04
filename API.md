# Doctor Appointment System - API Documentation

## Base URL
`http://localhost:5000/api` (Development)
`https://your-domain.com/api` (Production)

## Authentication

Most endpoints require authentication via JWT token in the Authorization header:
```
Authorization: Bearer <token>
```

## Endpoints

### Authentication

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123",
  "phone": "1234567890",
  "role": "patient" // optional, defaults to "patient"
}
```

**Response:**
```json
{
  "token": "jwt_token_here",
  "user": {
    "id": "user_id",
    "name": "John Doe",
    "email": "john@example.com",
    "role": "patient"
  }
}
```

#### Login
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "token": "jwt_token_here",
  "user": {
    "id": "user_id",
    "name": "John Doe",
    "email": "john@example.com",
    "role": "patient"
  }
}
```

#### Get Current User
```http
GET /api/auth/me
Authorization: Bearer <token>
```

---

### Doctors

#### Get All Doctors
```http
GET /api/doctors?specialization=Cardiology&search=doctor name
```

**Query Parameters:**
- `specialization` (optional): Filter by specialization
- `search` (optional): Search by name or specialization

#### Get Single Doctor
```http
GET /api/doctors/:id
```

#### Create Doctor (Admin Only)
```http
POST /api/doctors
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "userId": "user_id",
  "specialization": "Cardiology",
  "qualification": "MD",
  "experience": 10,
  "consultationFee": 100,
  "hospitalId": "hospital_id",
  "bio": "Doctor bio"
}
```

#### Update Doctor (Admin Only)
```http
PUT /api/doctors/:id
Authorization: Bearer <admin_token>
```

#### Delete Doctor (Admin Only)
```http
DELETE /api/doctors/:id
Authorization: Bearer <admin_token>
```

---

### Appointments

#### Get Appointments
```http
GET /api/appointments
Authorization: Bearer <token>
```

**Response:** Returns patient's appointments (for patients) or all appointments (for admin)

#### Get Single Appointment
```http
GET /api/appointments/:id
Authorization: Bearer <token>
```

#### Create Appointment
```http
POST /api/appointments
Authorization: Bearer <token>
Content-Type: application/json

{
  "doctorId": "doctor_id",
  "hospitalId": "hospital_id", // optional
  "appointmentDate": "2024-12-31",
  "appointmentTime": "10:00",
  "reason": "Regular checkup"
}
```

#### Update Appointment
```http
PUT /api/appointments/:id
Authorization: Bearer <token>
Content-Type: application/json

{
  "status": "confirmed" // or "cancelled", "completed"
}
```

#### Delete Appointment
```http
DELETE /api/appointments/:id
Authorization: Bearer <token>
```

---

### Hospitals

#### Get All Hospitals
```http
GET /api/hospitals?city=New York&search=hospital name
```

**Query Parameters:**
- `city` (optional): Filter by city
- `search` (optional): Search by name or city

#### Get Single Hospital
```http
GET /api/hospitals/:id
```

#### Create Hospital (Admin Only)
```http
POST /api/hospitals
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "name": "City Hospital",
  "address": "123 Main St",
  "city": "New York",
  "state": "NY",
  "phone": "1234567890",
  "email": "info@hospital.com",
  "website": "https://hospital.com",
  "description": "Hospital description",
  "facilities": ["Emergency", "ICU", "Lab"]
}
```

#### Update Hospital (Admin Only)
```http
PUT /api/hospitals/:id
Authorization: Bearer <admin_token>
```

#### Delete Hospital (Admin Only)
```http
DELETE /api/hospitals/:id
Authorization: Bearer <admin_token>
```

---

### Medical History

#### Get Medical History
```http
GET /api/medical-history?patientId=user_id
Authorization: Bearer <token>
```

**Query Parameters:**
- `patientId` (optional): Filter by patient (admin only)

#### Get Single Record
```http
GET /api/medical-history/:id
Authorization: Bearer <token>
```

#### Create Medical History (Admin Only)
```http
POST /api/medical-history
Authorization: Bearer <admin_token>
Content-Type: application/json

{
  "patientId": "user_id",
  "doctorId": "doctor_id",
  "appointmentId": "appointment_id",
  "diagnosis": "Common cold",
  "symptoms": ["Cough", "Fever"],
  "prescription": [
    {
      "medicineName": "Paracetamol",
      "dosage": "500mg",
      "duration": "7 days",
      "instructions": "Take after meals"
    }
  ],
  "testReports": [
    {
      "testName": "Blood Test",
      "testDate": "2024-01-01",
      "result": "Normal",
      "fileUrl": "https://..."
    }
  ],
  "notes": "Patient notes"
}
```

#### Update Medical History (Admin Only)
```http
PUT /api/medical-history/:id
Authorization: Bearer <admin_token>
```

---

### Users

#### Get All Users (Admin Only)
```http
GET /api/users
Authorization: Bearer <admin_token>
```

#### Get Single User
```http
GET /api/users/:id
Authorization: Bearer <token>
```

#### Update User
```http
PUT /api/users/:id
Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "Updated Name",
  "phone": "9876543210",
  "dateOfBirth": "1990-01-01",
  "gender": "male",
  "address": "123 Main St"
}
```

#### Delete User (Admin Only)
```http
DELETE /api/users/:id
Authorization: Bearer <admin_token>
```

---

## Error Responses

### 400 Bad Request
```json
{
  "message": "Error message here"
}
```

### 401 Unauthorized
```json
{
  "message": "No token, authorization denied"
}
```

### 403 Forbidden
```json
{
  "message": "Access denied. Admin only."
}
```

### 404 Not Found
```json
{
  "message": "Resource not found"
}
```

### 500 Internal Server Error
```json
{
  "message": "Something went wrong!",
  "error": "Error details"
}
```

## Status Codes

- `200` - Success
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `500` - Internal Server Error


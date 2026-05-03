# Hospital Reservation System - Backend API

A comprehensive RESTful API for managing hospital reservations, patient appointments, doctor profiles, and in-patient admissions.

## Features

- **User Authentication**: Patient registration and login with JWT tokens
- **Doctor Directory**: Browse doctors by specialization with availability management
- **Appointment Management**: Book, reschedule, and cancel appointments
- **In-Patient Admissions**: Request and manage hospital admissions
- **Patient Profiles**: Manage personal and medical information
- **Security**: Password hashing and JWT authentication

## Technology Stack

- **Node.js** - JavaScript runtime
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Mongoose** - ODM for MongoDB
- **JWT** - Authentication
- **bcryptjs** - Password hashing

## Installation

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- npm or yarn

### Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd hospital-reservation-system/backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and add your configuration:
   ```
   NODE_ENV=development
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/hospital-reservation
   JWT_SECRET=your_secure_secret_key
   JWT_EXPIRE=7d
   ```

4. **Start the server**
   ```bash
   npm run dev
   ```
   Server will run on `http://localhost:5000`

## API Endpoints

### Authentication (`/api/auth`)

- `POST /register` - Register new patient
- `POST /login` - Login patient
- `GET /profile` - Get patient profile (Auth required)
- `PUT /profile` - Update patient profile (Auth required)

### Doctors (`/api/doctors`)

- `GET /` - List all doctors (with filters)
- `GET /:doctorId` - Get doctor details
- `GET /:doctorId/available-slots` - Get available appointment slots
- `POST /search` - Search doctors

### Appointments (`/api/appointments`)

- `POST /` - Book appointment (Auth required)
- `GET /` - Get patient's appointments (Auth required)
- `GET /:appointmentId` - Get appointment details (Auth required)
- `PUT /:appointmentId/reschedule` - Reschedule appointment (Auth required)
- `PUT /:appointmentId/cancel` - Cancel appointment (Auth required)

### Admissions (`/api/admissions`)

- `POST /` - Request admission (Auth required)
- `GET /` - Get patient's admissions (Auth required)
- `GET /:admissionId` - Get admission details (Auth required)
- `PUT /:admissionId` - Update admission (Auth required)
- `PUT /:admissionId/cancel` - Cancel admission (Auth required)

## Database Models

### User (Patient)
- Personal information
- Medical history
- Emergency contact
- Account status

### Doctor
- Professional credentials
- Specialization
- Available slots
- Ratings and reviews
- Consultation fees

### Appointment
- Patient reference
- Doctor reference
- Date and time slot
- Consultation type
- Appointment status
- Prescription (if completed)

### Admission
- Patient reference
- Doctor reference
- Room allocation
- Admission/discharge dates
- Medical details
- Insurance information

## Authentication

All protected routes require JWT authentication. Include the token in the Authorization header:

```
Authorization: Bearer <your_jwt_token>
```

## Error Handling

The API returns appropriate HTTP status codes:

- `200` - Success
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `500` - Internal Server Error

## Development

### Running Tests
```bash
npm test
```

### Linting
```bash
npm run lint
```

## Future Enhancements

- Email notifications
- SMS reminders
- Payment integration
- Admin dashboard
- Staff management
- Hospital inventory
- Billing system
- Report generation

## Contributing

1. Create a new branch (`git checkout -b feature/amazing-feature`)
2. Commit your changes (`git commit -m 'Add amazing feature'`)
3. Push to the branch (`git push origin feature/amazing-feature`)
4. Open a Pull Request

## License

ISC

## Support

For support, email: support@medicarehospital.com  
Phone: +1-800-123-4567

---

**Made with ❤️ for better healthcare management**

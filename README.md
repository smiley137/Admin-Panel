# MovieHub — Full-stack Movie Booking System

A professional movie booking platform with admin panel and user website, built with Node.js, Express, MongoDB, React, and Tailwind CSS.

## Features

### User Website
- 🎬 Browse movies with beautiful, responsive grid layout
- 🔍 Search movies by title
- 📱 Movie detail pages with showtimes, cast, and trailers
- 🎫 Interactive seat selection
- 🍿 Snack and drink selection
- 💳 Complete checkout and payment process
- ✅ Booking confirmation page

### Admin Panel
- ➕ Add, edit, and delete movies
- 🎭 Manage movie details (description, showtimes, cast, pricing)
- 👁️ Toggle movie visibility (active/inactive)
- 📊 View all movies with search functionality

## Tech Stack

- **Backend**: Node.js, Express, MongoDB (Mongoose)
- **Frontend**: React, Vite, React Router, Tailwind CSS, Axios
- **Database**: MongoDB

## Quick Start

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or MongoDB Atlas)

### Backend Setup

1. Navigate to backend directory:
   ```bash
   cd backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create `.env` file (or use default):
   ```env
   MONGO_URI=mongodb://localhost:27017/moviedb
   PORT=5000
   ```

4. Seed the database:
   ```bash
   # Seed movies
   npm run seed
   
   # Seed snacks
   npm run seed:snacks
   ```

5. Start the server:
   ```bash
   npm run dev
   ```

   Backend will run on `http://localhost:5000`

### Frontend Setup

1. Navigate to frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create `.env` file (optional, defaults to localhost:5000):
   ```env
   VITE_API_URL=http://localhost:5000/api
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```

   Frontend will run on `http://localhost:5173`

## Usage

### User Flow

1. **Home Page** (`/`): Browse available movies
2. **Movie Detail** (`/movie/:id`): View movie details and select showtime
3. **Seat Selection** (`/booking/:id`): Choose your seats
4. **Snack Selection** (`/snacks/:id`): Add snacks and drinks to your order
5. **Checkout** (`/checkout/:id`): Complete payment
6. **Confirmation** (`/booking-success/:id`): View booking confirmation

### Admin Flow

1. **Admin Panel** (`/admin`): Manage movies
   - Click "Add Movie" to create new movies
   - Click "Edit" to modify existing movies
   - Click "Delete" to remove movies
   - Use search to find specific movies

## API Endpoints

### Movies
- `GET /api/movies` - Get all active movies (add `?admin=true` for all movies)
- `GET /api/movies/:id` - Get movie by ID
- `POST /api/movies` - Create movie (admin)
- `PUT /api/movies/:id` - Update movie (admin)
- `DELETE /api/movies/:id` - Delete movie (admin)

### Bookings
- `GET /api/bookings` - Get all bookings
- `GET /api/bookings/:id` - Get booking by ID
- `POST /api/bookings` - Create booking
- `PUT /api/bookings/:id/payment` - Update payment status

### Seats
- `GET /api/seats/:movieId/:showtime` - Get seat availability

### Snacks
- `GET /api/snacks` - Get all available snacks
- `GET /api/snacks/:id` - Get snack by ID
- `POST /api/snacks` - Create snack (admin)
- `PUT /api/snacks/:id` - Update snack (admin)

## Database Models

### Movie
- title, director, year, genre, rating
- poster, description, duration
- showtimes (array of dates)
- price, trailer, cast, language
- isActive (boolean)

### Booking
- movieId, userId, seats, snacks
- showtime, totalAmount
- paymentStatus, paymentId

### Seat
- movieId, showtime, row, number
- isBooked, bookingId

### Snack
- name, description, price, image
- category, available

## Responsive Design

The application is fully responsive and optimized for:
- 📱 Mobile devices (320px+)
- 📱 Tablets (768px+)
- 💻 Desktops (1024px+)
- 🖥️ Large screens (1280px+)

## Notes

- Payment processing is simulated for demo purposes. In production, integrate with a real payment gateway (Stripe, PayPal, etc.).
- User authentication is not implemented. The system uses a default 'guest' user ID.
- Seat availability is checked in real-time during booking.
- Movies marked as `isActive: false` are hidden from the user website but visible in admin panel.

## License

MIT

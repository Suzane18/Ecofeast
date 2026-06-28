# 🌱 Ecofeast

> A full-stack web platform that connects food donors, NGOs, and logistics volunteers to reduce food waste and support communities in need.

## 📖 Project Overview

### Problem Statement
Food waste remains a major global issue, while many communities still face food insecurity. The disconnect between surplus food availability and those who need it creates avoidable losses.

### Motivation
Ecofeast was built to create a practical bridge between donors, NGOs, and logistics partners so surplus food can be redistributed efficiently and transparently.

### Solution
The platform enables donors to list surplus food, NGOs to request available donations, and logistics volunteers to coordinate pickups and deliveries through a unified workflow.

### Key Objectives
- Reduce food waste through timely redistribution
- Provide a trust-based donation flow between stakeholders
- Support role-based collaboration for donors, NGOs, logistics staff, and admins
- Offer analytics and audit visibility for oversight

## ✨ Features

- 🍲 Donor dashboard to publish surplus food listings
- 🤝 NGO portal to browse and request food donations
- 🚚 Logistics workflow for pickup and delivery coordination
- 🛡️ Role-based access control for admin, donor, NGO, and logistics users
- 📍 Location-aware donation handling with Google Maps integration
- 📊 Admin analytics and monitoring dashboard
- 📝 Audit log tracking for important actions
- 🔔 Notification support for donation and delivery updates

## 🛠️ Tech Stack

### Frontend

| Technology | Purpose |
| --- | --- |
| HTML5 | Page structure |
| CSS3 | Responsive UI styling |
| JavaScript | Interactive frontend logic |
| Google Maps API | Location and mapping support |
| Chart.js | Administrative charts and analytics |

### Backend

| Technology | Purpose |
| --- | --- |
| Python | Core application logic |
| Flask | Web framework |
| Flask-Login | User authentication and session management |
| Flask-SQLAlchemy | ORM and database interaction |
| Flask-Migrate | Database migrations |
| Flask-CORS | Cross-origin resource handling |

### Database

| Technology | Purpose |
| --- | --- |
| PostgreSQL | Production relational database |
| SQLite | Local development fallback |

### Tools & Libraries

| Tool | Purpose |
| --- | --- |
| Python-dotenv | Environment variable loading |
| bcrypt | Password hashing |
| Jinja2 | Server-side templating |

## 🏗️ System Architecture

Ecofeast follows a modular Flask architecture:

1. The Flask app is created through an application factory in the main app package.
2. Blueprints handle major workflows for authentication, donor operations, NGO actions, logistics coordination, and admin management.
3. SQLAlchemy models manage users, donations, requests, deliveries, and audit data.
4. Templates and static assets provide the web interface, while the backend handles role-based access and business logic.
5. The app supports both PostgreSQL and SQLite depending on the environment configuration.

## 📂 Folder Structure

```text
Ecofeast/
├─ app/
│  ├─ blueprints/
│  │  ├─ admin.py
│  │  ├─ api.py
│  │  ├─ auth.py
│  │  ├─ donor.py
│  │  ├─ logistics.py
│  │  ├─ main.py
│  │  └─ ngo.py
│  ├─ models/
│  ├─ static/
│  ├─ templates/
│  └─ __init__.py
├─ config.py
├─ requirements.txt
├─ run.py
├─ .env.example
├─ INSTALLATION_GUIDE.md
├─ API_REFERENCE.md
├─ TESTING_GUIDE.md
└─ README.md
```

## ⚙️ Installation & Setup

### Prerequisites

- Python 3.10+
- PostgreSQL (optional for production; SQLite works for local development)
- pip
- Git

### 1. Clone the repository

```bash
git clone https://github.com/Suzane18/Ecofeast.git
cd Ecofeast
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate
# On Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Copy the example file and update the values:

```bash
cp .env.example .env
```

Example configuration:

```env
FLASK_ENV=development
SECRET_KEY=your_secret_key
JWT_SECRET_KEY=your_jwt_secret
DATABASE_URL=postgresql://user:password@localhost:5432/ecofeast_dev
GOOGLE_MAPS_KEY=your_google_maps_key
```

### 5. Run the application

```bash
python run.py
```

The app will be available at `http://localhost:5000`.

## 💻 Usage Guide

1. Register an account with the appropriate role: donor, NGO, logistics, or admin.
2. Log in to the dashboard.
3. Donors can create food listings with location details.
4. NGOs can browse listings and request donations.
5. Logistics users can manage delivery pickups and statuses.
6. Admins review listings, permissions, and platform activity.

## 🔌 API Overview

| Endpoint | Method | Description |
| --- | --- | --- |
| `/auth/register` | POST | Register a new user |
| `/auth/login` | POST | Log in a user |
| `/auth/logout` | GET | Log out the current user |
| `/donor/dashboard` | GET | Donor dashboard |
| `/ngo/browse` | GET | Browse available donations |
| `/logistics/dashboard` | GET | Logistics dashboard |
| `/admin/dashboard` | GET | Admin analytics dashboard |
| `/api/notifications/unread` | GET | Get unread notifications |
| `/api/distance` | POST | Calculate distance between locations |

## 🗄️ Database Schema

The application uses SQLAlchemy models to manage the core entities:

- **User** — stores account details, role, and contact metadata
- **Donation** — stores food listing details and donor association
- **Request** — links NGOs to available donations
- **Delivery** — tracks pickup and delivery workflow
- **AuditLog** — records admin and platform actions for oversight

## 🔒 Security Features

- Password hashing using `bcrypt`
- Role-based access control for each user type
- Session-based authentication with Flask-Login
- Environment-based secret configuration
- CSRF and input validation support
- Relational database protection with SQLAlchemy ORM

## 🧪 Testing

### Manual Testing
- Register and log in as various roles
- Create and approve food donations
- Request donations as an NGO
- Track delivery status changes
- Review admin dashboard analytics

### Recommended Future Testing
- Unit tests for models and controllers
- Integration tests for blueprint routes
- End-to-end testing of donation workflows

## 🌐 Deployment

### Recommended deployment steps
1. Set `FLASK_ENV=production`
2. Configure a production PostgreSQL database
3. Set strong `SECRET_KEY` and `JWT_SECRET_KEY` values
4. Deploy the Flask app to a platform such as Render, Railway, or Heroku
5. Configure the Google Maps API key and secure environment variables

## 🔮 Future Enhancements

- [ ] Add real-time chat for donors and NGOs
- [ ] Introduce mobile-friendly push notifications
- [ ] Add AI-based food demand forecasting
- [ ] Improve route optimization for logistics delivery
- [ ] Add multilingual support for wider adoption

### Password Requirements
- Minimum 8 characters
- At least 1 uppercase letter
- At least 1 lowercase letter
- At least 1 digit
- At least 1 special character

## Database Schema

### Key Tables
- **users** - All users with role-based access
- **donations** - Food listings from donors
- **food_requests** - NGO requests for food
- **deliveries** - Delivery tracking
- **notifications** - In-app notifications
- **feedback** - User feedback
- **audit_logs** - Admin action tracking

### Database Indexing
- Indexed on `user_id`, `created_at`, `status` for fast queries
- Foreign key constraints for data integrity
- Proper pagination for large datasets

### Caching Opportunities
- Cache user locations for map display
- Cache admin dashboard statistics (refresh every 5 minutes)
- Cache available donations list

## Future Enhancements

1. **Email Notifications** via SendGrid or similar
2. **SMS Notifications** via Twilio
3. **Real-time Updates** using WebSockets
4. **Mobile App** using React Native or Flutter
5. **Payment Integration** for optional donations
6. **Machine Learning** for demand prediction
7. **Carbon Credit Tracking** and certification
8. **Integration with Food Banks** and Government Programs
9. **Blockchain** for transparent tracking
10. **Gamification** with leaderboards and badges

## Troubleshooting

### Database Connection Issues
```bash
# Check PostgreSQL is running
psql -U postgres

# Verify DATABASE_URL in .env
# Format: postgresql://username:password@localhost:5432/database_name
```

### Port Already in Use
```bash
# Change port in run.py or run with alternative port
python run.py --port=5001
```

### Map Not Loading
- Verify Google Maps API key in .env
- Check API key has necessary permissions enabled
- Ensure billing is enabled on Google Cloud Platform

### Static Files Not Loading
- Clear browser cache
- Check static files path in config.py
- Verify CSS/JS files exist in `app/static/`


## Acknowledgments

- Built with Flask, PostgreSQL, and Vanilla JavaScript
- Google Maps API for geolocation services
- Chart.js for analytics visualization
- Community supporters and contributors

---

**Together, we can reduce food waste and feed our communities.** 🌍💚

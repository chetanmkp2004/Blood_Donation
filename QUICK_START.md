# Quick Start Guide - Django + React Native Blood Donation App

## ✅ Setup Complete! Here's what was configured:

### Django Backend (API Server)
- ✅ Django REST Framework installed and configured
- ✅ CORS headers configured for React Native
- ✅ Token-based authentication set up
- ✅ API endpoints created for user authentication
- ✅ Database migrations applied
- ✅ Server tested and working

### React Native Frontend
- ✅ API service layer created with Axios
- ✅ Authentication context for state management
- ✅ Login/Register screens implemented
- ✅ Dashboard screen for authenticated users
- ✅ AsyncStorage for token persistence
- ✅ App structure integrated

## 🚀 How to Run Both Applications

### 1. Start Django Backend
```bash
cd g:\Blood_Donation\backend\Blood_Donation
python manage.py runserver
```
- Django will run on: http://127.0.0.1:8000
- API endpoints available at: http://127.0.0.1:8000/api/

### 2. Start React Native Frontend
```bash
cd g:\Blood_Donation\frontend\BloodDonation
npm start
```
- Choose your preferred platform (iOS/Android/Web)
- The app will connect to your Django backend automatically

## 📱 Testing the Connection

1. **Start Django server** (if not already running)
2. **Start React Native app**
3. **Register a new user** in the app
4. **Login with your credentials**
5. **Check the dashboard** - it should show your user info and API connection status

## 🔧 Current Features

### Authentication
- User registration
- User login/logout
- Token-based session management
- User profile display

### API Endpoints Available
- `GET /api/` - API overview
- `POST /api/auth/register/` - User registration
- `POST /api/auth/login/` - User login
- `POST /api/auth/logout/` - User logout
- `GET /api/auth/profile/` - Get user profile

## 🛠 What You Can Do Next

### 1. Expand the API (Django side)
Add these features to your Django backend:
- Blood donor profiles
- Blood request system
- Location-based matching
- Blood bank information
- Donation history

### 2. Enhance the Frontend (React Native side)
Add these screens/features:
- Donor registration with blood type
- Blood request creation
- Map integration for location
- Push notifications
- Profile management

### 3. Add More Functionality
- Search and filtering
- Real-time messaging
- Photo uploads
- Appointment scheduling
- Emergency alerts

## 📋 Development Tips

### Backend Development
- Add new API endpoints in `api/views.py`
- Create database models in `api/models.py`
- Update URL patterns in `api/urls.py`
- Run `python manage.py makemigrations` after model changes
- Run `python manage.py migrate` to apply changes

### Frontend Development
- Add new API calls in `services/ApiService.ts`
- Create new screens in `components/`
- Update navigation in app router files
- Use the `useAuth()` hook for authentication state

### Testing
- Test API endpoints using: `curl http://127.0.0.1:8000/api/auth/login/`
- Use Django admin: `python manage.py createsuperuser`
- Check React Native debugger for network requests

## 📚 Important Files

### Backend
- `settings.py` - Django configuration
- `api/views.py` - API endpoint handlers
- `api/urls.py` - API URL routing
- `requirements.txt` - Python dependencies

### Frontend
- `services/ApiService.ts` - API communication layer
- `contexts/AuthContext.tsx` - Authentication state management
- `constants/ApiConfig.ts` - API configuration
- `components/LoginScreen.tsx` - Login interface
- `components/DashboardScreen.tsx` - Main app interface

## 🔐 Security Notes

- In production, change Django `SECRET_KEY`
- Use HTTPS for production API
- Set `CORS_ALLOW_ALL_ORIGINS = False` in production
- Implement proper input validation
- Add rate limiting for API endpoints

## 🆘 Troubleshooting

### Django Issues
- **Module not found**: Run `pip install -r requirements.txt`
- **Database errors**: Run `python manage.py migrate`
- **CORS errors**: Check settings.py CORS configuration

### React Native Issues
- **Network errors**: Ensure Django server is running
- **Import errors**: Check if packages are installed with `npm install`
- **Authentication issues**: Clear AsyncStorage and try again

Your Django + React Native blood donation app is now connected and ready for development! 🎉

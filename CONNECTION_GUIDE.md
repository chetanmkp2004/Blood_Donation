# Django + React Native Connection Guide

This guide explains how your Django backend connects with your React Native frontend application.

## Architecture Overview

```
React Native App (Frontend) ←→ HTTP/HTTPS ←→ Django API (Backend)
```

## Backend Setup (Django)

### 1. Dependencies Installed
- `djangorestframework`: For creating REST APIs
- `django-cors-headers`: For handling Cross-Origin Resource Sharing (CORS)

### 2. Key Configuration Files

#### settings.py
- Added REST Framework and CORS to `INSTALLED_APPS`
- Configured CORS to allow requests from React Native
- Set up REST Framework authentication with tokens
- Configured allowed hosts

#### API Structure
- `api/views.py`: Contains API endpoints for authentication and user management
- `api/urls.py`: URL routing for API endpoints
- `Blood_Donation/urls.py`: Main URL configuration including API routes

### 3. Available API Endpoints

| Endpoint | Method | Description | Authentication |
|----------|---------|-------------|---------------|
| `/api/` | GET | API Overview | No |
| `/api/auth/register/` | POST | User Registration | No |
| `/api/auth/login/` | POST | User Login | No |
| `/api/auth/logout/` | POST | User Logout | Yes |
| `/api/auth/profile/` | GET | Get User Profile | Yes |

## Frontend Setup (React Native)

### 1. Dependencies Installed
- `@react-native-async-storage/async-storage`: For storing auth tokens locally
- `axios`: For making HTTP requests to the Django API

### 2. Key Files Created

#### API Service (`services/ApiService.ts`)
- Handles all communication with Django backend
- Manages authentication tokens
- Provides methods for login, register, logout, etc.

#### Authentication Context (`contexts/AuthContext.tsx`)
- React Context for managing authentication state
- Provides authentication methods to components
- Handles user session management

#### UI Components
- `LoginScreen.tsx`: Login and registration interface
- `DashboardScreen.tsx`: Main app interface for authenticated users

## How the Connection Works

### 1. Authentication Flow

```
1. User enters credentials in React Native app
2. App sends POST request to Django `/api/auth/login/`
3. Django validates credentials and returns auth token
4. React Native stores token in AsyncStorage
5. Future API requests include token in Authorization header
```

### 2. API Communication

```typescript
// Example API call from React Native
const response = await ApiService.login({
  username: 'user@example.com',
  password: 'password123'
});
```

### 3. Token-Based Authentication

- Django uses Token Authentication
- React Native stores tokens securely
- Tokens are included in API request headers
- Automatic token management through axios interceptors

## Running the Applications

### Backend (Django)
```bash
cd g:\Blood_Donation\backend\Blood_Donation
python manage.py runserver
```
- Django runs on `http://127.0.0.1:8000`
- API available at `http://127.0.0.1:8000/api/`

### Frontend (React Native)
```bash
cd g:\Blood_Donation\frontend\BloodDonation
npm start
```
- Expo development server starts
- App can run on iOS/Android simulator or device

## Network Configuration

### For Development
- Django: `http://127.0.0.1:8000`
- React Native: Connects to Django via IP address
- CORS configured to allow frontend origin

### For Production
- Use HTTPS for Django API
- Update `ApiConfig.ts` with production URL
- Set `CORS_ALLOW_ALL_ORIGINS = False` in Django settings
- Configure proper allowed origins

## Security Considerations

1. **Token Storage**: Tokens stored securely in AsyncStorage
2. **CORS**: Properly configured for development
3. **HTTPS**: Use in production
4. **Token Expiration**: Implement token refresh if needed
5. **Input Validation**: Validate data on both frontend and backend

## Testing the Connection

### 1. Test Backend API
```bash
# Test API overview
curl http://127.0.0.1:8000/api/

# Test user registration
curl -X POST http://127.0.0.1:8000/api/auth/register/ \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","email":"test@example.com","password":"testpass123"}'
```

### 2. Test Frontend
1. Start Django server
2. Start React Native app
3. Try registering a new user
4. Try logging in
5. Check dashboard for connection status

## Troubleshooting

### Common Issues
1. **CORS Errors**: Check Django CORS settings
2. **Network Errors**: Ensure Django server is running
3. **Authentication Errors**: Verify token handling
4. **Module Not Found**: Check package installations

### Debug Tips
- Check Django console for API request logs
- Use React Native debugger for network requests
- Verify API endpoints in browser
- Check AsyncStorage for stored tokens

## Next Steps

1. Create more API endpoints for blood donation features
2. Implement proper error handling
3. Add loading states and better UI
4. Implement push notifications
5. Add data validation and sanitization
6. Set up proper production deployment

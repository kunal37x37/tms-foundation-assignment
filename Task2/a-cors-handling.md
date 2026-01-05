
## a) API Integration: Handling Cross-Origin Resource Sharing (CORS)  
### in a Django + React Architecture

---

### Introduction

In a **decoupled architecture** where **React** handles the frontend and **Django REST Framework** handles the backend, the two applications usually run on **different domains or ports**.  
For example:

- React Frontend → `http://localhost:3000`
- Django Backend → `http://localhost:8000`

Due to browser security policies, this setup introduces **Cross-Origin Resource Sharing (CORS)** challenges that must be handled correctly to allow secure API communication.

---

### What is CORS?

**CORS (Cross-Origin Resource Sharing)** is a browser security mechanism that restricts web applications from making requests to a domain different from the one that served the frontend.

Without proper CORS configuration:
- API requests from React to Django will fail
- Browsers will block requests for security reasons

---

### Why CORS Matters for a Non-Profit Platform

For platforms like **TMS Foundation**, CORS handling is critical because:

- React frontend may be hosted on a CDN or separate server
- APIs handle sensitive data (donations, volunteers, admin access)
- Security and data integrity must not be compromised

---

### Recommended Approach: Using `django-cors-headers`

The industry-standard solution is to use the **`django-cors-headers`** package.

---

### Step-by-Step CORS Implementation

#### 1. Install the Package

```bash
pip install django-cors-headers
```

#### 2. Add to INSTALLED_APPS
```bash
INSTALLED_APPS = [
    ...
    "corsheaders",
]
```

#### 3. Add Middleware (Important Order)
```bash
MIDDLEWARE = [
    "corsheaders.middleware.CorsMiddleware",
    "django.middleware.common.CommonMiddleware",
    ...
]
```
#### 4. Configure Allowed Origins
```bash
CORS_ALLOWED_ORIGINS = [
    "http://localhost:3000",
    "https://tmsfoundation.org",
]
```
##### For development only:
```bash
CORS_ALLOW_ALL_ORIGINS = True
```

#### 5. Allow Credentials (If Required)
```bash
CORS_ALLOW_CREDENTIALS = True
```
##### Useful for:
- JWT authentication
- Session-based login
- Secure admin access

### Security Best Practices
- llow only trusted domains
- Use HTTPS in production
- Combine CORS with:
     - JWT authentication
     - Role-based permissions
     - CSRF protection where applicable

---
### Conclusion

#### Handling CORS properly ensures that:

   - React and Django communicate securely
   - Browsers allow API access
   - Sensitive non-profit data remains protected

A well-configured CORS policy is a foundation-level security requirement for any modern decoupled web application.


---

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


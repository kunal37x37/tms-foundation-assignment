## b) State Management: Choosing Redux / Context API vs useState  
### for a Non-Profit Platform

---

### Introduction

React offers multiple ways to manage application state, ranging from simple local state using `useState` to global state solutions like **Context API** and **Redux**.

Choosing the correct approach is crucial for:
- Performance
- Maintainability
- Scalability

This decision becomes especially important for a **non-profit platform** with multiple user roles and complex workflows.

---

### Understanding State Management Options

#### 1. `useState` (Local State)
- Component-level state
- Simple and lightweight
- Best for isolated UI behavior

#### 2. Context API (Global State – Medium Scale)
- Built-in React solution
- Avoids prop drilling
- Suitable for app-wide shared data

#### 3. Redux (Global State – Large Scale)
- Centralized state store
- Predictable state changes
- Best for complex applications

---

### When to Use `useState`

Use `useState` when:
- State is limited to a single component
- Data does not need to persist across pages
- Example:
  - Form inputs
  - Modal open/close state
  - UI toggles

➡️ **Example for TMS Foundation:**  
Temporary form validation state during registration.

---

### When to Use Context API

Use **Context API** when:
- State must be shared across multiple components
- Application size is medium
- Complexity is manageable

**Common use cases:**
- User authentication state
- Theme or language preference
- Logged-in user role (Admin / Volunteer / Donor)

➡️ **Example for TMS Foundation:**  
Sharing logged-in user data across dashboard, profile, and booking pages.

---

### When to Use Redux

Redux is recommended when:
- Application state becomes complex
- Multiple components depend on the same data
- Frequent API calls and async logic exist

**Key scenarios:**
- Donation workflows
- Volunteer management
- Booking or reporting dashboards
- Real-time updates or notifications

➡️ **Example for TMS Foundation:**  
Managing donation transactions, admin analytics, and global loading states.

---

### Why Redux is Useful for Long-Term Growth

- Centralized state improves debugging
- Predictable data flow using actions and reducers
- Middleware (Redux Thunk / Toolkit) simplifies async API handling

This makes Redux ideal for:
- Multi-role platforms
- Scalable non-profit systems
- Team-based development environments

---

### Performance & Maintainability Considerations

| Feature | useState | Context API | Redux |
|--------|----------|-------------|--------|
| Learning Curve | Low | Medium | High |
| Scalability | Low | Medium | High |
| Debugging | Simple | Moderate | Excellent |
| Best Use Case | Local UI | Shared App State | Complex Global State |

---

### Conclusion

For a non-profit platform like **TMS Foundation**:

- Use **useState** for simple, local UI logic  
- Use **Context API** for authentication and shared app-level data  
- Use **Redux** when the application scales and business logic becomes complex  

Choosing the right state management strategy ensures **performance, clarity, and future readiness**.

# Full-Stack App 

A static prototype web application demonstrating email registration, login, role-based access control, and CRUD operations for managing employees, departments, and user requests.

## 🎯 Quick Start

1. Open `index.html` in a web browser
2. Data automatically initializes with seeded admin account
3. Login with: **admin@example.com** / **admin123**
4. Or register a new account and verify email

---

## 📁 Project Files

```
├── index.html      # Main HTML file with all pages
├── script.js       # All JavaScript functionality
├── style.css       # Complete styling
└── README.md       # This documentation
```

---

## 🔑 Key Features

### 🔐 Authentication
- **Registration** - Sign up with email and password
- **Email Verification** - Simulated email verification process
- **Login/Logout** - Secure authentication with role-based access
- **Session Management** - Current user tracking throughout the app

### 👥 User Management
- **View Profile** - Display user information (name, email, role)
- **Edit Profile** - Update first and last name via modal
- **Role Assignment** - Admin or User roles with different permissions

### 📋 Requests System
- **Create Requests** - Submit requests with type and multiple items
- **Dynamic Items** - Add/remove items with quantities on the fly
- **Request Types** - Equipment, Leave, Resources
- **Status Tracking** - Color-coded status (Pending, Approved, Rejected)
- **Edit/Delete** - Modify or remove requests
- **User Filtering** - Each user sees only their own requests

### 🏢 Admin Features

#### Accounts Management
```javascript
goToPage('accounts')
```
- Create user accounts with email, password, role, and verification status
- Edit account details and reset passwords
- Delete accounts (with self-deletion prevention)
- View all user accounts in table format

#### Departments Management
```javascript
goToPage('departments')
```
- Create departments with name and description
- Edit existing departments
- Delete departments
- Pre-seeded with: Engineering, HR, Finance, IT, Accounting, Marketing

#### Employees Management
```javascript
goToPage('employees')
```
- Create employee records linked to existing users
- Assign positions and departments
- Track hire dates
- Edit and delete employee records
- Validates that user email exists before creating employee

### 🎨 User Interface
- **Responsive Design** - Works on desktop, tablet, and mobile
- **Navbar Navigation** - Full-Stack App on left, Login/Register on right
- **User Dropdown** - Shows when logged in with Profile, Requests, Admin links
- **Toast Notifications** - Real-time feedback (Success, Warning, Danger, Info)
- **Modal Forms** - Clean popup forms for adding/editing records
- **Status Badges** - Color-coded request statuses

---

## 🔧 Technical Details

### Storage System

All data is stored in `localStorage` under the key: `ipt_demo_v1`

```javascript
window.db = {
  accounts: [...],        // User accounts
  departments: [...],     // Departments list
  employees: [...],       // Employee records
  requests: [...]         // User requests
}
```

### Core Functions

#### Navigation
```javascript
goToPage(name)            // Switch between pages
updateNavbar()            // Update navbar based on login state
toggleDropdown()          // Show/hide user menu
```

#### Storage
```javascript
save(key, data)           // Save data to localStorage
load(key, defaultValue)   // Load data from localStorage
saveToStorage()           // Persist window.db
loadFromStorage()         // Load window.db on startup
```

#### Authentication
```javascript
handleRegister()          // Process user registration
simulateVerification()    // Simulate email verification
handleLogin()             // Authenticate user login
userLogout()              // Clear user session
getCurrentUser()          // Get current logged-in user
setCurrentUser(user)      // Set current user
```

#### Requests
```javascript
showRequestModal()        // Open request creation modal
handleAddRequest()        // Create or update request
editRequest(id)           // Load request for editing
deleteRequest(id)         // Delete request
loadRequests()            // Load user's requests into table
```

#### Accounts (Admin)
```javascript
showAddAccountForm()      // Open account creation form
handleAddAccount()        // Create or update account
editAccount(id)           // Load account for editing
deleteAccount(id)         // Delete account
resetPassword(id)         // Reset user password
loadAccounts()            // Load accounts into table
```

#### Departments (Admin)
```javascript
showDepartmentForm()      // Open department form
handleAddDepartment()     // Create or update department
editDepartment(id)        // Load department for editing
deleteDepartment(id)      // Delete department
loadDepartments()         // Load departments into table
```

#### Employees (Admin)
```javascript
showEmployeeForm()        // Open employee form
handleAddEmployee()       // Create or update employee
editEmployee(id)          // Load employee for editing
deleteEmployee(id)        // Delete employee
renderEmployeesTable()    // Load employees into table
```

#### UI/UX
```javascript
showToast(message, type)  // Display notification (success, warning, danger, info)
showEditProfileModal()    // Open profile editor
closeEditProfileModal()   // Close profile editor
handleEditProfile()       // Save profile changes
```

---

## 📝 Pages & Features

### Home Page
- Welcome message and feature list
- "Get Started" button linking to registration
- localStorage note

### Register Page
- First Name, Last Name, Email, Password fields
- Email uniqueness validation
- Creates account with `isVerified: false`

### Verify Email Page
- Shows simulated email verification message
- "Simulate Email Verification" button to verify account
- Links to login page

### Login Page
- Email and Password fields
- Validates account exists, password matches, and account is verified
- Sets current user and redirects to profile

### Profile Page
- Displays user name, email, and role
- "Edit Profile" button opens modal
- Modal allows updating first and last name

### My Requests Page
- Shows all user's requests in a table
- "+ New Request" button opens modal
- Request modal has:
  - Type dropdown (Equipment, Leave, Resources)
  - Dynamic item fields with add (+) and remove (×) buttons
  - Submit button to create/update request
- Request table shows:
  - Type, Items (as list), Status (with color badge), Date
  - Edit and Delete buttons

### Employees Page (Admin Only)
- "+ Add Employee" button opens form
- Form fields:
  - Employee ID (unique, required)
  - User Email (must exist in accounts, required)
  - Position (required)
  - Department (dropdown, required)
  - Hire Date (required)
- Table displays: ID, User, Position, Department, Actions
- Actions: Edit, Delete buttons

### Departments Page (Admin Only)
- "+ Add Department" button opens form
- Form fields:
  - Department Name (required)
  - Description (required)
- Table displays: Name, Description, Actions
- Actions: Edit, Delete buttons

### Accounts Page (Admin Only)
- "+ Add Account" button opens form
- Form fields:
  - First Name, Last Name (required)
  - Email (required, must be unique)
  - Password (required for new, optional for edit)
  - Role (User or Admin dropdown)
  - Verified checkbox
- Table displays: Name, Email, Role, Verified, Actions
- Actions: Edit, Reset Password, Delete buttons
- Verified shown as ✓ (green) or blank (red)

---

## 🚀 How to Use

### Getting Started

1. **Open the app**
   ```
   Double-click index.html or open in browser
   ```

2. **First login**
   - Use admin account: `admin@example.com` / `admin123`
   - Or register a new account

3. **Register New Account**
   - Click "Register" link
   - Fill in First Name, Last Name, Email, Password
   - Click "Sign Up"
   - Click "Simulate Email Verification"
   - You're verified and can login

### Using As Regular User

1. **Login** with your account
2. **View Profile** - See your user information
3. **Edit Profile** - Click "Edit Profile" to update name
4. **My Requests** - Create and manage your requests
   - Click "+ New Request"
   - Select type
   - Add items with quantities
   - Click "Submit Request"
   - View, edit, or delete your requests

### Using As Admin

1. **Login** with admin account
2. **Access Admin Pages** from dropdown menu
3. **Manage Accounts**
   - Add new user accounts
   - Edit existing accounts
   - Reset passwords
   - Delete accounts
4. **Manage Departments**
   - Create departments
   - Edit department info
   - Delete departments
5. **Manage Employees**
   - Add employees (must link to existing user)
   - Assign positions and departments
   - Set hire dates
   - Edit or delete employees

---

## 💾 Data Structure

### Accounts (Users)
```javascript
{
  id: timestamp,
  firstName: "string",
  lastName: "string",
  email: "string",
  password: "string",
  role: "admin" | "user",
  isVerified: boolean
}
```

### Departments
```javascript
{
  id: timestamp,
  name: "string",
  desc: "string"
}
```

### Employees
```javascript
{
  id: timestamp,
  employeeID: "string",        // Unique ID
  userID: number,              // Links to account.id
  userEmail: "string",         // From linked account
  position: "string",
  deptID: number,              // Links to department.id
  deptName: "string",
  hireDate: "string"           // Date format
}
```

### Requests
```javascript
{
  id: timestamp,
  type: "Equipment" | "Leave" | "Resources",
  items: [
    { name: "string", quantity: number }
  ],
  status: "Pending" | "Approved" | "Rejected",
  date: "string",
  employeeEmail: "string"      // User who created it
}
```

---

## 🔄 Authentication Flow

```
┌─────────────┐
│  Register   │
└──────┬──────┘
       │
┌──────▼─────────────┐
│ Verify Email       │
│ (Simulated)        │
└──────┬─────────────┘
       │
┌──────▼─────────────┐
│  Login              │
│  (Enter Creds)      │
└──────┬─────────────┘
       │
┌──────▼──────────────────┐
│  Authenticated           │
│  (setCurrentUser)        │
│  (updateNavbar)          │
└──────┬──────────────────┘
       │
┌──────▼──────────────────┐
│  User/Admin Features     │
└─────────────────────────┘
```

---

## 🎨 UI Components

### Toast Notifications
```javascript
showToast(message, type)
// Types: 'success', 'warning', 'danger', 'info'

// Examples:
showToast('Request saved successfully!', 'success')
showToast('Fill all fields', 'warning')
showToast('Password reset successfully!', 'success')
```

### Modals
- Profile Edit Modal
- Request Creation Modal
- Account, Employee, Department Forms (inline)

### Status Badges
- **Pending** - Yellow background
- **Approved** - Green background
- **Rejected** - Red background

---

## 🧪 Testing

### Test Accounts

**Admin Account (Pre-seeded)**
```
Email: admin@example.com
Password: admin123
Role: Admin
```

**Create Test Users**
1. Click "Register"
2. Fill in details
3. Click "Sign Up"
4. Simulate verification
5. Login and test features

### Test Workflows

**1. User Registration & Request**
- Register → Verify → Login → Create Request → View Request

**2. Admin Management**
- Login as admin → Create Account → Create Employee → View All

**3. Request Lifecycle**
- Create → Edit → View Status → Delete

---

## 🔧 Troubleshooting

### Data Not Saving

**Issue:** Data disappears after refresh

**Solution:**
```
1. Open DevTools (F12)
2. Go to Application → Local Storage
3. Look for 'ipt_demo_v1'
4. If missing, refresh page to reinitialize
5. If corrupted, delete and refresh to reset
```

### Cannot Login

**Issue:** "Invalid credentials" error

**Solution:**
- Use admin account: `admin@example.com` / `admin123`
- Verify your email using simulate button after registration
- Check exact email and password

### Admin Features Not Showing

**Issue:** Can't see Employees, Departments, Accounts links

**Solution:**
- Login as admin account
- Check that your role is set to "admin"
- Use admin account to manage other users

### Employee Creation Fails

**Issue:** "User email does not exist" error

**Solution:**
- Create the user account first in Accounts page
- Use the exact email from the Accounts table

### Clear All Data

**Steps:**
```
1. Press F12 to open DevTools
2. Go to Application tab
3. Find Local Storage
4. Delete 'ipt_demo_v1' key
5. Refresh page
6. App reinitializes with seeded data
```

---

## 📋 Completed Features Checklist

✅ HTML5 structure with Bootstrap 5
✅ Registration with email and password
✅ Email verification (simulated)
✅ Login/Logout with role-based access
✅ Profile view and edit
✅ Request creation with dynamic items
✅ Request editing and deletion
✅ Request status tracking
✅ Account management (Create, Read, Update, Delete)
✅ Department management (Create, Read, Update, Delete)
✅ Employee management (Create, Read, Update, Delete)
✅ localStorage data persistence
✅ Toast notifications
✅ Form validation
✅ Responsive design
✅ Admin-only access control

---

## 🎓 Learning Outcomes

This project demonstrates:
- Client-side form handling and validation
- localStorage for data persistence
- Page routing without backend
- Role-based access control
- CRUD operations with JavaScript
- Modal and form management
- User session management
- Toast notifications for UX
- Responsive CSS design
- Bootstrap integration

---

## 📖 Code Quality

- **Modular Functions** - Each feature has dedicated functions
- **Data Validation** - Input validation before saving
- **Error Handling** - Toast notifications for all operations
- **Comments** - Code organized with section headers
- **Responsive** - Works on all screen sizes
- **Clean UI** - Bootstrap 5 with custom styling

---

## 🚀 Deployment

To deploy this app:

1. Upload all three files (HTML, CSS, JS) to a static hosting service
2. Options:
   - GitHub Pages
   - Netlify
   - Vercel
   - Any static host

No backend server required!

---

## 📞 Notes

- **Storage:** All data stored in localStorage (not for production)
- **Security:** For demonstration only (plaintext passwords)
- **Backend:** This is frontend-only prototype
- **Real Use:** Would need backend API and proper security

---

## ✅ Status


**Status:** Complete and fully functional  
**Last Updated:** February 2026  
**Testing:** All features tested and working

---

## 📝 Summary

This Full-Stack App prototype demonstrates a complete web application with:
- User authentication and authorization
- Multi-page interface
- CRUD operations
- Data persistence
- Admin controls



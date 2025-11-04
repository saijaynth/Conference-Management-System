# Conference Management System - Running Guide

## 🚀 Quick Start Guide

This guide will help you run the Conference Management System locally on your machine.

## 📋 Prerequisites

Before running the application, ensure you have the following installed:

- **PHP 7.4 or higher** (Tested with PHP 8.3.6)
- **Web Server** (Apache, Nginx, or PHP's built-in development server)
- **Modern Web Browser** (Chrome, Firefox, Safari, or Edge)

## 🔧 Installation Steps

### 1. Clone the Repository

```bash
git clone https://github.com/saijaynth/Conference-Management-System.git
cd Conference-Management-System
```

### 2. Navigate to the Application Directory

```bash
cd public_html
```

### 3. Start the PHP Development Server

```bash
php -S localhost:8000
```

The application will be available at: **http://localhost:8000**

## 🌐 Accessing the Application

Open your web browser and navigate to:
- **Homepage**: http://localhost:8000/index.php
- **Login/Signup**: http://localhost:8000/colorlib-regform-7/login.php

## 👥 Demo Accounts

The system comes with pre-configured demo accounts for testing different user roles:

### Organizer Account
- **Email**: `organizer@hotmail.com`
- **Password**: `sinop5757`
- **Features**: Full admin access, user management, conference setup, maintenance mode control

### Author Account
- **Email**: `author@hotmail.com`
- **Password**: `sinop5757`
- **Features**: Submit papers, view submission status, edit submissions

### Reviewer Account
- **Email**: `reviewer@hotmail.com`
- **Password**: `sinop5757`
- **Features**: Review submitted papers, provide feedback and scores

### Participant Account
- **Email**: `participant@hotmail.com`
- **Password**: `sinop5757`
- **Features**: View conference schedule, register for sessions, provide feedback

### Additional Organizer Account
- **Email**: `gorkemturkut@hotmail.com`
- **Password**: `sinop5757`
- **Features**: Full admin access

## 🎯 Key Features & Pages

### For All Users
- **Homepage**: View conference information, services, live sessions, and testimonials
- **Registration**: Create a new account with different role types
- **Login**: Access your account based on your role

### For Organizers
- **Conference Setup**: Configure conference title, description, venue, dates, and capacity
- **User Management**: Add, update, or delete users and manage their roles
- **Maintenance Mode**: Enable/disable system maintenance with custom messages
- **Admin Panel**: Monitor system status, view logs, and generate reports
- **Session Management**: Create and manage live sessions

### For Authors
- **Paper Submission**: Upload abstracts and presentations
- **Submission Status**: Track review progress and feedback
- **Profile Management**: Update personal information

### For Reviewers
- **Review Dashboard**: Access assigned papers for review
- **Evaluation System**: Provide scores and detailed feedback
- **Review History**: Track completed reviews

### For Participants
- **Conference Schedule**: View all available sessions
- **Session Registration**: Register for specific sessions
- **Feedback System**: Provide feedback on attended sessions

## 🗂️ Project Structure

```
Conference-Management-System/
├── public_html/              # Main application directory
│   ├── assets/              # CSS, JS, images, and vendors
│   ├── colorlib-regform-7/  # Login and registration system
│   ├── uploads/             # User uploaded files
│   ├── index.php            # Homepage
│   ├── organizator.php      # Organizer dashboard
│   ├── author.php           # Author dashboard
│   ├── reviewer.php         # Reviewer dashboard
│   ├── user.php             # Participant dashboard
│   ├── maintenance_admin.php # Admin maintenance panel
│   └── user_management.php  # User management interface
├── Screenshots/             # Application screenshots
├── README.md               # Project documentation
└── package.json           # Frontend build dependencies (optional)
```

## 🔒 Authentication System

The application uses a **JSON-based authentication system**:
- User credentials are stored in `public_html/colorlib-regform-7/users.json`
- Sessions are managed using PHP sessions
- Role-based access control (RBAC) for different user types

## 📱 User Interface

The application features:
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Bootstrap 4.x Framework**: Modern and clean UI
- **Role-based Dashboards**: Each user type has a customized interface
- **Intuitive Navigation**: Easy-to-use menu system

## 🛠️ Troubleshooting

### Issue: PHP Not Found
**Solution**: Install PHP or add it to your system PATH
```bash
# For Ubuntu/Debian
sudo apt-get install php

# For macOS (using Homebrew)
brew install php

# For Windows
Download from https://windows.php.net/download/
```

### Issue: Port 8000 Already in Use
**Solution**: Use a different port
```bash
php -S localhost:8080
```

### Issue: File Upload Errors
**Solution**: Ensure the `uploads/` directory has write permissions
```bash
chmod 755 public_html/uploads/
```

### Issue: Session Not Persisting
**Solution**: Check PHP session configuration and ensure session save path is writable

## 📸 Application Screenshots

### Homepage
![Homepage](https://github.com/user-attachments/assets/faa4f234-31e4-4aaf-9a3f-adc530a0dc1c)

### Login & Registration
![Login Page](https://github.com/user-attachments/assets/5155d3c6-a725-4c16-9259-d921c05fa199)

### Organizer Dashboard
![Organizer Dashboard](https://github.com/user-attachments/assets/a0a4a026-3452-4ed0-bf47-db7cf3ce8f3a)

### Admin Panel
![Admin Panel](https://github.com/user-attachments/assets/c2448685-538c-4c58-9ff4-858f1bed47cd)

### User Management
![User Management](https://github.com/user-attachments/assets/81afe1a5-81c1-4803-a41a-0d48db78415e)

## 🔄 System Requirements

- **Minimum PHP Version**: 7.4
- **Recommended PHP Version**: 8.0 or higher
- **Required PHP Extensions**: 
  - json
  - session
  - fileinfo (for file uploads)
- **Browser Support**: All modern browsers (Chrome, Firefox, Safari, Edge)
- **Screen Resolution**: 1024x768 or higher recommended

## 🎓 Getting Started Tutorial

1. **Start the Server**: Run `php -S localhost:8000` in the `public_html` directory
2. **Access Homepage**: Open http://localhost:8000 in your browser
3. **Login**: Click "Login" in the navigation menu
4. **Choose Role**: Login with one of the demo accounts based on your desired role
5. **Explore Features**: Each dashboard provides role-specific functionality

## 📞 Support

For issues, questions, or contributions:
- **GitHub Issues**: Report bugs or request features
- **Project Lead**: Görkem Turkut (gorkemturkut@hotmail.com)
- **GitHub Profile**: https://github.com/gorkemturkut57

## 📝 Notes

- This is a development/demo version using JSON file storage
- For production use, consider implementing a proper database (MySQL/PostgreSQL)
- Passwords in demo accounts are for testing purposes only
- The maintenance mode feature allows organizers to temporarily disable access for system updates

## 🎉 Enjoy Using the Conference Management System!

The system is now running and ready to use. Explore the different dashboards and features by logging in with different user roles.

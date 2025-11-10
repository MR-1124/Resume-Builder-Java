# 📋 Resume Builder

A professional, full-featured web application for creating, managing, and exporting resumes with a modern Material Design interface.

![Java](https://img.shields.io/badge/Java-11+-orange.svg)
![MongoDB](https://img.shields.io/badge/MongoDB-4.11+-green.svg)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

## Overview

Resume Builder is a comprehensive web application that empowers users to create professional resumes with minimal effort. Built with Java Servlets, JSP, and MongoDB, it features a beautiful Material Design interface with dark theme support, multiple export formats, and complete user management.

### Key Features

- 🔐 **Secure Authentication** - BCrypt password hashing with session management
- 📝 **Resume Management** - Create, edit, preview, and delete resumes
- 🎨 **Material Design UI** - Modern interface with smooth animations and dark theme
- 📄 **Multiple Templates** - Classic and Modern resume templates
- 💾 **Export Options** - Download resumes as PDF or XML
- 👤 **Profile Management** - Update personal information and change passwords
- 📱 **Responsive Design** - Works seamlessly on desktop, tablet, and mobile
- 🌙 **Dark Theme** - Eye-friendly dark mode with persistent preference

## Quick Start

### Prerequisites

- **Java Development Kit (JDK) 11+**
- **Apache Maven 3.6+**
- **MongoDB 4.0+**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/MR-1124/resume-builder.git
   cd resume-builder
   ```

2. **Start MongoDB**
   ```bash
   # Windows
   net start MongoDB
   
   # Or use the provided script
   start-mongodb.bat
   
   # Linux/Mac
   sudo systemctl start mongod
   ```

3. **Build and run the application**
   ```bash
   # Using Maven
   mvn clean tomcat7:run

   ```

4. **Access the application**
   ```
   http://localhost:8080/resume-builder
   ```

## 📖 Usage Guide

### Creating Your First Resume

1. **Sign Up** - Create a new account with your email and password
2. **Login** - Access your dashboard
3. **Create Resume** - Click "Create New Resume" and fill in your information:
   - Personal details (name, email, phone, etc.)
   - Education history
   - Work experience
   - Projects
   - Skills
   - Achievements
4. **Choose Template** - Select Classic or Modern template as per your preference
5. **Save** - Your resume is automatically saved to the database

### Managing Resumes

- **Preview** - View your resume before downloading
- **Edit** - Update any part of your resume
- **Download PDF** - Get a print-ready PDF doc
- **Download XML** - Export structured data for backup
- **Delete** - Remove unwanted resumes

### Profile Management

- Update your personal information
- Change your password securely
- View account statistics

## Architecture

### Technology Stack

**Backend:**
- Java 11+
- Servlets 4.0
- JSP 2.3 with JSTL
- Maven (Build Tool)

**Database:**
- MongoDB
- MongoDB Java Driver

**Frontend:**
- HTML5, CSS3, JavaScript ES6
- Material Design Components
- Google Fonts (Roboto)
- Material Icons

**Libraries:**
- iText 5.5.13.3 (PDF Generation)
- BCrypt 0.4 (Password Hashing)
- Gson 2.10.1 (JSON Processing)

### Project Structure

```
resume-builder/
├── src/main/
│   ├── java/com/resumebuilder/
│   │   ├── model/          # Data models (User, Resume, etc.)
│   │   ├── dao/            # Database access objects
│   │   ├── servlet/        # HTTP request handlers
│   │   └── util/           # Utility classes (MongoDB, PDF, XML)
│   └── webapp/
│       ├── WEB-INF/
│       │   ├── views/      # JSP pages
│       │   ├── includes/   # Reusable components
│       │   └── web.xml     # Servlet configuration
│       ├── css/            # Stylesheets
│       └── js/             # JavaScript files
├── pom.xml                 # Maven configuration
└── README.md              # This file
```

## 🎨 Features in Detail

### Authentication & Security

- **BCrypt Password Hashing** 
- **Session Management** - Secure session handling with 30-minute timeout
- **Input Validation** - Server-side validation for all user inputs
- **Access Control** - Protected routes requiring authentication

### Resume Templates Provided

#### Classic Template Design
- Traditional professional design
- Times New Roman font
- Black and white color scheme
- ATS-friendly formatting

#### Modern Template Design
- Contemporary design
- Helvetica font
- Colored section headers
- Clean, minimalist layout

### Export Formats

#### PDF Export Feature
- Print-ready documents
- Professional classic resume design formatting
- Embedded fonts
- Proper page breaks

#### XML Export Feature
- Structured data format
- Backup and portability
- Integration-friendly

### Inspired by Material Design UI

- **Elevation System** - 5-level shadow hierarchy
- **Color Palette** - Purple-blue gradient theme
- **Typography** - Roboto font family
- **Animations** - Smooth transitions
- **Responsive Grid** - Flexible layouts for all devices

### Dark Theme

- **Eye-friendly** - Reduced eye strain in low-light conditions
- **Persistent** - Theme preference saved in localStorage
- **Smooth Transitions** - Smooth theme switching
- **Consistent** - All pages support dark mode

## 🔧 Configuration

### Database Configuration

Edit `src/main/java/com/resumebuilder/util/MongoDBUtil.java`:

```java
private static final String CONNECTION_STRING = "mongodb://localhost:27017";
private static final String DATABASE_NAME = "resume-builder";
```

### Server Configuration

Edit `pom.xml` to change server settings:

```xml
<configuration>
    <port>8080</port>
    <path>/resume-builder</path>
</configuration>
```

## 📊 Database Schema

### Users Collection

```json
{
  "_id": ObjectId,
  "email": "user@example.com",
  "password": "$2a$10$...",
  "fullName": "John Doe"
}
```

### Resumes Collection

```json
{
  "_id": ObjectId,
  "userId": "user_id",
  "title": "Software Engineer Resume",
  "template": "modern",
  "createdAt": ISODate,
  "updatedAt": ISODate,
  "personalInfo": {
    "fullName": "John Doe",
    "email": "john@example.com",
    "phone": "+1234567890",
    "address": "City, Country",
    "linkedin": "linkedin.com/in/johndoe",
    "github": "github.com/johndoe",
    "summary": "Professional summary..."
  },
  "education": [...],
  "experience": [...],
  "projects": [...],
  "skills": [...],
  "achievements": [...]
}
```

## 🛠️ Development

### Building the Project

```bash
# Clean and compile
mvn clean compile

# Run tests (if available)
mvn test

# Package as WAR
mvn package

# Run development server
mvn tomcat7:run
```

### Project Scripts provided

- `start-mongodb.bat` - Start MongoDB service

## API Endpoints Details

### Authentication
- `GET /login` - Login page
- `POST /login` - Authenticate user
- `GET /signup` - Signup page
- `POST /signup` - Register user
- `GET /logout` - Logout user

### Dashboard & Profile
- `GET /dashboard` - User dashboard
- `GET /profile` - User profile
- `POST /profile` - Update profile/password

### Resume Management
- `GET /resume/` - Create resume form
- `POST /resume/` - Save new resume
- `GET /resume/edit/{id}` - Edit resume form
- `POST /resume/update/{id}` - Update resume
- `POST /resume/delete/{id}` - Delete resume
- `GET /resume/preview/{id}` - Preview resume

### Export
- `GET /download/pdf/{id}` - Download PDF
- `GET /download/xml/{id}` - Download XML

### Information Pages
- `GET /help` - Help center
- `GET /tips` - Resume tips
- `GET /tutorials` - Tutorials
- `GET /contact` - Contact form
- `GET /privacy` - Privacy policy
- `GET /terms` - Terms of service
- `GET /cookies` - Cookie policy

## 🚀 Deployment

### Deployment

```bash
mvn tomcat7:run
```

### Deploy and run

1. **Build WAR file**
   ```bash
   mvn clean package
   ```

2. **Deploy to Tomcat**
   ```bash
   cp target/resume-builder.war $TOMCAT_HOME/webapps/
   ```

3. **Configure MongoDB**
   - Enable authentication
   - Set up proper user permissions
   - Configure firewall rules

4. **Enable HTTPS**
   - Configure SSL certificate
   - Update Tomcat server.xml
   - Redirect HTTP to HTTPS

## 📄 License

This project is licensed under the MIT License

## 👥 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

**Made as a Semester Project for Java**

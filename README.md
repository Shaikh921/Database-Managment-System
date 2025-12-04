# Library Management System

A comprehensive web-based library management system built with PHP and MySQL. This system provides separate interfaces for administrators and library members with complete book management, user management, and transaction tracking capabilities.

## Features

### Admin Panel
- **Dashboard**: Overview of library statistics and recent activities
- **Book Management**: Add, edit, and manage books with categories and authors
- **Author Management**: Add and manage book authors
- **Category Management**: Organize books by categories
- **Member Management**: Register and manage library members
- **Issue/Return Books**: Handle book lending and returns
- **Reports**: Generate various library reports

### User Interface
- **Browse Books**: Search and filter available books
- **Book Details**: View detailed information about books
- **My Issues**: Track borrowed books and due dates
- **User Dashboard**: Personal library account overview

### Technical Features
- **Secure Authentication**: Password hashing and session management
- **Input Validation**: Comprehensive form validation (client and server-side)
- **Responsive Design**: Bootstrap-based responsive UI
- **Database Security**: Prepared statements and SQL injection prevention
- **Foreign Key Constraints**: Data integrity with proper relationships

## Technology Stack

- **Backend**: PHP 7.4+
- **Database**: MySQL 5.7+
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap 5.3
- **Server**: Apache/Nginx with mod_rewrite

## Installation

### Prerequisites
- PHP 7.4 or higher
- MySQL 5.7 or higher
- Apache/Nginx web server
- mod_rewrite enabled

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/library-management-system.git
   cd library-management-system
   ```

2. **Database Setup**
   - Create a MySQL database named `library_db`
   - Import the database schema:
   ```bash
   mysql -u your_username -p library_db < sql/library_db.sql
   ```

3. **Configuration**
   - Update database credentials in `includes/config.php`:
   ```php
   $host = 'localhost';
   $username = '';
   $password = '';
   $database = 'library_db';
   ```

4. **Web Server Setup**
   - Point your web server document root to the project directory
   - Ensure `.htaccess` file is in place for URL rewriting
   - Set appropriate file permissions

5. **Access the Application**
   - Navigate to your domain/server in a web browser
   - Default admin credentials will be created during database import

## Usage

### Admin Access
1. Go to the login page
2. Select "Admin Login"
3. Use the admin credentials created during setup
4. Access the admin dashboard to manage the library

### Member Registration
1. Go to the login page
2. Click "Register as New Member"
3. Fill out the registration form with validation
4. Login with your registered email and password

### Book Management
- Admins can add books with authors and categories
- Books have quantity tracking for availability
- Issue and return processes update availability automatically

## Database Schema

### Main Tables
- `admins` - Administrator accounts
- `members` - Library member accounts  
- `authors` - Book authors
- `book_categories` - Book categories
- `books` - Book catalog with foreign keys to authors and categories
- `issue_books` - Book lending transactions
- `reservations` - Book reservation system
- `activity_log` - System activity tracking

### Key Relationships
- Books reference authors and categories (foreign keys)
- Issue transactions reference books and members
- Proper constraints prevent deletion of referenced records

## Security Features

- Password hashing using PHP's `password_hash()`
- SQL injection prevention with prepared statements
- Input sanitization and validation
- Session-based authentication
- CSRF protection considerations
- Secure password requirements (8+ chars, mixed case, numbers)

## File Structure

```
library-management-system/
├── admin/                  # Admin panel files
│   ├── dashboard.php      # Admin dashboard
│   ├── books_add.php      # Add books
│   ├── authors_add.php    # Add authors
│   ├── categories_add.php # Add categories
│   ├── members_add.php    # Add members
│   ├── issue_book.php     # Issue books
│   ├── return_book.php    # Return books
│   ├── manage_books.php   # Manage books
│   ├── reports.php        # Generate reports
│   ├── login.php          # Admin login (redirects to unified)
│   └── logout.php         # Admin logout
├── user/                  # User interface files
│   ├── dashboard.php      # User dashboard
│   ├── browse.php         # Browse books
│   ├── book_detail.php    # Book details
│   ├── my_issues.php      # User's borrowed books
│   ├── reserve_book.php   # Book reservation
│   └── logout.php         # User logout
├── public/                # Public access files
│   ├── index.php          # Homepage
│   ├── login.php          # Unified login system
│   ├── register.php       # Member registration
│   └── assets/            # CSS, JS, images
├── includes/              # Shared PHP files
│   ├── config.php         # Database configuration
│   ├── auth.php           # Authentication functions
│   ├── helpers.php        # Utility functions
│   ├── header.php         # Common header
│   └── footer.php         # Common footer
├── sql/                   # Database files
│   └── library_db.sql     # Complete database schema with sample data
├── .htaccess              # URL rewriting rules
└── README.md              # This file
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

For support, please open an issue on GitHub or contact the development team.

---

**Note**: This system is designed for educational and small-scale library management purposes. For production use, consider additional security measures and scalability optimizations.
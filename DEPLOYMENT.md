# Conference Management System - Deployment Guide

## Overview
This guide will help you deploy the Conference Management System on your server or local environment.

## System Requirements

### Server Requirements
- **PHP**: 8.0 or higher
- **Web Server**: Apache, Nginx, or PHP built-in server
- **Node.js**: 16.x or higher (for building assets)
- **npm**: 8.x or higher

### PHP Extensions Required
- `json` - For handling user data
- `session` - For session management
- `fileinfo` - For file uploads

## Installation Steps

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Conference-Management-System
```

### 2. Install Dependencies
```bash
npm install
```

**Note**: The project has been updated to use modern `sass` instead of deprecated `node-sass` for compatibility with Node.js v20+.

### 3. Build Assets (Optional)
If you want to rebuild the CSS and JS assets:

```bash
# Compile SCSS to CSS
npm run start
# or manually run gulp
npx gulp sass

# For production build (minified assets)
npx gulp build
```

### 4. Configure File Permissions
Ensure the following directories are writable by the web server:

```bash
chmod 755 public_html/uploads
chmod 644 public_html/colorlib-regform-7/users.json
chmod 644 public_html/maintenance_status.txt
chmod 644 public_html/logs.txt
```

### 5. Deploy to Web Server

#### Option A: PHP Built-in Server (Development)
```bash
cd public_html
php -S localhost:8000
```

Then access: `http://localhost:8000`

#### Option B: Apache
1. Copy the `public_html` directory to your web server document root
2. Configure your virtual host to point to the `public_html` directory
3. Ensure `.htaccess` is enabled (if using Apache)

Example Apache configuration:
```apache
<VirtualHost *:80>
    ServerName conference.yourdomain.com
    DocumentRoot /path/to/Conference-Management-System/public_html
    
    <Directory /path/to/Conference-Management-System/public_html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

#### Option C: Nginx
Example Nginx configuration:
```nginx
server {
    listen 80;
    server_name conference.yourdomain.com;
    root /path/to/Conference-Management-System/public_html;
    index index.php index.html;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.3-fpm.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        include fastcgi_params;
    }
}
```

## Default User Accounts

The system comes with pre-configured test accounts:

| Role | Email | Password |
|------|-------|----------|
| Organizer | organizer@hotmail.com | sinop5757 |
| Author | author@hotmail.com | sinop5757 |
| Reviewer | reviewer@hotmail.com | sinop5757 |
| Participant | participant@hotmail.com | sinop5757 |

**⚠️ IMPORTANT**: Change these passwords in production!

## Post-Deployment Configuration

### 1. Update User Credentials
Edit `public_html/colorlib-regform-7/users.json` and update the passwords to secure values.

### 2. Configure Timezone
The system is configured for Istanbul timezone by default. To change it, edit `public_html/maintenance_config.php`:

```php
date_default_timezone_set('America/New_York'); // Change as needed
```

### 3. Security Recommendations
1. **Change default passwords** immediately
2. **Set proper file permissions** to prevent unauthorized access
3. **Use HTTPS** in production
4. **Backup** the `users.json` file regularly
5. **Monitor logs** in `public_html/logs.txt`

### 4. Admin Panel Access
- URL: `http://yourdomain.com/maintenance_admin.php`
- Only organizers can access the admin panel
- Features include:
  - Enable/Disable maintenance mode
  - User management (CRUD operations)
  - System monitoring
  - View logs

## Features

### User Roles & Capabilities

#### Organizer
- Full admin access
- Conference setup and management
- User management (add, edit, delete users)
- Enable/disable maintenance mode
- Access system logs and reports

#### Author
- Submit abstracts and presentations
- View submission status
- Edit/withdraw submissions (before review)
- View feedback from reviewers

#### Reviewer
- View assigned submissions
- Download abstracts/presentations
- Submit reviews and scores
- Track review history

#### Participant
- View conference schedule
- Register for sessions
- Download conference materials
- Provide session feedback

## Troubleshooting

### Issue: npm install fails with node-sass error
**Solution**: The project has been updated to use modern `sass`. Delete `node_modules` and `package-lock.json`, then run `npm install` again.

### Issue: CSS files not loading
**Solution**: Run `npx gulp sass` to compile SCSS files to CSS.

### Issue: File upload fails
**Solution**: Check that the `uploads` directory exists and has proper write permissions (755).

### Issue: Session errors
**Solution**: Ensure PHP session save path is writable and `session_start()` is not called multiple times.

### Issue: Maintenance mode stuck
**Solution**: Manually delete `public_html/maintenance_status.txt` and `public_html/maintenance_info.json` files.

## Development

### Running in Development Mode
```bash
# Start PHP server
cd public_html
php -S localhost:8000

# In another terminal, watch for SCSS changes
npx gulp watch
```

This will:
- Start a local PHP server on port 8000
- Launch BrowserSync for live reload
- Watch for SCSS file changes and recompile

### Building for Production
```bash
# Build all assets (minified CSS, JS, optimized images)
npx gulp build
```

## Maintenance Mode

The system includes a maintenance mode feature:

1. **Enable**: Login as organizer → Management → Start Maintenance Mode
2. **Disable**: Login as organizer → Management → End Maintenance Mode

When enabled:
- Regular users see a maintenance page
- Organizers can still access the system
- Useful for system updates or database maintenance

## File Structure

```
Conference-Management-System/
├── public_html/              # Web root directory
│   ├── assets/              # CSS, JS, images
│   ├── colorlib-regform-7/  # Login/signup system
│   │   └── users.json       # User database
│   ├── uploads/             # File uploads directory
│   ├── index.php            # Homepage
│   ├── author.php           # Author dashboard
│   ├── reviewer.php         # Reviewer dashboard
│   ├── organizator.php      # Organizer dashboard
│   ├── user.php             # Participant dashboard
│   ├── maintenance_admin.php # Admin panel
│   ├── user_management.php  # User CRUD interface
│   └── maintenance.php      # Maintenance mode page
├── package.json             # npm dependencies
├── gulpfile.js             # Gulp build configuration
└── README.md               # Project documentation
```

## Support

For issues or questions:
- Check the `logs.txt` file in `public_html/`
- Review PHP error logs
- Ensure all file permissions are correctly set

## License

[Include your license information here]

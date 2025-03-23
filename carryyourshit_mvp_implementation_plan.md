# CarryYourShit E-commerce MVP Implementation Plan

## 1. Project Overview

CarryYourShit is a luggage and travel accessories e-commerce store built on the Bagisto platform. Bagisto is an open-source Laravel-based e-commerce platform that allows for the quick development of online stores. This document outlines the implementation plan for setting up a Minimum Viable Product (MVP) for the CarryYourShit brand using Bagisto as the underlying technology.

### Core Requirements
- PHP >=7.1 (Installed PHP 8.4.5 ✓)
- Composer (Installed Composer 2.8.6 ✓)
- MySQL/MariaDB database (Installed MySQL 9.2.0 ✓)
- Local development environment (Using built-in PHP server ✓)
- Basic e-commerce functionalities including product catalog, user authentication, and payment processing

## 2. Environment Setup

### 2.1 Prerequisites Installation
- [x] Install PHP >=7.1
  - Check version: `php -v` ✓
  - Ensure required PHP extensions are enabled: BCMath, Ctype, Fileinfo, JSON, Mbstring, OpenSSL, PDO, Tokenizer, XML, cURL, GD
  - Note: Installed PHP 8.4.5 via Homebrew which includes the required extensions

- [x] Install Composer
  - Install via Homebrew: `brew install composer` ✓
  - Verify installation: `composer -V` ✓

- [x] Set up MySQL/MariaDB
  - Install MySQL via Homebrew: `brew install mysql` ✓
  - Start MySQL service: `brew services start mysql` ✓
  - Create a database for Bagisto: `mysql -u root -e "CREATE DATABASE CYS;"` ✓

### 2.2 Local Development Environment
- [x] Using PHP's built-in development server
  - Simpler approach for local development
  - Started with `php artisan serve` ✓

## 3. Bagisto Installation Process

### 3.1 Clone Repository
- [x] Clone the Bagisto repository:
  ```bash
  git clone https://github.com/bagisto/bagisto.git
  cd bagisto
  ```

### 3.2 Install Dependencies
- [x] Install PHP dependencies:
  ```bash
  composer install
  ```

### 3.3 Configure Environment
- [x] Create environment configuration file:
  ```bash
  cp .env.example .env
  ```

- [x] Update the following variables in the `.env` file:
  ```
  APP_NAME=CarryYourShit
  APP_URL=http://localhost
  DB_CONNECTION=mysql
  DB_HOST=127.0.0.1
  DB_PORT=3306
  DB_DATABASE=CYS
  DB_USERNAME=root
  DB_PASSWORD=
  ```

### 3.4 Complete Installation
- [x] Generate application key:
  ```bash
  php artisan key:generate
  ```

- [x] Run CarryYourShit installation (using the Bagisto installer):
  ```bash
  php artisan bagisto:install
  ```
  - Followed interactive prompts to:
    - Attempted to set up custom admin credentials (though default were kept: Email: admin@example.com, Password: admin123)
    - Choose installation type (with sample data)
    - Configure store settings

- [x] Start development server:
  ```bash
  php artisan serve
  ```
  - Note: Server might run on a different port (e.g., port 8001) if port 8000 is already in use

## 4. Core Features Configuration

### 4.1 Admin Panel Access
- [x] Access the admin panel at `http://localhost:8000/admin`
  - Note: Admin panel might run on a different port (e.g., `http://localhost:8001/admin`) if port 8000 is already in use
- [x] Login with the admin credentials:
  - Email: admin@example.com
  - Password: admin123
  - Note: Default credentials were kept during installation despite entering custom information

### 4.2 Multi-Language & Multi-Currency Setup
- [x] Verify default languages (English) and currencies (INR) are enabled
  - Database confirms English locale is configured
  - Database confirms Indian Rupee (INR) is configured
- [ ] Add additional languages (if needed):
  - Go to Admin Panel → Configuration → General → Locale Options
  - Add and configure new locales
- [ ] Add additional currencies (if needed):
  - Go to Admin Panel → Configuration → General → Currencies
  - Add and configure new currencies
  - Set exchange rates

### 4.3 User Authentication & Profiles
- [ ] Test user registration flow
- [ ] Test user login flow
- [ ] Configure user profile fields if needed:
  - Admin Panel → Configuration → Customers → Customer Settings
- [ ] Configure email templates for registration and password reset:
  - Admin Panel → Configuration → Emails → Email Settings

### 4.4 Product Catalog Setup
- [x] Create product categories:
  - Admin Panel → Catalog → Categories
  - Define category hierarchy (parent/child relationships)
  - Created categories for luggage and travel accessories

- [ ] Add product attributes:
  - Admin Panel → Catalog → Attributes
  - Create attributes for size, color, material, etc.
  - Create attribute families to group related attributes

- [ ] Add products:
  - Admin Panel → Catalog → Products → Add Product
  - Configure product types (simple, configurable, virtual, etc.)
  - Add product details (name, description, price, images)
  - Assign categories and attributes
  - Set inventory levels

- [ ] Configure search settings:
  - Admin Panel → Configuration → Catalog → Inventory

### 4.5 Payment Integration
- [x] Configure Razorpay as the primary payment method:
  - Admin Panel → Configuration → Sales → Payment Methods
  - Razorpay supports UPI payments, credit/debit cards, and other Indian payment methods
  
- [x] Install Razorpay extension:
  ```bash
  composer require wontonee/razorpay
  ```
  
- [x] Update service provider:
  - Added `Wontonee\Razorpay\Providers\RazorpayServiceProvider::class` to `config/app.php`
  
- [x] Update CSRF exception for Razorpay:
  - Added Razorpay route `/razorpaycheck` to CSRF token exception list in `app/Http/Middleware/VerifyCsrfToken.php`
  
- [ ] Configure Razorpay credentials in admin panel:
  - Register for Razorpay account at razorpay.com
  - Obtain API key ID and Secret
  - Configure in Bagisto admin panel: Configuration → Sales → Payment Methods → Razorpay
  - Set up webhook for payment notifications
  
- [ ] Test payment flow in test mode:
  - Test UPI payment
  - Test credit card payment
  - Verify webhook functionality

### 4.6 Shipping Methods
- [ ] Configure shipping methods:
  - Admin Panel → Configuration → Sales → Shipping Methods
  - Configure flat rate shipping for different regions in India
    - Set appropriate rates for Metro cities, Tier 2 cities, and other regions
    - Configure weight-based pricing for heavier luggage items
  - Enable free shipping for orders above a certain value (e.g., ₹5000)
  - Set up shipping method display order
  - Configure appropriate shipping descriptions for customer clarity

## 5. Frontend Customization & API Integration

### 5.1 Theme Customization (if needed)
- [ ] Explore default themes in `public/themes`
- [ ] Make necessary adjustments to:
  - Layout (`resources/themes/default/views/layouts`)
  - CSS styles (`public/themes/default/assets/css`)
  - JavaScript (`public/themes/default/assets/js`)

### 5.2 API Integration
- [ ] Review Bagisto API documentation
- [ ] Register API client:
  - Admin Panel → Configuration → General → API
  - Create API credentials

- [ ] Test API endpoints for:
  - Products listing
  - Category listing
  - Customer registration
  - Cart operations
  - Checkout process

### 5.3 Custom Frontend Development (Optional)
- [ ] Set up a headless frontend if desired:
  - Choose framework (React, Vue, Angular)
  - Create project structure
  - Implement API calls to Bagisto
  - Develop UI components for:
    - Product listing
    - Product details
    - Shopping cart
    - Checkout
    - User account

## 6. Testing Strategy

### 6.1 Functionality Testing
- [ ] Test user registration and login
- [ ] Test product browsing and search
- [ ] Test adding items to cart
- [ ] Test checkout process with different payment methods
- [ ] Test order management and tracking

### 6.2 Performance Testing
- [ ] Test page load times
- [ ] Test concurrent user sessions
- [ ] Test database query performance

### 6.3 Security Testing
- [ ] Verify secure checkout process
- [ ] Test authentication and authorization
- [ ] Check for common vulnerabilities (XSS, CSRF, SQL injection)

### 6.4 Mobile Responsiveness
- [ ] Test on multiple device sizes
- [ ] Verify usability on mobile devices

## 7. Deployment Steps

### 7.1 Prepare Production Environment
- [ ] Set up production server with required specifications:
  - PHP >=7.1
  - MySQL/MariaDB
  - Nginx or Apache web server
  - SSL certificate

### 7.2 Deploy Codebase
- [ ] Clone or upload Bagisto code to production server
- [ ] Set proper file permissions
- [ ] Configure production environment variables
- [ ] Install dependencies with `composer install --no-dev`

### 7.3 Database Migration
- [ ] Export and import database or run migrations:
  ```bash
  php artisan migrate
  ```

### 7.4 Optimize for Production
- [ ] Compile assets:
  ```bash
  npm run production
  ```
- [ ] Cache configuration:
  ```bash
  php artisan config:cache
  php artisan route:cache
  php artisan view:cache
  ```

### 7.5 Final Checks
- [ ] Test the production site thoroughly
- [ ] Configure monitoring and alerts
- [ ] Set up regular backups

## 8. Maintenance & Future Enhancements

### 8.1 Regular Maintenance
- [ ] Update Bagisto core when new versions are released
- [ ] Monitor server performance
- [ ] Regular security updates

### 8.2 Potential Enhancements Post-MVP
- [ ] Advanced analytics integration
- [ ] Marketing tools (email campaigns, promotions)
- [ ] Customer loyalty program
- [ ] Advanced shipping options
- [ ] Integration with ERP or accounting systems
- [ ] Mobile app development

## 9. Resources & Documentation
- [Bagisto Official Documentation](https://devdocs.bagisto.com/)
- [Bagisto GitHub Repository](https://github.com/bagisto/bagisto)
- [Bagisto Community Forum](https://forums.bagisto.com/)
- [Laravel Documentation](https://laravel.com/docs)

## 10. Troubleshooting Notes

### 10.1 Common Issues and Solutions
- Database connection issues: 
  - Ensure MySQL service is running (`brew services list`)
  - Verify database credentials in `.env` file
  - Make sure the specified database exists (`mysql -u root -e "SHOW DATABASES;"`)

- PHP version or extension issues:
  - Check PHP version with `php -v`
  - Check installed extensions with `php -m`

### 10.2 Deprecation Warnings
- OpenAI client parameter issue and Opis\Closure warnings:
  - These are deprecation notices in vendor packages 
  - Not critical for functionality but should be addressed in future updates
  - Attempted solutions:
    - Added error suppression in `.env` file with `PHP_INI_ERROR_REPORTING="E_ALL & ~E_DEPRECATED & ~E_NOTICE"`
    - Created custom `error_suppress.php` script to modify error reporting at runtime
    - Decided to proceed with development despite warnings as they don't affect functionality

## 11. Current Status and Next Steps

### 11.1 Completed Tasks
- [x] Environment setup (PHP 8.4.5, MySQL 9.2.0, Composer 2.8.6)
- [x] Bagisto platform installation and configuration
- [x] CarryYourShit database setup (CYS database)
- [x] Admin credentials configuration
- [x] Application successfully running on local development server
- [x] Updated branding to consistently use "CarryYourShit" as the store/brand name
- [x] Created comprehensive README.md with setup instructions
  - Installation steps
  - Configuration details
  - Troubleshooting guide
  - Development guidelines

### 11.2 Next Steps
- [x] Configure core e-commerce features in admin panel
- [x] Set up product catalog
- [x] Begin payment method integration
  - [x] Install Razorpay package
  - [x] Configure service provider
  - [x] Set up CSRF exceptions
  - [ ] Complete Razorpay credentials setup in admin panel
- [ ] Configure shipping methods
  - [ ] Set up flat rate shipping for different regions in India
  - [ ] Enable free shipping for orders above threshold
  - [ ] Test shipping calculations in checkout
- [ ] Test user flows and functionality
- [ ] Customize frontend as needed 
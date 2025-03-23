# CarryYourShit E-commerce Website

A comprehensive luggage and travel accessories e-commerce platform built on the Bagisto Laravel framework.

## Overview

CarryYourShit is an e-commerce store specializing in luggage and travel accessories. This project uses Bagisto, an open-source Laravel-based e-commerce platform, providing a robust foundation with features like product management, user authentication, payment processing, and more.

## Prerequisites

Make sure your system meets the following requirements:

- PHP 8.1+ (we're using PHP 8.4.5)
- Composer 2.0+ (we're using Composer 2.8.6)
- MySQL 5.7+ or MariaDB 10.2+ (we're using MySQL 9.2.0)
- Node.js and npm (for asset compilation)
- Git

## Installation

Follow these steps to set up the project locally:

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/CarryYourShit.git
cd CarryYourShit
```

### 2. Install PHP Dependencies

Navigate to the Bagisto directory and install PHP dependencies:

```bash
cd bagisto
composer install
```

### 3. Configure Environment Variables

Copy the example environment file and update it with your configuration:

```bash
cp .env.example .env
```

Update the following variables in the `.env` file:

```
APP_NAME=CarryYourShit
APP_URL=http://localhost
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=CYS
DB_USERNAME=root
DB_PASSWORD=your_password
```

### 4. Create Database

Create a MySQL database for the application:

```bash
mysql -u root -p -e "CREATE DATABASE CYS;"
```

### 5. Generate Application Key

```bash
php artisan key:generate
```

### 6. Run Bagisto Installation

```bash
php artisan bagisto:install
```

During the installation, you will be prompted to:
- Choose installation type (with or without sample data)
- Configure store settings

### 7. Start the Development Server

```bash
php artisan serve
```

The website will be available at http://localhost:8000 and the admin panel at http://localhost:8000/admin

### 8. Admin Access

Use the following credentials to log in to the admin panel:
- URL: http://localhost:8000/admin
- Email: admin@example.com
- Password: admin123

## Payment Integration

CarryYourShit uses Razorpay for payment processing, which supports UPI payments, credit/debit cards, and other Indian payment methods.

To configure Razorpay:

1. Install the Razorpay extension (already included in composer dependencies)
2. Register for a Razorpay account at [razorpay.com](https://razorpay.com)
3. Configure Razorpay in the admin panel:
   - Go to Admin Panel → Configuration → Sales → Payment Methods → Razorpay
   - Enter your API key ID and Secret
   - Set up webhook for payment notifications

## Shipping Configuration

CarryYourShit offers flexible shipping options for customers across India:

1. **Flat Rate Shipping**: 
   - Region-specific rates based on delivery location
   - Different rates for Metro cities, Tier 2 cities, and other regions
   - Weight-based pricing for heavier luggage items

2. **Free Shipping**:
   - Available for orders above ₹5000
   - Encourages larger purchases

3. **Future Integration with Shiprocket** (Phase 2):
   - Will integrate with Shiprocket for more delivery options
   - Will support Cash on Delivery (COD)
   - Real-time tracking and multiple courier options

For detailed configuration steps, refer to the [Shipping Configuration Guide](shipping-configuration-guide.md).

## Features

- **Multi-Language & Multi-Currency**: Supports multiple languages and currencies
- **Product Management**: Comprehensive product catalog with attributes and categories
- **User Authentication**: Secure login and registration system
- **Payment Processing**: Integrated with Razorpay for seamless payments including UPI
- **Order Management**: Complete order tracking and management
- **Responsive Design**: Mobile-friendly interface for all devices

## Development

### Directory Structure

The main directories you'll be working with:

- `bagisto/packages`: Core functionality modules
- `bagisto/resources`: Views, assets, and language files
- `bagisto/config`: Application configuration
- `bagisto/routes`: Application routes

### Custom Development

To customize the application:

1. Explore the default themes in `public/themes`
2. Make adjustments to layouts in `resources/themes/default/views/layouts`
3. Modify CSS styles in `public/themes/default/assets/css`
4. Update JavaScript in `public/themes/default/assets/js`

## Troubleshooting

### Common Issues

- **Database Connection Issues**:
  - Ensure MySQL service is running (`brew services list`)
  - Verify database credentials in `.env` file
  - Check that the database exists (`mysql -u root -e "SHOW DATABASES;"`)

- **PHP Version/Extension Issues**:
  - Check PHP version with `php -v`
  - Verify installed extensions with `php -m`

- **Deprecated Warnings**:
  - You may see deprecation notices in vendor packages
  - These aren't critical and don't affect functionality

- **Admin Login Issues**:
  - Default credentials are email: admin@example.com, password: admin123
  - If login fails, try clearing cache: `php artisan cache:clear`

## License

This project uses Bagisto which is licensed under the MIT License.

## Resources

- [Bagisto Documentation](https://devdocs.bagisto.com/)
- [Bagisto GitHub Repository](https://github.com/bagisto/bagisto)
- [Bagisto Community Forum](https://forums.bagisto.com/)
- [Laravel Documentation](https://laravel.com/docs) 
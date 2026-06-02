# accessory_final_cs519  

**A PHP‑based e‑commerce accessory store** – admin panel, product management, order handling and a buyer‑facing email system (PHPMailer).

---

## Overview  

`accessory_final_cs519` is a small‑scale web application that demonstrates a complete workflow for an online accessory shop:

* Admin users can log in, manage categories, products, orders and view complaints/reviews.  
* Buyers can place orders and receive email notifications through PHPMailer.  
* All data is stored in a MySQL database (see `Database/accessory_db.sql`).  

The project is intended for educational purposes (CS‑519) and can be used as a starting point for more complex e‑commerce solutions.

---

## Features  

| Admin side | Buyer side |
|------------|------------|
| Secure admin login (`admin/admin_login.php`) | Order placement (via your own front‑end) |
| Category CRUD (`admin/admin_category.php`, `admin/edit_category.php`) | Email notifications using PHPMailer |
| Product CRUD with image upload (`admin/add_product.php`, `admin/edit_product.php`, `admin/view_products.php`) | |
| Order overview & status update (`admin/order_report.php`, `admin/update_order_status.php`) | |
| View complaints & reviews (`admin/view_complaints.php`, `admin/view_reviews.php`) | |
| Logout (`admin/logout.php`) | |
| Responsive admin UI (`admin/css/style.css`) | |

---

## Tech Stack  

| Layer | Technology |
|-------|------------|
| **Backend** | PHP 7+ |
| **Database** | MySQL (SQL dump in `Database/accessory_db.sql`) |
| **Styling** | CSS (custom admin stylesheet) |
| **Email** | PHPMailer (bundled in `buyer/PHPMailer/`) |
| **Version control** | Git (GitHub) |

---

## Installation  

1. **Clone the repository**  

   ```bash
   git clone https://github.com/your-username/accessory_final_cs519.git
   cd accessory_final_cs519
   ```

2. **Create the database**  

   ```sql
   -- In MySQL client or phpMyAdmin
   SOURCE Database/accessory_db.sql;
   ```

3. **Configure the application**  

   Edit `admin/config.php` and set your own credentials:

   ```php
   // Database
   define('DB_HOST', 'localhost');
   define('DB_NAME', 'accessory_db');
   define('DB_USER', 'YOUR_DB_USERNAME');
   define('DB_PASS', 'YOUR_DB_PASSWORD');

   // PHPMailer (SMTP)
   define('SMTP_HOST', 'smtp.example.com');
   define('SMTP_PORT', 587);
   define('SMTP_USER', 'YOUR_SMTP_USERNAME');
   define('SMTP_PASS', 'YOUR_SMTP_PASSWORD');
   define('SMTP_FROM_EMAIL', 'no-reply@example.com');
   define('SMTP_FROM_NAME', 'Accessory Store');
   ```

4. **Install PHPMailer dependencies (optional)**  

   If you use Composer, run:

   ```bash
   cd buyer/PHPMailer
   composer install
   ```

   Otherwise the bundled library works out‑of‑the‑box.

5. **Set up the web server**  

   * Place the project in your web‑root (e.g., `htdocs` or `public_html`).  
   * Ensure the `admin/products_images/` folder is writable for image uploads.  

6. **Secure the admin directory** (recommended)  

   ```apache
   # .htaccess in /admin
   AuthType Basic
   AuthName "Restricted Area"
   AuthUserFile /path/to/.htpasswd
   Require valid-user
   ```

   Create the `.htpasswd` file
# Daily Expense Tracker (PHP & MySQL)

A simple PHP + MySQL web app to track daily expenses with date-, month-, and year-wise reports.

## Features
- Add, edit, and delete expenses
- Summaries and detailed reports by date, month, and year
- User authentication (register, login, change password)
- Responsive UI with Bootstrap

## Tech Stack
- PHP (mysqli)
- MySQL
- Bootstrap, jQuery (assets included in `plugins/` and `css/`)

## Project Structure (detailed)
```
.
├─ add-expense.php                  # Add a new expense entry
├─ change-password.php              # Change current user's password
├─ dashboard.php                    # User dashboard overview
├─ detsdb.sql                       # Database schema and seed data
├─ expense-*.php                    # Listing and summary pages:
│  ├─ expense-reports.php           # Overall report
│  ├─ expense-reports-detailed.php  # Detailed overall report
│  ├─ expense-datewise-reports*.php # Date-wise listing and detail
│  ├─ expense-monthwise-reports*.php# Month-wise listing and detail
│  └─ expense-yearwise-reports*.php # Year-wise listing and detail
├─ forgot-password.php              # Start password reset flow
├─ index.php                        # Login page
├─ logout.php                       # Destroy session and logout
├─ manage-expense.php               # Edit/Delete expenses
├─ register.php                     # New user registration
├─ reset-password.php               # Complete password reset flow
├─ user-profile.php                 # User profile
│
├─ includes/
│  ├─ dbconnection.php              # Local DB credentials (git-ignored)
│  ├─ dbconnection.sample.php       # Sample DB config to copy
│  ├─ header.php                    # Top navigation/header
│  ├─ sidebar.php                   # Left sidebar/menu
│  └─ footer.php                    # Footer
│
├─ assets/                          # Images and related assets
├─ css/                             # Core CSS
├─ fonts/                           # Web fonts
├─ js/                              # Core JS
├─ plugins/                         # 3rd-party libs (Bootstrap, jQuery, Flot, etc.)
└─ sass/                            # SCSS sources (optional)
```

## Prerequisites
- PHP 7.4+ (8.x recommended) with `mysqli` enabled
- MySQL 5.7/8.0
- Web server (XAMPP/WAMP) or PHP built-in server

## Quick Start (Windows)
1) Create the database
- Using XAMPP MySQL binaries:
   ```powershell
   # Create DB (enter password if prompted; press Enter for empty password)
   & "C:\xampp\mysql\bin\mysql.exe" -u root -p -e "CREATE DATABASE IF NOT EXISTS detsdb CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"

   # Import schema/data
   cmd /c ""C:\xampp\mysql\bin\mysql.exe" -u root -p detsdb < "detsdb.sql""

   # Optional: verify
   & "C:\xampp\mysql\bin\mysql.exe" -u root -p -D detsdb -e "SHOW TABLES;"
   ```
- Using MySQL in PATH:
   ```powershell
   mysql -u root -p -e "CREATE DATABASE IF NOT EXISTS detsdb CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
   cmd /c "mysql -u root -p detsdb < detsdb.sql"
   mysql -u root -p -D detsdb -e "SHOW TABLES;"
   ```

2) Configure database connection
- Copy `includes/dbconnection.sample.php` to `includes/dbconnection.php`.
- Edit the copy with your credentials (host, user, password, DB name).

3) Run the app
- XAMPP/WAMP (Apache):
   - Move or copy the project folder to your web root, e.g. `C:\xampp\htdocs\expense-tracker`.
   - Visit `http://localhost/expense-tracker`.

- PHP built-in server (for quick testing):
   ```powershell
   # From the project directory
   php -S localhost:8000
   ```
   Then open `http://localhost:8000` in your browser.

4) Sign up and log in
- Use `register.php` to create a user account, then log in via `index.php`.

### Database Connection Example
```
<?php
$con = mysqli_connect("localhost", "root", "", "detsdb");
if (mysqli_connect_errno()) {
  echo "Connection Fail" . mysqli_connect_error();
}
?>
```

## Security & Git Hygiene
- `includes/dbconnection.php` is intentionally in `.gitignore` to prevent leaking credentials.
- Commit the provided `includes/dbconnection.sample.php` only.

## Troubleshooting
- "Connection Fail": verify DB name, user/password, host, and that MySQL is running.
- Enable `mysqli` in `php.ini` if using the built-in server.
- For XAMPP, ensure Apache and MySQL services are running in the Control Panel.
- If assets don't load, confirm you're running from a web server (not opening files directly).
- On Windows, quote paths with spaces or use short paths.

## Contributing
Feel free to open issues and PRs. For larger changes, please discuss first.

## License
Add a license of your choice (MIT, Apache-2.0, etc.).

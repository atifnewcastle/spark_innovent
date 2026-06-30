# 🚀 Spark Innovent — Project Setup Guide
**Sistem Pengurusan Pertandingan Spark Innovent**  
GitHub: [https://github.com/atifnewcastle/spark_innovent](https://github.com/atifnewcastle/spark_innovent)

---

## 📋 Prerequisites

Before you begin, make sure the following software is installed on your machine:

| Software | Recommended Version | Download Link |
|---|---|---|
| **Git** | Latest | https://git-scm.com/downloads |
| **XAMPP** (or WAMP/Laragon) | PHP 7.4+ / 8.x | https://www.apachefriends.org/ |
| **MySQL** | 5.7+ or 8.x (bundled with XAMPP) | — |
| **phpMyAdmin** | Bundled with XAMPP | — |
| **Web Browser** | Chrome / Firefox | — |

> [!NOTE]
> This guide uses **XAMPP** as the local server environment. Adjust paths accordingly if you use WAMP, Laragon, or another stack.

---

## 🔧 Step 1: Clone the Repository

Open **Command Prompt** or **Git Bash** and navigate to your XAMPP web root directory:

```bash
# Navigate to the XAMPP htdocs folder (Windows)
cd C:\xampp\htdocs

# Clone the repository
git clone https://github.com/atifnewcastle/spark_innovent.git

# Navigate into the project folder
cd spark_innovent
```

> [!TIP]
> If you want to name the folder differently (e.g., `sparkinnovent_copy`), run:
> ```bash
> git clone https://github.com/atifnewcastle/spark_innovent.git sparkinnovent_copy
> ```

---

## 🗄️ Step 2: Set Up the MySQL Database

### 2.1 — Start XAMPP Services

1. Open **XAMPP Control Panel**
2. Click **Start** next to **Apache**
3. Click **Start** next to **MySQL**

### 2.2 — Create the Database

1. Open your browser and go to: `http://localhost/phpmyadmin`
2. Click **New** in the left sidebar
3. Enter the database name: **`spark_innovent`** (or check the project's config file for the exact name)
4. Choose **Collation**: `utf8_general_ci` or `utf8mb4_unicode_ci`
5. Click **Create**

### 2.3 — Import the Database (SQL File)

1. In phpMyAdmin, click on the **`spark_innovent`** database in the left panel
2. Click the **Import** tab at the top
3. Click **Choose File** and browse to the SQL file inside the cloned project:

```
C:\xampp\htdocs\spark_innovent\[database_file].sql
```

> [!IMPORTANT]
> Look inside the project folder for any `.sql` file (commonly named `spark_innovent.sql`, `database.sql`, or similar). If the SQL file is in a subfolder (e.g., `database/`, `db/`, or `sql/`), navigate there.

4. Leave all import settings as default
5. Click **Go** to import

---

## ⚙️ Step 3: Configure the Database Connection

Locate the database configuration file in the project. It is typically one of these:

```
spark_innovent/
├── config.php         ← most common
├── connection.php
├── db.php
├── includes/
│   └── config.php
└── database/
    └── db.php
```

Open the config file and update the connection credentials:

```php
<?php
// Database Configuration
define('DB_HOST', 'localhost');      // Usually 'localhost'
define('DB_USER', 'root');           // Default XAMPP MySQL user
define('DB_PASS', '');               // Default XAMPP MySQL password (empty)
define('DB_NAME', 'spark_innovent'); // The database name you created

// OR using mysqli connection style:
$host     = "localhost";
$username = "root";
$password = "";             // Empty by default on XAMPP
$database = "spark_innovent";

$conn = mysqli_connect($host, $username, $password, $database);
?>
```

> [!WARNING]
> Do **not** use `root` with an empty password in a production environment. This is only safe for local development.

---

## 🌐 Step 4: Run the Project

1. Make sure **Apache** and **MySQL** are running in XAMPP Control Panel
2. Open your browser and navigate to:

```
http://localhost/spark_innovent/
```

> [!TIP]
> If you renamed the project folder (e.g., `sparkinnovent_copy`), update the URL accordingly:
> ```
> http://localhost/sparkinnovent_copy/
> ```

---

## 🔑 Step 5: Default Login Credentials

Check the imported SQL database in phpMyAdmin for any default admin accounts. Look in tables named `users`, `admin`, `pengguna`, or similar.

Common default credentials for PHP projects:

| Role | Username | Password |
|---|---|---|
| Admin | `admin` | `admin` or `admin123` |
| User | `user` | `user` or `123456` |

> [!NOTE]
> If no default credentials exist, check for a registration page or a seeder file inside the project (e.g., `seeder.php`, `setup.php`, or `install.php`).

---

## 🗂️ Typical Project Structure

```
spark_innovent/
├── index.php              ← Entry point / Homepage
├── config.php             ← Database connection
├── admin/                 ← Admin panel pages
├── includes/              ← Shared includes (header, footer, etc.)
├── assets/                ← CSS, JS, images
│   ├── css/
│   ├── js/
│   └── img/
├── database/              ← SQL dump files
│   └── spark_innovent.sql
└── uploads/               ← User uploads (may need write permissions)
```

---

## 🛠️ Troubleshooting

### ❌ "Connection Refused" or blank page
- Ensure Apache and MySQL are **started** in XAMPP.
- Verify the project path is inside `C:\xampp\htdocs\`.

### ❌ Database connection error
- Double-check `DB_NAME`, `DB_USER`, and `DB_PASS` in the config file.
- Make sure the database was created in phpMyAdmin with the exact same name.

### ❌ SQL import fails
- Try splitting the SQL file if it is too large.
- In phpMyAdmin → PHP section, increase `max_execution_time` and `upload_max_filesize` in `php.ini`.

### ❌ Images or uploads not showing
- Check that the `uploads/` folder exists and has write permissions.
- On Windows, right-click the folder → Properties → Security → allow full control.

### ❌ Page shows PHP errors
- Open `C:\xampp\php\php.ini` and set:
  ```ini
  display_errors = On
  error_reporting = E_ALL
  ```
- Restart Apache after saving.

---

## 🔄 Alternative: Download as ZIP (No Git Required)

If Git is not installed:

1. Go to: [https://github.com/atifnewcastle/spark_innovent](https://github.com/atifnewcastle/spark_innovent)
2. Click the green **Code** button
3. Select **Download ZIP**
4. Extract the ZIP to `C:\xampp\htdocs\spark_innovent\`
5. Continue from **Step 2** above

---

## ✅ Setup Checklist

- [ ] Git cloned (or ZIP extracted) to `htdocs`
- [ ] XAMPP Apache & MySQL started
- [ ] Database `spark_innovent` created in phpMyAdmin
- [ ] SQL file imported successfully
- [ ] `config.php` updated with correct DB credentials
- [ ] Project accessible at `http://localhost/spark_innovent/`
- [ ] Login tested with default credentials

---
⚖️ Disclaimer
This software is provided "as is", without warranty of any kind, express or implied. In no event shall the authors or copyright holders be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or the use or other dealings in the software.
*Project: Spark Innovent — Sistem Pengurusan Pertandingan*  

*Repository: https://github.com/atifnewcastle/spark_innovent*

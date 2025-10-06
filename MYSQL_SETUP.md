# MySQL Setup Instructions for Collect Me IoT

## Database Configuration

### Database Name: `collect_me_iot`

## Step 1: Install MySQL Dependencies

```bash
pip install PyMySQL cryptography
```

## Step 2: MySQL Workbench Setup

1. **Open MySQL Workbench**
2. **Connect to your MySQL server**
3. **Run the setup script**:
   - Open the file `mysql_setup.sql` in MySQL Workbench
   - Execute the script to create the database

## Step 3: Configure Database Connection

### Option A: Using Environment Variables (Recommended)
Edit the `.env` file with your MySQL credentials:

```
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_mysql_password_here
DB_NAME=collect_me_iot
```

### Option B: Direct Configuration
Edit `app.py` and modify these lines:
```python
DB_HOST = 'localhost'
DB_PORT = '3306'
DB_USER = 'root'
DB_PASSWORD = 'your_mysql_password'  # Your MySQL root password
DB_NAME = 'collect_me_iot'
```

## Step 4: Run the Application

```bash
python app.py
```

The application will:
- ✅ Connect to MySQL database `collect_me_iot`
- ✅ Automatically create all required tables
- ✅ Create an admin user: admin@collectme.com / admin123
- ✅ Start the Flask-SocketIO server with real-time features

## Step 5: Access the Application

Open your browser and go to: `http://localhost:5000`

**Login Credentials:**
- **Admin**: admin@collectme.com / admin123

## MySQL Workbench Management

Once running, you can use MySQL Workbench to:
- 📊 View and edit data in all tables
- 🔍 Run queries to analyze bin data
- 📈 Monitor database performance
- 💾 Backup and restore data
- 👥 Manage users and permissions

## Database Tables Created

The Flask application will automatically create these tables:
- `users` - User accounts and authentication
- `drivers` - Driver profiles and information  
- `vehicles` - Vehicle management
- `bins` - Smart bin data and sensors
- `tasks` - Collection tasks and assignments
- `task_bins` - Junction table for task-bin relationships
- `sensor_readings` - Historical IoT sensor data

## Troubleshooting

### Connection Issues:
1. Verify MySQL server is running
2. Check username/password in `.env` file
3. Ensure database `collect_me_iot` exists
4. Check MySQL port (default: 3306)

### Permission Issues:
```sql
GRANT ALL PRIVILEGES ON collect_me_iot.* TO 'root'@'localhost';
FLUSH PRIVILEGES;
```

The application will automatically fall back to SQLite if MySQL connection fails.
# Messaging Application

A secure, real-time chat application built with Django, featuring end-to-end encryption and WebSocket communication.

## 🏗 Architecture

The application follows a two-app architecture:

### App1 (Frontend)
```bash
DjangoProject-App1/
├── a_core/          # Main project settings
├── a_rtchat/        # Chat application
├── a_users/         # User management
└── a_home/          # Landing pages
```

### App2 (Backend)
```bash
DjangoProject-App2/
└── ab_core/         # Backend API and storage
```

## 🚀 Installation

1. Clone the repository
```bash
git clone [repository-url]
cd [project-directory]
```

2. Create and activate virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Set up environment variables
```bash
# Create .env file in project root
SECRET_KEY=your_secret_key
DEBUG=True
ENCRYPT_KEY=your_encryption_key
```

5. Run migrations
```bash
python manage.py migrate
```

6. Start the development server
```bash
python manage.py runserver
```

## 🚀 Running the Applications

### Setup App1 (Frontend) and App2 (Backend)

1. **Initial Setup for Both Apps**
```bash
# Clone the repository
git clone [repository-url]

# Create two separate virtual environments
python -m venv DjangoProject-App1/venv
python -m venv DjangoProject-App2/venv
```

2. **Setup App1 (Frontend)**
```bash
# Navigate to App1 directory
cd DjangoProject-App1

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On Unix or MacOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py migrate

# Start App1 server (default port 8000)
python manage.py runserver
```

3. **Setup App2 (Backend)**
```bash
# Open a new terminal
# Navigate to App2 directory
cd DjangoProject-App2

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On Unix or MacOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run migrations
python manage.py migrate

# Start App2 server on port 8081
python manage.py runserver 8081
```

### Verifying the Setup

1. **Check App1 (Frontend)**
   - Open browser: `http://127.0.0.1:8000`
   - You should see the welcome page
   - Register/Login to access chat features

2. **Check App2 (Backend)**
   - API endpoint: `http://127.0.0.1:8081/api/`
   - Handles message storage and retrieval
   - No direct user interface

### Important Notes

- Both applications must be running simultaneously
- App1 communicates with App2 through API calls
- WebSocket connections are handled by App1
- Message encryption/decryption happens in App1
- Message storage occurs in App2

### Troubleshooting

1. **Port Conflicts**
   ```bash
   # If port 8000 is in use for App1
   python manage.py runserver 8001

   # If port 8081 is in use for App2
   python manage.py runserver 8082
   ```

2. **Cross-Origin Issues**
   - Ensure CORS settings are correct in App2
   - Check App1's settings for correct App2 URL

3. **WebSocket Connection Issues**
   - Verify Daphne is running
   - Check channel layer configuration
   - Ensure Redis is running (if using Redis channel layer)

## 💬 Usage

1. Register a new account or login
2. Navigate to the chat interface
3. Join or create a chat room
4. Start sending encrypted messages

## 🔐 Security Features

### Message Encryption
- All messages are encrypted using Fernet symmetric encryption
- Encryption keys are securely managed
- Messages are encrypted before storage

### WebSocket Security
- Authenticated WebSocket connections
- Secure group management
- Protected chat rooms

### User Authentication
- Secure registration and login
- Session management
- Password reset functionality

## 🛠 Development

### Running Tests
```bash
python manage.py test
```

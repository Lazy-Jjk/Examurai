# Examurai - Engineering Exam Resource Hub

A comprehensive web application for engineering students to access, share, and manage question papers from various colleges and universities.

## Features

- **User Authentication**: Sign in with email to access personalized features
- **Question Paper Upload**: Upload PDF question papers with metadata
- **Advanced Filtering**: Filter papers by college, branch, subject, and more
- **Bookmarking System**: Save and manage favorite papers
- **User Dashboard**: Track contributions and bookmarks
- **Email Integration**: Query and message submission via email
- **Responsive Design**: Mobile-friendly interface

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Backend**: Node.js, Express.js
- **Authentication**: Session-based with bcryptjs
- **File Upload**: Multer for PDF handling
- **Email**: Nodemailer for Gmail integration
- **Styling**: Custom CSS with CSS Grid and Flexbox

## Project Structure

```
rtp/
├── assets/                 # Images, logos, team photos
│   ├── colleges/          # College logos
│   ├── team/              # Team member photos
│   └── ...
├── pages/                 # HTML pages
│   ├── account.html       # User account page
│   ├── bookmarks.html     # User bookmarks
│   ├── contact.html       # Contact form
│   ├── filters.html       # Filter/search page
│   ├── signin.html        # Authentication page
│   └── upload.html        # Paper upload page
├── scripts/               # JavaScript files
│   ├── main.js           # Main functionality
│   ├── account.js        # Account management
│   ├── bookmarks.js      # Bookmarks functionality
│   ├── contact.js        # Contact form handling
│   ├── signin.js         # Authentication
│   └── upload.js         # File upload handling
├── styles/                # CSS files
│   ├── main.css          # Main styles
│   ├── account.css       # Account page styles
│   ├── bookmarks.css     # Bookmarks page styles
│   ├── contact.css       # Contact page styles
│   ├── filters.css       # Filter page styles
│   ├── signin.css        # Sign in page styles
│   └── upload.css        # Upload page styles
├── uploads/               # Uploaded PDF files (created automatically)
├── package.json           # Node.js dependencies
├── server.js              # Express server
└── README.md              # This file
```

## Installation & Setup

### Prerequisites

- Node.js (v14 or higher)
- npm (Node Package Manager)
- Gmail account for email functionality

### Step-by-Step Installation

#### 1. Clone or Download the Project

```bash
# If using git
git clone <repository-url>
cd rtp

# Or download and extract the project files
```

#### 2. Install Dependencies

Open your terminal/command prompt in the project root directory (`rtp/`) and run:

```bash
npm install
```

This will install all required dependencies:
- express
- express-session
- bcryptjs
- nodemailer
- multer
- cors
- body-parser

#### 3. Configure Email Settings

Edit the `server.js` file and update the email configuration:

```javascript
// In server.js, around line 60
const transporter = nodemailer.createTransporter({
    service: 'gmail',
    auth: {
        user: 'your-email@gmail.com', // Replace with your Gmail
        pass: 'your-app-password'     // Replace with your app password
    }
});
```

**Important**: You need to:
1. Enable 2-factor authentication on your Gmail account
2. Generate an App Password (not your regular password)
3. Use the App Password in the configuration

#### 4. Create Uploads Directory

The server will automatically create the `uploads/` directory when needed, but you can create it manually:

```bash
mkdir uploads
```

## Running the Application

### Development Mode

```bash
npm run dev
```

This starts the server with nodemon for automatic restarts during development.

### Production Mode

```bash
npm start
```

### Access the Application

Open your web browser and navigate to:
```
http://localhost:3000
```

## Navigation Flow

### Authentication Flow
1. **Sign In**: Click "Sign In" button → `pages/signin.html`
2. **Email Sign In**: Enter email → Creates account if new, signs in if existing
3. **Success**: Redirects to `pages/account.html`
4. **Sign Out**: Click "Sign Out" → Shows success dialog → Redirects to home

### Protected Pages
- **Account**: Requires sign in → Redirects to signin if not authenticated
- **Bookmarks**: Requires sign in → Redirects to signin if not authenticated
- **Upload**: Requires sign in → Redirects to signin if not authenticated

### Navigation Links
- **Examurai Logo**: Always goes to home page
- **Home**: Goes to home page
- **Get Started**: Goes to filters page
- **Learn More**: Goes to contact page
- **View All Colleges/Branches**: Goes to filters page
- **Filter**: Goes to filters page
- **Contact Us**: Goes to contact page

### Social Media Links
- **Instagram**: `https://www.instagram.com/examurai`
- **LinkedIn**: `https://www.linkedin.com/company/examurai`
- **X (Twitter)**: `https://x.com/examurai`

## API Endpoints

### Authentication
- `POST /api/signin` - User sign in/registration
- `POST /api/signout` - User sign out
- `GET /api/user` - Get current user data

### File Upload
- `POST /api/upload-paper` - Upload question paper (requires auth)

### Bookmarks
- `GET /api/bookmarks` - Get user bookmarks (requires auth)
- `POST /api/bookmarks` - Add bookmark (requires auth)
- `DELETE /api/bookmarks/:id` - Remove bookmark (requires auth)

### Email
- `POST /api/submit-query` - Submit search query
- `POST /api/submit-message` - Submit contact form message

## File Locations for Commands

### Windows (PowerShell/Command Prompt)
```bash
# Navigate to project directory
cd C:\Users\sathe\OneDrive\Desktop\rtp

# Install dependencies
npm install

# Start development server
npm run dev

# Start production server
npm start
```

### macOS/Linux (Terminal)
```bash
# Navigate to project directory
cd /path/to/rtp

# Install dependencies
npm install

# Start development server
npm run dev

# Start production server
npm start
```

## Troubleshooting

### Common Issues

1. **Port Already in Use**
   ```bash
   # Kill process on port 3000
   # Windows
   netstat -ano | findstr :3000
   taskkill /PID <PID> /F
   
   # macOS/Linux
   lsof -ti:3000 | xargs kill -9
   ```

2. **Email Not Working**
   - Verify Gmail 2FA is enabled
   - Check App Password is correct
   - Ensure Gmail allows "less secure apps" or use App Password

3. **File Upload Issues**
   - Check file size (max 20MB)
   - Ensure file is PDF format
   - Verify uploads directory exists

4. **Session Issues**
   - Clear browser cookies
   - Restart server
   - Check session secret in server.js

### Development Tips

1. **View Server Logs**: Check terminal for error messages
2. **Browser Developer Tools**: Check Console and Network tabs
3. **Database**: Currently using in-memory storage (resets on server restart)
4. **File Storage**: PDFs stored in `uploads/` directory

## Production Deployment

For production deployment:

1. **Environment Variables**: Use environment variables for sensitive data
2. **Database**: Replace in-memory storage with proper database (MongoDB, PostgreSQL)
3. **File Storage**: Use cloud storage (AWS S3, Google Cloud Storage)
4. **HTTPS**: Enable HTTPS for security
5. **PM2**: Use PM2 for process management
6. **Nginx**: Use Nginx as reverse proxy

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License.

## Support

For support and questions:
- Email: satheeshannarapu@gmail.com
- Create an issue in the repository

---

**Note**: This is a development version. For production use, implement proper security measures, database storage, and cloud file storage. 